# Go2 status

This page tracks the status of "Go 2".

We are currently seeking feedback on potential designs for improved error handling, error values, and generics:

* [Announcement of Go2 Draft Designs](https://blog.golang.org/go2draft)
* [Go2 Error Handling, Generics, and Error Values](https://go.googlesource.com/proposal/+/master/design/go2draft.md)

## Bugs

* [Open Go2 bugs](https://github.com/golang/go/issues?q=is%3Aissue+is%3Aopen+label%3AGo2)

## Talks

* [GopherCon 2017: Russ Cox - The Future of Go](https://www.youtube.com/watch?v=0Zbh_vmAKvk) 
* [GopherCon Russia 2018: Brad Fitzpatrick - Go: Looking back and looking forward](https://www.youtube.com/watch?v=ZCB-g2B4Y5A) (Go2 stuff is at about 20 minutes in)

## Scope

From talk above:

* "maybe three major changes"
* plus minor housekeep tasks
* TBD

Examples of major changes:

* [versioning](https://github.com/golang/go/issues/24301)
* [generics](https://github.com/golang/go/issues/15292)?
* [simplified, improved error handling](https://github.com/golang/go/issues/21161)?
* ...

Examples of housekeeping:

* [Open Go2Cleanup bugs](https://github.com/golang/go/issues?q=is%3Aissue+is%3Aopen+label%3AGo2Cleanup) (please don't add this label to things without discussion)

## Compatibility

We do not want to break the ecosystem. Go 1 and Go 2 code must be able to interoperate in programs with ease.

## Standard library

The standard library would probably be versioned and permit out-of-cycle updates, but be included with Go releases. Maybe "encoding/foo" become shorthand for "golang.org/x/std/encoding/foo". TBD. Some package would probably get v2 major versions, but the v1 versions would be minimally maintained, at least for security.

## Roadmap

TBD