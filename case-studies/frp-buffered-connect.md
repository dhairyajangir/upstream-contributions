# Preserve early bytes in HTTP CONNECT tunnels

## Problem

A client may send tunnel bytes immediately after its CONNECT headers. Go's HTTP server can already have read those bytes into its buffered reader when the connection is hijacked. Forwarding only the raw connection discards the bytes retained in that buffer.

## Change

The tunnel joins the backend with a wrapper that reads from the hijacked buffered reader, writes to the connection and closes the connection normally. Already-buffered bytes are forwarded before later socket reads.

## Validation in the merged change

The accepted test uses real in-memory connections and an HTTP server. It checks ordinary and pipelined CONNECT requests, early data, the response and later tunnel data. Both source and regression test landed. fatedier merged the PR; the public review collection does not contain a separate APPROVED review.

## Upstream evidence

- [fatedier/frp #5556](https://github.com/fatedier/frp/pull/5556) — merged 2026-10-09T15:07:49Z by [fatedier](https://github.com/fatedier); [actual merge commit `9c7d9898`](https://github.com/fatedier/frp/commit/9c7d9898b319215823274f40fa70bb12f0aa99c8).
  - [Final `pkg/util/vhost/http.go`](https://github.com/fatedier/frp/blob/9c7d9898b319215823274f40fa70bb12f0aa99c8/pkg/util/vhost/http.go)
  - [Final `pkg/util/vhost/http_test.go`](https://github.com/fatedier/frp/blob/9c7d9898b319215823274f40fa70bb12f0aa99c8/pkg/util/vhost/http_test.go)
