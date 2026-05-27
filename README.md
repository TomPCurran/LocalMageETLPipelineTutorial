# Local ETL Pipeline with Mage.ai + Postgres (Docker)

This repo is a tutorial-style, locally hosted ETL stack designed for data scientists: **Mage.ai** orchestrates pipelines, and **PostgreSQL** stores results — all containerized with **Docker Compose**.

## Goals

This tutorial is for data scientists who want a **local, reproducible ETL environment** without standing up cloud infrastructure or managing a heavy orchestration platform like Airflow.

By the end of the series, you will have built a small but complete pipeline that:

- **Extracts** data from an external source
- **Transforms** it with Python (Pandas)
- **Loads** it into PostgreSQL for analysis

Everything runs on your machine via Docker Compose, so you can iterate quickly, reset the environment when needed, and reuse the setup for side projects or prototyping.

You do **not** need prior experience with Docker or Mage.ai — each part introduces the concepts you need as you go.

---

## Outcomes

After working through all three parts (or checking out the corresponding branches), you will be able to:

1. **Run a local ETL stack** — spin up Mage.ai and PostgreSQL with a single `docker compose up` command, and tear it down cleanly when you're done.
2. **Build Mage.ai pipelines** — create Data Loader, Transformer, and Data Exporter blocks; connect them in the Mage UI; and run pipelines end to end.
3. **Persist data in PostgreSQL** — load transformed data into a local database, including upsert patterns so re-runs don't create duplicates.
4. **Understand Docker Compose basics** — read and modify a `docker-compose.yml` to add services, wire environment variables, and manage volumes and networking.
5. **Connect downstream tools** — point a Jupyter notebook, DBeaver, or pgAdmin at your local Postgres instance to explore pipeline output and build new analyses on top of it.

### What you'll have at each stage

| Stage  | Branch                          | What you can do                                                                                  |
| ------ | ------------------------------- | ------------------------------------------------------------------------------------------------ |
| Part 1 | `part-1-infrastructure`         | Postgres and Mage containers are running; you can open the Mage UI and connect to the database.  |
| Part 2 | `part-2-orchestration`          | A working Extract → Transform pipeline; data flows through Mage blocks but is not yet persisted. |
| Part 3 | `part-3-persistence-automation` | Full Extract → Transform → Load pipeline with upserts, validation, and scheduling triggers.      |

---

## Repository branch roadmap

To help you follow along (or jump straight to a later stage), the repo is organized into tactical branches:

- **`main`**: The landing branch with this `README.md` and the high-level architecture.
- **`part-1-infrastructure`**: Core container infrastructure configs (`docker-compose.yml`, `.env.example`) to spin up the local environment.
- **`part-2-orchestration`**: Mage pipeline + DB connectivity (`io_config.yaml`) and the **Extract** (Data Loader) + **Transform** blocks.
- **`part-3-persistence-automation`**: Finalized codebase with the **Load** (Data Exporter) upsert block, data validation scripts, and orchestration triggers.

---

## Tech stack

- **Orchestrator**: [Mage.ai](https://www.mage.ai/)
- **Database**: PostgreSQL 16
- **Containerization**: Docker + Docker Compose
- **Data processing**: Python 3, Pandas, Requests

---

## Prerequisites

- **Docker Desktop** (or Docker Engine) with **Docker Compose v2** (`docker compose ...`)
- **Git**
- (Optional) A Postgres client like **DBeaver** or **pgAdmin**

---

## Quickstart

### 1) Clone the repository

```bash
git clone https://github.com/TomPCurran/LocalMageETLPipelineTutorial.git
cd LocalMageETLPipelineTutorial
```

### 2) Check out a runnable tutorial stage

The `main` branch is intentionally lightweight (docs + high-level structure). To run the Dockerized stack locally, check out the infrastructure stage:

```bash
git checkout part-1-infrastructure
```

### 3) Start the stack

```bash
docker compose up -d
docker compose ps
```

### 4) Open the services

- **Mage.ai UI**: `http://localhost:6789`
- **Postgres**: `localhost:5657` (use the credentials configured via your environment / `.env`)

---

## Stopping / resetting

Stop containers (keeps volumes):

```bash
docker compose down
```

Full reset (deletes volumes — **database data will be removed**):

```bash
docker compose down -v
```

---

## Medium article series

- **Part 1**: Containerizing Infrastructure with Docker and PostgreSQL — _link coming_
- **Part 2**: Orchestrating the Ingestion Pipeline with Mage.ai — _link coming_
- **Part 3**: Data Persistence, Upserts, and Automation — _link coming_
