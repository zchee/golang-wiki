What version of Go are you using (go version)?
$ go version 1.18.2
Does this issue reproduce with the latest release?
yes

What operating system and processor architecture are you using (go env)?
linux & windows , amd64

What did you do?
https://go.dev/play/p/wi_i3Dx8Hpa

package main

func clearMap(m map[string]string) {
	for k := range m {
		delete(m, k)
	}
}

//go:noinline
func clearMap2(m map[string]string) {
	for k := range m {
		delete(m, k)
	}
}

var m map[string]string

func main() {
	clearMap(m)
	clearMap2(m)
}
In go1.18, the compiler will inline clearMap by default, then generates:

CALL runtime.mapiterinit(SB)
JMP 0x45b3c9
MOVQ 0(DX), CX
MOVQ 0x8(DX), DI
LEAQ type.*+23744(SB), AX
MOVQ 0x20(SP), BX
CALL runtime.mapdelete_faststr(SB)
LEAQ 0x28(SP), AX
CALL runtime.mapiternext(SB)
MOVQ 0x28(SP), DX
TESTQ DX, DX
JNE 0x45b3a7
and clearMap2 will call runtime.mapclear.

Is this expected behavior?