# AI assistant for Hasura Observability

## How it works

The supergraph allows you to querying logs and metrics data from Loki and Prometheus. The AI assistant helps you to talk to those data using natural languages. You can ask logs of GraphQL Engine instances and node exporter metrics.

## Get started

Input your project name in `.hasura/context.yaml`, export `ANTHROPIC_API_KEY` environment variable, build the supergraph and start Docker Compose.

```sh
ddn supergraph build local

export ANTHROPIC_API_KEY=xxx
ddn run docker-start
```

> [!NOTE]
> If you see this error `ERR no PromptQL secret key found for project xxx` the `ddn auth print-promptql-secret-key` command doesn't work. In this case, you can go to the project setting of DDN console to create the PromptQL API key directly.

## Talk to your data

Now, you can ask semantic questions on your data:

- Get the last 1 minute data of http_log, include log line
- Get the last 1 minute data of hasura log with type query-log, include log line
- Get total prometheus http requests in the last 10 minutes and have total requests > 0
- Get the last process virtual memory value in prometheus in the last 5 minutes, step 1m, group by instance

## Limitation

The AI assistant doesn't work well with aggregate queries. Query languages of Loki and Grafana aren't compatible with SQL. This may be improved after upgrading NDC Specification v0.2.
