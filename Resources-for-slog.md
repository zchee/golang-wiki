---
title: Resources for slog
---

This page links to projects that use or enhance [`slog`](https://pkg.go.dev/log/slog), the structured logging package for the standard library.

#### Log formatting
- slog-formatter: Common formatters for slog + helpers for building your own: https://github.com/samber/slog-formatter
- ConsoleHandler (similar to Zap's ConsoleEncoder): https://gist.github.com/wijayaerick/de3de10c47a79d5310968ba5ff101a19
- logf (attr {key} interpolation, rich tty output): https://pkg.go.dev/github.com/AndrewHarrisSPU/logf (uses lazy Handler stores: https://go.dev/play/p/psdD7KDF5fp )
- slogd - slog with duration https://github.com/kaihendry/slogd with video https://youtu.be/IsPa11N5pzI
- tinted (colorized) output: https://pkg.go.dev/github.com/lmittmann/tint
- humane: a human-friendly (but still largely structured) slog Handler: https://github.com/telemachus/humane
- slug: a handler that prints colourful logs for humans: https://github.com/dotse/slug
- slogor: A colorful slog handler: https://gitlab.com/greyxor/slogor
- [klog](https://github.com/kubernetes/klog): the text format used by Kubernetes. Provides klog output routing when using the main package's logger and [a simpler logger](https://github.com/kubernetes/klog/tree/main/textlogger) that just writes to stderr. Both slog/logr and go-logr/logr APIs are supported.
- slogjson: Format using the upcoming [JSON v2 library](https://github.com/golang/go/discussions/63397), with optional single-line pretty-printing: https://github.com/veqryn/slog-json

#### Logger bridge
- Zap Handler, a slog handler that uses Zap: https://github.com/chanchal1987/zaphandler
- [zapr](https://github.com/go-logr/zapr): starting with v1.3.0, both slog/logr and go-logr/logr APIs are supported by the same logger instance.

#### Logging Middleware
- slogctx: store attributes or the logger in context, read any custom values from context: https://github.com/veqryn/slog-context
- slog-context/otel: automatically read and add OpenTelemetry TraceID and SpanID to logs, and can set Span error code: [github.com/veqryn/slog-context/otel](https://github.com/veqryn/slog-context#opentelemetry-traceid-spanid-extractor)
- slogdedup: deduplication and sorting of attribute keys, with multiple policies, useful for json logging. Convenience methods to output for Stackdriver, Graylog, and others: https://github.com/veqryn/slog-dedup

#### HTTP server middleware
- slog-gin: Gin middleware for slog logger: https://github.com/samber/slog-gin
- slog-echo: Echo middleware for slog logger: https://github.com/samber/slog-echo
- slog-fiber: Fiber middleware for slog logger: https://github.com/samber/slog-fiber
- slog-chi: Chi middleware for slog logger: https://github.com/samber/slog-chi

#### Log sinks
- Experimental example using both OpenTelemetry and `slog`: https://github.com/justinsb/experiments-slog
- Simple slog handler with opentelemetry tracing: https://github.com/ttys3/slogsimple/tree/main
- slog-datadog: a `slog.Handler` for Datadog: https://github.com/samber/slog-datadog
- slog-rollbar: a `slog.Handler` for Rollbar: https://github.com/samber/slog-rollbar
- slog-sentry: a `slog.Handler` for Sentry: https://github.com/samber/slog-sentry
- slog-syslog: a `slog.Handler` for Syslog: https://github.com/samber/slog-syslog
- slog-logstash: a `slog.Handler` for Logstash: https://github.com/samber/slog-logstash
- slog-fluentd: a `slog.Handler` for Fluentd: https://github.com/samber/slog-fluentd
- slog-graylog: a `slog.Handler` for Graylog: https://github.com/samber/slog-graylog
- slog-loki: a `slog.Handler` for Loki: https://github.com/samber/slog-loki
- slog-slack: a `slog.Handler` for Slack: https://github.com/samber/slog-slack
- slog-telegram: a `slog.Handler` for Telegram: https://github.com/samber/slog-telegram
- slog-mattermost: a `slog.Handler` for Mattermost: https://github.com/samber/slog-mattermost
- slog-microsoft-teams: a `slog.Handler` for Microsoft Teams: https://github.com/samber/slog-microsoft-teams
- slog-webhook: a `slog.Handler` for Webhook: https://github.com/samber/slog-webhook
- slog-kafka: a `slog.Handler` for Kafka: https://github.com/samber/slog-kafka
- slogbugsnag: a `slog.Handler` for Bugsnag: https://github.com/veqryn/slog-bugsnag
- slogdriver: a `slog.Handler` for Stackdriver Logging / GCP Cloud Logging: https://github.com/jussi-kalliokoski/slogdriver

#### Handlers
- slog-multi: chain of `slog.Handler` (pipeline, fanout, ...): https://github.com/samber/slog-multi
- various handlers: https://github.com/galecore/xslog

#### Other:
- Additional resources written by jba: https://github.com/jba/slog
- slog-sampling: drop repetitive log entries: https://github.com/samber/slog-sampling
- slog-context: adds support to reading values from context: https://github.com/PumpkinSeed/slog-context
- slogassert: handle for testing slog logs emitted by code: https://github.com/thejerf/slogassert
- sloggen: generate various helpers for `log/slog`: https://github.com/go-simpler/sloggen
- sloglint: ensure consistent code style when using `log/slog`: https://github.com/go-simpler/sloglint
