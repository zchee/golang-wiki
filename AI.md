---
title: AI
---

A list of resources for accessing AI (Artificial Intelligence)
services using Go, notably Large Language Models (LLM) and Machine
Learning (ML) systems.

## What kind of AI applications can you build with Go?

Go is an excellent language for writing programs that use AI services.
This includes programs that use LLM services for summarizing or
classifying data, answering questions based on a database, or avoiding
repetitive tasks.
The services can be accessed on the Internet (hosted services), or run
locally (downloaded services).

For example, the program
[golang.org/x/cmd/vulndb/vulnreport](https://pkg.go.dev/golang.org/x/vulndb/cmd/vulnreport)
uses AI to summarize vulnerability reports.
When a member of Go's security team runs the program with a new
vulnerability report, vulnreport contacts a generative AI service (in
this case Google's generative AI service).
It passes a
[prompt](https://go.googlesource.com/vulndb/+/refs/heads/master/internal/genai/templates/preamble.txt)
along with the original description of the vulnerability.
The AI service will respond with a concise summary.
The Go security team member can then refine that into the final
human-readable report.

## How do I find Go packages to access AI services?

This is a fast moving area of development, and these answers may
change.

**Provider-Specific SDKs**
If you are targeting a specific service, check if the provider offers an official Go package.
- **Google Generative AI**: [github.com/googleapis/go-genai](https://pkg.go.dev/google.golang.org/genai) ([Examples](https://pkg.go.dev/google.golang.org/genai#pkg-examples))

**General Frameworks**
For greater flexibility across different services, consider using a general framework:
- [Genkit Go](https://genkit.dev/docs/overview/?lang=go): An open source framework from Google for building AI-powered applications.
- [langchaingo](https://pkg.go.dev/github.com/tmc/langchaingo): The Go implementation of the LangChain framework.
- [Ollama](https://pkg.go.dev/github.com/ollama/ollama/api): A library for running large language models locally.

## How do I call a hosted service from Go?

It varies from service to service, but the basic steps are

- create a client
- assemble a message to send to the model
  - the message will include a prompt that asks a question or tells
    the service what to do
  - the message can have different parts
- send the message to the client
- receive a reply

Here is a [complete small example using the Google AI service](https://eli.thegreenplace.net/2023/using-gemini-models-from-go/).

## How do I call a downloaded service from Go?

Ollama provides a good framework for using downloaded services.
Ollama runs on the local machine but opens a port on the localhost to
provide a REST API.
At that point Ollama can be treated as a hosted service, but the
actual AI computation will be done on the local machine.

Here is a [complete small example of using Ollama from Go](https://eli.thegreenplace.net/2023/using-ollama-with-langchaingo/).

## How do I build LLM-powered applications in Go?

To learn how to build an application with different LLM frameworks, take a look at
[how to build a RAG server using various LLM frameworks](https://go.dev/blog/llmpowered).

## How do I manage prompts in Go?

The message sent to an LLM service is referred to as a _prompt_.
In many cases a program will have a general prompt that contains
variables that are filled in based on user input.
In Go a natural way to do this is to use the
[text/template package](https://pkg.go.dev/text/template).
