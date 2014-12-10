# Introduction

This wiki page collects patches to build older version of Go on newer systems for
testing and benchmark purposes. Please note that older Go versions are not
supported, so don't use older version in production.

# Go 1.0.x
## Go 1.0
```
diff -ur go/src/cmd/cc/funct.c go1/src/cmd/cc/funct.c
--- go/src/cmd/cc/funct.c	2012-03-28 00:49:24.000000000 -0400
+++ go1/src/cmd/cc/funct.c	2014-05-04 00:56:00.971460175 -0400
@@ -269,7 +269,7 @@
 		goto bad;
 
 	f = alloc(sizeof(*f));
-	for(o=0; o<sizeof(f->sym); o++)
+	for(o=0; o<nelem(f->sym); o++)
 		f->sym[o] = S;
 
 	t->funct = f;
```