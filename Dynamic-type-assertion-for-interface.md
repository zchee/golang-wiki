Please do note that the structs in this example is a sample.My struct is complex than this.
https://play.golang.org/p/_t7gx3javb
Here I have a function where i will be using lot of times.Each time i will be passing object of different struct types.So i use the parameter arguments as interface{}.
So to solve the error i need to do type assertion.But here the interface can be of any struct type.So i am looking if there is any possible way to do the dynamic type assertion based on the reflect.TypeOf value.