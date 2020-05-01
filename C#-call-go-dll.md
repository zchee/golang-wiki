字符串的参数传递，非常麻烦。GoString方式，总是导致程序崩溃。使用byte[]和IntPtr传递，非常可靠。

go code
```go
//export TestApi
func TestApi(inParam *C.char, outParam **C.char, outlen *C.int) int {
	// 输入参数
	in := C.GoString(inParam)

	// 注意事项
	s := "1122ABC你" + in

	bytS := []byte(s)
	s = hex.EncodeToString(bytS)

	// 输出参数
	*outParam = C.CString(s)
	var noutlen int
	noutlen = len(C.GoString(*outParam))
	*outlen = C.int(noutlen)

	return 0
}

```


C# code
```csharp

[DllImport("dlltest.dll", CharSet = CharSet.Ansi)]
        public static extern int TestApi(byte[] inParam,ref IntPtr outstr, ref int outlen);


            byte[] inParam = null;
            IntPtr ptr = IntPtr.Zero;
            int outlen = -1;
            string outstr = "";

            inParam = Encoding.UTF8.GetBytes("Hello world!");

            int ret = Inwhtl_DLL.TestApi(inParam,ref ptr, ref outlen);

            if(outlen > 0)
            {
                outstr = Marshal.PtrToStringAnsi(ptr, (int)outlen);
                byte[] byt = strToToHexByte(outstr);
                outstr = Encoding.UTF8.GetString(byt);

                MessageBox.Show(outstr);

            }
```
环境：
windows7 + TDM gcc


# 编译生成动态库（**TDM 命令行下执行**）
go build -buildmode=c-shared -o dlltest.dll
