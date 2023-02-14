This page links to projects that use or enhance `slog`, the [proposed](https://go.dev/issue/56345) structured logging package for the standard library.

Currently, `slog` is at [golang.org/x/exp/slog](https://pkg.go.dev/golang.org/x/exp/slog).

- ConsoleHandler (similar to Zap's ConsoleEncoder): https://gist.github.com/wijayaerick/de3de10c47a79d5310968ba5ff101a19
- Zap Handler, a slog handler that uses Zap: https://github.com/chanchal1987/zaphandler
- logf (attr {key} interpolation, rich tty output): https://pkg.go.dev/github.com/AndrewHarrisSPU/logf (uses lazy Handler stores: https://go.dev/play/p/psdD7KDF5fp)
- Simple slog handler with opentelemetry tracing: https://github.com/ttys3/slogsimple/tree/main
- Experimental example using both OpenTelemetry and `slog`: https://github.com/justinsb/experiments-slog
- Additional resources written by jba: https://github.com/jba/slog
- slogd - slog with duration https://github.com/kaihendry/slogd with video https://youtu.be/IsPa11N5pzI