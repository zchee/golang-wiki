Here's an alternative syntax that uses the familiar <> and avoids parsing complexity by placing it to the left of the identifier.  It is a bit (very?) unusual, but has the benefits of brevity and making the type parameters stand out.  Converting some examples from [Generics — Problem Overview](https://go.googlesource.com/proposal/+/master/design/go2draft-generics-overview.md#draft-design):

```
type <T>List []T
func <K, V>Keys(m map[K]V) []K
var ints <int>List
keys := <int, string>Keys(map[int]string){1: "one", 2: "two"})
```


A method:
```
type <T Equal>Set []T
func (s <T>Set) Find(x T) int {
    ...
}
```
