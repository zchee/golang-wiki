## Introduction

grpc-connection-library is a library that supports the gRPC client-server connection interface for the developers to use as a gRPC middleware in the application. The library is written in Golang with a concurrency pipeline design pattern to synchronize the gRPC connection pool system.

## Features
* The gRPC connection flow among server/client synchronized using the Ping/Pong services.
* gRPC connection library supports connection pool reuse the gRPC client connection instance.
* Concurrency Pipeline design pattern synchronizes the data flow among several stages while creating the connection pool.
* The selection process of the gRPC connection instance from the pool is designed using the [reflect.SelectCase](https://pkg.go.dev/reflect#SelectCase) that supports pseudo-random technique for choosing among different cases.
* [go-batch](https://github.com/Deeptiman/go-batch) processing library implemented to divide the connection instances from the pool into batches.
* The grpc-retry policy helps to retry the failure of gRPC connections with backoff strategy.
* The [grpclog](https://pkg.go.dev/google.golang.org/grpc/grpclog) will show the internal connection lifecycle that will be useful to debug the connection flow.

## Installation

`go get github.com/Deeptiman/go-connection-library`

## Go Docs

Documentation at [pkg.go.dev](https://pkg.go.dev/github.com/Deeptiman/grpc-connection-library)


