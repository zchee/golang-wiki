i have searched this issue many times and its always the same response: put http:// before your link and I did that, and then the error changed from get: www.facebook.com unsupported protocol error 
to get 0: unsupported protocl error????
heres the code :

package main

import (
"strings"
"log"
"bufio"
"os"
"io/ioutil"
"fmt"
"net/http"
)
var companyname string
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
func main() {
res, err := http.Get("https://www.facebook.com/search/pages/?q=" + "KFC")

if err != nil {

log.Fatal(err)
}
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
robots, err := ioutil.ReadAll(res.Body)

res.Body.Close()
if err != nil {

log.Fatal(err)
}

    err = ioutil.WriteFile("source.txt", robots, 0644)      
    if err != nil {
        panic(err)
    }
  lines, err := readLines("source.txt")                 
  if err != nil {
    log.Fatalf("readLines: %s", err)
    for i, line := range lines {
      fmt.Println(i, line)
    }
  }

  for i := 0; i < len(lines); i++ {                     
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

    lineToTest := lines[i]                              
    if strings.Contains(lineToTest, "Forgot your password?") == true {              
      WhatToPrint := strings.Split(lineToTest, "value=")    // this text will be deleted.
      WhatToPrint2 := WhatToPrint[5]
      WhatToPrint3 := strings.Split(WhatToPrint2, "\"")
      WhatToPrint4 := WhatToPrint3[1]
      fmt.Println(WhatToPrint4)
      URL := WhatToPrint4                               
      res, err := http.Get(URL)                 
      if err != nil {                                   
        log.Fatal(err)
      }

      robots, err := ioutil.ReadAll(res.Body)           
      res.Body.Close()
      if err != nil {
        log.Fatal(err)
      }

      err = ioutil.WriteFile("source.txt", robots, 0644)                            
      if err != nil {                                   
        panic(err)
      }
    }
  }
}
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
func readLines(path string) ([]string, error) {
file, err := os.Open(path)

if err != nil {

return nil, err
}
defer file.Close()

var lines []string
scanner := bufio.NewScanner(file)

for scanner.Scan() {
lines = append(lines, scanner.Text())

}
return lines, scanner.Err()

}