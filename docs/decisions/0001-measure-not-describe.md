# 0001: Log queries and count, instead of describing impressions

**Status:** accepted, 0.1.0

## Context

Most teardowns are opinions with screenshots. A search teardown can be measured.

## Decision

Run a fixed set of queries, record offer counts, promoted positions and title counts, and publish the log.

## Tradeoff

- Eight queries is a small, single-session sample
- Every claim on the page traces to a number in the log
