Problem:  
The scope of a variable as follows:
1. Whthin the braces, if it is a local variable.
2. Whthin whole package, if it define out of a pair of braces.
However, sometimes we need an variable which just work in current go file, because I just want to use it in current go file but not pollute other go files within current package.

Just imagine such scenarios:
1. I need a variable, and I want to share it within current go file, but want to forbidden access it out of current go file. I have no way. It broke the rule：minimize the scope of variable.
2. A big package within many go files. I need a log variable to record log. I can define just only one log variable with the name "logger". Even if I just want to modify some format configuration of logger and want it just work on current go file, it will influence the whole package.

Suggestion:   
If go language can provide a keyword, such as "local", to limit a variable's work scope within a go file, it will be very useful for go programmer.