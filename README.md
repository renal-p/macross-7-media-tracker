# Relational Media Tracker & Database Seeding Utility

This repository contains a standalone database pipeline built to seed, map, and track contextual media metadata, specifically isolating episodic music cues and performance tracking across a series lifecycle.

## Core Architecture & Integrity Constraints

* **PostgreSQL Schema Seeding:** Utilizes parameterized `executemany` queries to handle bulk insertion operations across relational tables safely via a `psycopg2` database connection.
* **Idempotent Operations:** Implements explicit `ON CONFLICT DO NOTHING` clauses to prevent primary and unique key violations, ensuring the pipeline can be re-run safely without duplicating historical log records.
* **Foreign Key Mapping:** Programmatically fetches unique relational IDs to construct a dynamic lookup map dictionary (`song_id_map`), translating raw string inputs into exact relational foreign keys for historical appearance logs.
