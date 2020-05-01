It just test on linux(deepin linux or ubuntu).
```go
//dllcall.go
package dlltest

/*
#include "loaddll.h"
#cgo LDFLAGS: -ldl
*/
import "C"
import (
	"encoding/hex"
	"errors"
	"fmt"
	"unsafe"
)

type DllCall struct {
}

var (
	// 启用调试标记 1 启动调试 0 关闭调试
	M_Conf_Debug = 1
)

func NewDllCall() *DllCall {
	return &DllCall{}
}

// 计算哈希
func (o *DllCall) HashData(agmId int, iv string, src string) (string, error) {
	agmID := C.int(agmId)
	var hashValueByt [2048]byte
	hashValueBytLen := C.int(len(hashValueByt))

	bytIv, _ := hex.DecodeString(iv)   //公钥
	bytSrc, _ := hex.DecodeString(src) // 待哈希数据

	//logs.Info("src= \n%v", src)
	ret := C.HashData(
		M_Conf_Debug,
		agmID,                                                   /* 加密方案，1 国密算法 */
		(*C.char)(unsafe.Pointer(&bytIv[0])), C.int(len(bytIv)), /* 字符串，向量 */
		(*C.char)(unsafe.Pointer(&bytSrc[0])), C.int(len(bytSrc)), /* 字符串，待哈希数据 */
		(*C.char)(unsafe.Pointer(&hashValueByt[0])), &hashValueBytLen) /* 出参: 字节缓冲区*/
	if ret != 0 {
		outButStr := ""
		errmsg := fmt.Sprintf("c dll HashData call fail, ret=%v, errmsg=%v, msg=%v", ret, GetErrorMsg(int(ret)), outButStr)
		return "", errors.New(errmsg)
	}

	hashValue := hex.EncodeToString(hashValueByt[:hashValueBytLen])

	return hashValue, nil
}

func GetErrorMsg(errorCode int) string {
	errorCodeMap := make(map[int]string)

	errorCodeMap[-1] = "参数错误"
	errorCodeMap[-2] = "结果数据缓冲区长度不足"

	return errorCodeMap[errorCode]
}
```
loaddll.h
```go


// 计算哈希
int HashData(int ctl, int agmID, char *iv, int iLen, char *src, int sLen, char *rslt, int *rLen);
```

loaddll.c
```c
#include "loaddll.h"
#include <dlfcn.h>
#include <stdio.h>
#include <unistd.h>
#include <string.h>

// ----------- 预定义变量 ----------------
#define LIB_NAME "libdll.so"  //library name

// 外部参数
char dll_name[]= LIB_NAME;
// 动态库句柄
void* dll_handle;

// 动态库load标记 0 成功
int dll_loaded = 1;

// 函数声明
 void uint8_2_hex(char *source, int length, char *target) ;
 int load_dll(const char* dllname, char* outbuf);

// 函数指针，计算Hash
typedef int (*fptr_HashData)(int agmID, char *iv, int iLen, char *src, int sLen, char *rslt, int *rLen);

// 计算哈希
int HashData(int ctl, int agmID, char *iv, int iLen, char *src, int sLen, char *rslt, int *rLen){
  int callret = -1; //调用结果
  int dllret = -1;
  char buf[20480] = {0};
  
  // 检测动态库是否加载，没有加载就自动加载
  if(dll_loaded != 0)
  {
		char szOutMsg[256] = {0};
        int b = load_dll(dll_name, szOutMsg);
        if(b!=0)
		{
			callret = -1;
			strcpy(rslt, szOutMsg);
			*rLen = strlen(rslt);

			return callret;
		}
	}

    if(ctl)
    {
        // ------------- 打印参数
        printf("--Debug--method(HashData)--> InputParam:\n");
        printf("--> ctl: %d\n", ctl);
        uint8_2_hex(iv,iLen, buf);
        printf("--> iv[%ld]: %s\n",  strlen(buf)/2, buf);
        uint8_2_hex(src,sLen, buf);
        printf("--> src[%ld]: %s\n",strlen(buf)/2, buf);
    }

	// 函数指针
	fptr_HashData fptr = (fptr_HashData)dlsym(dll_handle, "HashData");
iLen = 0;
	// 调用动态库函数
	dllret = (*fptr)(agmID, iv, iLen, src, sLen, rslt, rLen);

    if(ctl)
    {
        printf("--Debug--method(HashData)--> OutParam:\n");
        printf("--> Ret=%d\n",dllret);
        if(!dllret)
        {
            uint8_2_hex(rslt,*rLen, buf);
            printf("--> hash[s,%ld==%d]: %s\n", strlen(buf)/2, *rLen, buf);
        }
    }

	callret = dllret ;
	return callret;
}

// 加载动态库
int load_dll(const char* dllname, char* outbuf)
{
    // -------------- 得到当前路径 -----------
    char buf[1024] = {0};   
    char *p = getcwd(buf,sizeof(buf));   

    char szFullPath[1200] = {0};
    strcpy(szFullPath, buf);
    strcat(szFullPath, "/lib/");  //第三方依赖库存放路径
    strcat(szFullPath, dllname);

    // ------------ 打开动态库 --------------
    dll_handle = dlopen(szFullPath, 1);
    if(dll_handle == 0){
			memset(buf, 0, sizeof(buf));
			sprintf(buf,"open dll fail, filename= %s", szFullPath);   

	strcpy(outbuf,buf);
      return -1; 
    }

    dll_loaded = 0;
    return 0;
}


// ----------------- 工具函数 ----------------------
/**
 * 字节数组转十六进制字符串
 * @param source
 *  字符数组
 * @param length
 *  字符数组长度
 * @param target
 *  字符串
 */
void uint8_2_hex(char *source, int length, char *target) {
    char szbuf[10240] = {0};
    for (int i = 0; i < length; i++) {
        char buf[3]={0};
        sprintf(buf, "%.2X", (unsigned char)source[i]);
        strcat(szbuf, buf);
    }
    strcpy(target, szbuf);
}

```

library api decalre 
```c
//  底层库操作接口说明


// 计算数据的hash值
// 返回值:
// 		>0: 计算成功, 返回结果数据的字节数
// 		<0: 计算失败, 错误代码
// 参数:
// 		[in]agmID: 系统将要使用的算法组标识
// 		[in]iv: 算法所需的初始化数据
// 		[in]iLen: iv数据的字节数
// 		[in]src: 所需哈希的数据
// 		[in]sLen: src数据的字节数
// 		[out]rslt: 返回结果数据
// 		[in/out]rLen: 期望的结果数据字节长度.如果输入值小于实际长度则返回实际所需的字节数,同时方法的返回值返回特殊值报告此种情况.
int HashData(int agmID, char *iv, int iLen, char *src, int sLen, char *rslt, int *rLen);

```