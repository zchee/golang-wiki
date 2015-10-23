# Introduction

Programmers from languages like Java or C++ may miss an `enum` type, providing type-safe constants.

# Code

    type LogLevel struct { name string }
    var (
      LL_FATAL = LogLevel{"fatal"}
      LL_ERROR = LogLevel{"error"}
      LL_WARN = LogLevel{"warn"}
      LL_INFO = LogLevel{"info"}
      LL_DEBUG = LogLevel{"debug"}
    )

This code allows functions to take a parameter of type `LogLevel` and prevents callers from accidentally passing values of other types for this parameter.
