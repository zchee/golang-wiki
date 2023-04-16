This page links to projects that use or enhance `slog`, the [proposed](https://go.dev/issue/56345) structured logging package for the standard library, accepted for Go 1.21.

A preliminary implementation is at [golang.org/x/exp/slog](https://pkg.go.dev/golang.org/x/exp/slog). That won't be receiving any more updates; instead, follow the `src/log/slog` directory of the [main Go repo](https://go.googlesource.com/go).

Since slog has been in flux for several months, some of these resources may be out of date and may not build. The API did not change that much, though, so fixes should be straightforward.

- ConsoleHandler (similar to Zap's ConsoleEncoder): https://gist.github.com/wijayaerick/de3de10c47a79d5310968ba5ff101a19
- Zap Handler, a slog handler that uses Zap: https://github.com/chanchal1987/zaphandler
- logf (attr {key} interpolation, rich tty output): https://pkg.go.dev/github.com/AndrewHarrisSPU/logf (uses lazy Handler stores: https://go.dev/play/p/psdD7KDF5fp)
- Simple slog handler with opentelemetry tracing: https://github.com/ttys3/slogsimple/tree/main
- Experimental example using both OpenTelemetry and `slog`: https://github.com/justinsb/experiments-slog
- Additional resources written by jba: https://github.com/jba/slog
- slogd - slog with duration https://github.com/kaihendry/slogd with video https://youtu.be/IsPa11N5pzI
- tinted (colorized) output: https://pkg.go.dev/github.com/lmittmann/tint
- humane: a human-friendly (but still largely structured) slog Handler: https://github.com/telemachus/humane
- slug: a handler that prints colourful logs for humans: https://github.com/dotse/slug
- various handlers: https://github.com/galecore/xslog
- slog-multi: chain of `slog.Handler` (pipeline, fanout, ...): https://github.com/samber/slog-multi
- slog-formatter: Common formatters for slog + helpers for building your own: https://github.com/samber/slog-formatter
- slog-gin: Gin middleware for slog logger: https://github.com/samber/slog-gin
- slog-sentry: a `slog.Handler` for Sentry: https://github.com/samber/slog-sentry
- slog-logstash: a `slog.Handler` for Logstash: https://github.com/samber/slog-logstash
- slog-datadog: a `slog.Handler` for Datadog: https://github.com/samber/slog-datadog
- slog-loki: a `slog.Handler` for Loki: https://github.com/samber/slog-loki
- slog-fluentd: a `slog.Handler` for Fluentd: https://github.com/samber/slog-fluentd
- slog-syslog: a `slog.Handler` for Syslog: https://github.com/samber/slog-syslog
- slog-graylog: a `slog.Handler` for Graylog: https://github.com/samber/slog-graylog
- slog-slack: a `slog.Handler` for Slack: https://github.com/samber/slog-slack
