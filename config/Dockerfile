# syntax=docker/dockerfile-upstream:master-labs

FROM squidfunk/mkdocs-material:latest AS mkdocs_base

WORKDIR /github/workspace
RUN set -eux && \
	pip install --no-cache-dir -U --pre --compile --verbose pip
COPY ./config/requirements.txt /github/workspace/config/requirements.txt
RUN set -eux && \
	pip install --no-cache-dir -U --pre --compile --verbose --requirement /github/workspace/config/requirements.txt
COPY . .

FROM mkdocs_base AS mkdocs_build
RUN set -eux && \
	mkdocs --verbose build --clean --site-dir /docs --config-file /github/workspace/config/mkdocs.yml

FROM mkdocs_base AS mkdocs
ARG MKDOCS_PORT
ENV MKDOCS_PORT=${MKDOCS_PORT:-8000}
EXPOSE $MKDOCS_PORT
CMD ["mkdocs", "--verbose", "serve", "--dev-addr", "localhost:$MKDOCS_PORT", "--livereload", "--config-file", "./config/mkdocs.yml"]

FROM scratch AS docs
COPY --link --from=mkdocs_build /docs /docs
