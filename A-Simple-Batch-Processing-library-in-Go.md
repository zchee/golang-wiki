## Introduction
go-batch is a batch processing library written in Go. The process execution has multiple stages to release a Batch to the client.

## Features
* Client can use this library as an asynchronous batch processing for their application use case.
* There are no restrictions on applying batch processing matrices to the library. The client can define the maximum no of items for a batch using the BatchOptions.
* The library has a Workerpool that will faster the batch processing in concurrent scenarios.

## Demo
 [![asciicast](https://asciinema.org/a/2vi5gAHjsuTrB3tCBTGeSW6hq.svg)](https://asciinema.org/a/2vi5gAHjsuTrB3tCBTGeSW6hq) 

## Installation
`go get github.com/Deeptiman/go-batch`

## Go Docs
Documentation at [pkg.go.dev](https://pkg.go.dev/github.com/Deeptiman/go-batch)