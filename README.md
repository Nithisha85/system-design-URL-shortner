# system-design-URL-shortner
A scalable, multi-region URL Shortener with fast redirects, edge caching, and real-time click analytics powered by streaming and OLAP storage.

# 🌐 URL Shortener with Multi-Region Click Analytics

A scalable, globally distributed URL shortening service designed for low-latency redirects, high availability, and real-time click analytics.

# 🚀 Overview

This project provides a production-grade design for a URL Shortener capable of handling billions of redirects, write bursts, and detailed analytics tracking.
It incorporates global CDNs, edge caching, strongly consistent link storage, and an asynchronous analytics pipeline using streaming technologies and OLAP databases.

## This repository includes:

📄 Full system design document

🖼️ Architecture, sequence, ER, and context diagrams

⚙️ Requirements, SLOs, trade-offs & engineering notes

📊 Data model and analytics workflow

🎨 Images for use in documents and presentations

## ✨ Features

🔗 Short URL creation (auto-ID or custom alias)

⚡ Sub-50ms redirects using CDN + edge caching

📈 Click analytics (timestamp, IP, referrer, geo, device)

🌍 Multi-region deployment with Anycast routing

🔄 Strong consistency for redirect mapping

🧵 Eventual consistency for analytics

📊 OLAP-based analytics reporting

🛡️ Rate limiting & abuse detection

🚧 Reliable failover, retries, circuit breakers

## 🧱 System Architecture

The high-level system includes:

Global CDN / Anycast (primary redirect path)

Edge cache (Redis / POP)

Redirect service (stateless)

API Gateway + URL Shorten service

Primary link database (strong consistency)

Read replicas (geo-distributed)

Kafka-based analytics stream

Stream processor (Flink / Dataflow)

OLAP store (ClickHouse / BigQuery)

📌 Architecture diagram included in the /diagrams folder.

## 📊 Data Model

Main tables:

links — stores short_id, long_url, metadata

click_events — records redirect metadata

owners — user-level ownership of links

ER diagram included in /diagrams.

## 📜 Requirements Summary
### Functional Requirements

Create short links

Resolve short links

Track clicks

Provide analytics

### Non-Functional Requirements

99.99% redirect availability

p95 < 50ms latency

Multi-region deployment

Strong consistency for mappings

Eventual consistency for analytics

## 🔧 Engineering Notes

This repo includes details on:

Capacity planning

API design

Data storage strategy

Caching & indexing

Retry/backoff mechanisms

Logging, metrics, tracing

Maintenance & failover plan


