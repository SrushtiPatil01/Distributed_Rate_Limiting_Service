# Distributed Rate Limiting Service

## Project Summary

A distributed rate limiting service built in Go using gRPC and Redis. Implements a token-bucket algorithm to protect downstream microservices from burst traffic.

## Overview
This service provides centralized rate limiting for microservices in a distributed system.
- Built with Go
- Uses gRPC for low-latency communication
- Uses Redis (AWS ElastiCache compatible) for shared state
- Enforces limits atomically using Redis Lua scripts
- Stateless and horizontally scalable
- Containerized with Docker
- Monitored using Prometheus and Grafana

The service sustained 5K+ requests per second during load testing while maintaining stable p95 and p99 latencies.

## Technologies Used
Each client key (user/API/service) is assigned:
- Capacity (maximum burst size)
- Refill rate (tokens added per second)
For every request:
- Tokens are refilled based on elapsed time.
- If enough tokens are available, the request is allowed.
- If not, the request is rejected.

All operations are executed atomically using a Redis Lua script to prevent race conditions in distributed environments.

## Tech Stack

- **Go** 
- **gRPC** 
- **Redis (AWS ElastiCache)** 
- **Docker**
- **AWS EC2**
- **Prometheus** 
- **Grafana** 
