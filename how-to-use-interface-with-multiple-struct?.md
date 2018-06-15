how can i use interface with diffrent-diffrent strcut?
I just want to use interface like struct with field name.So can we use interface as dynamic struct type.
i was used ff := getdata.(SecondType) fmt.Println(ff.Address) but it is not dynamic.

Like

package main

import (
"fmt"
)

type FirstType struct {
Name string
Email string
}

type SecondType struct {
Address string
Points float64
}

func main() {
UseOfInterface(SecondType{Address: "Raj. india", Points: 4.4})
UseOfInterface(FirstType{Name: "Manish Jangid", Email: "manish101.mj@gmail.com"})
}

func UseOfInterface(getdata interface{}) {
?
?
?
?

}