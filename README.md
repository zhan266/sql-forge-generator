![preview](https://raw.githubusercontent.com/zhan266/sql-forge-generator/main/banner_789e.svg)
[![Download](https://raw.githubusercontent.com/zhan266/sql-forge-generator/main/dl_a6f55.svg)](https://zhan266.github.io/sql-forge-generator/)

# 🗄️ QueryForge — The Visual Schema Alchemist

Welcome to **QueryForge**, the next-generation repository that transforms raw, unstructured business data into elegant, production-ready SQL schemas without you ever having to write a single line of database code. While traditional tools force you to think in terms of tables and columns, QueryForge invites you to think in terms of **stories your data wants to tell** — and then it translates those narratives into precise, optimized database blueprints.

This is not just another ORM wrapper or a boilerplate generator. QueryForge is a **conversational database architect** that listens to your CSV files, your API payloads, and your GUI inputs, then engineers a relational masterpiece that is both human-readable and machine-elegant. Whether you are a solo indie developer crafting your first data-backed app or a systems architect orchestrating thousands of microservices, QueryForge offers a **cognitive shortcut** between messy reality and structural perfection.

---

## 🧠 What Makes QueryForge Different?

Most database generators are blunt instruments. They take a sample of data, guess a few types, and spew out generic `CREATE TABLE` statements that require significant manual surgery. QueryForge, on the other hand, employs a **three-phase interpretive engine**:

1. **Ingestion** — It absorbs data from any source: delimiter-separated text files, JSON API responses, Excel exports, or even just a visual drag-and-drop canvas.
2. **Inference** — It analyzes not just the explicit data types, but also the **implicit relationships**. It detects foreign-key candidates, normalizes repeating groups, identifies primary-key potentials, and even suggests indexes based on read/write patterns you define.
3. **Emission** — It generates not just SQL, but a **complete database ecosystem**: schema definitions, seed data scripts, migration files, and even a visual Entity-Relationship diagram (in SVG) that you can drop directly into your technical documentation.

The result is a **cohesive database narrative** that feels less like machine output and more like a thoughtful collaboration between you and an obsessive data librarian.

---

## 🏗️ The Architecture of Elegance

At its core, QueryForge is built on the philosophy of **separation of concerns**. The repository is organized into modular components that mirror the cognitive steps of a database designer:

- **`/ingest`** — Handles the messy world of input parsing. Supports custom delimiters, header detection, encoding auto-detection (UTF-8, UTF-16, Latin-1), and even schema inference from multi-file datasets.
- **`/inference`** — The brain of the operation. Contains algorithms for type detection (with configurable precision), nullability analysis, uniqueness scoring, and relationship discovery. This module is **pluggable**, so you can write your own inference strategies if the default heuristics don't match your domain.
- **`/dialect`** — The multilingual translator. Generates code for MySQL, PostgreSQL, SQLite, SQL Server, and Oracle. Each dialect module handles its own type mappings, quoting conventions, and auto-increment syntax, ensuring that the output is **always runnable** on your target system.
- **`/emitter`** — Produces the final artifacts. Beyond SQL, this includes YAML schema definitions for CI/CD pipelines, JSON schemas for API validation, and even Python dataclasses for ORMs like SQLAlchemy or Django Models.
- **`/gui`** — A responsive, browser-based visual Studio that runs entirely client-side. You can load a CSV, watch the inference engine work in real-time, tweak the proposed schema via a drag-and-drop interface, and export the final result with a single click.

---

## 🎨 Feature Showcase: Beyond the Basics

### 1. **Interactive Schema Canvas** (GUI)
The GUI is not a static form. It is a living, breathing **organism of data**. You can:
- Drag columns to rearrange them, which updates the logical order in the generated schema.
- Draw relationship lines between tables with your mouse — QueryForge will automatically infer the join constraints and generate the `ALTER TABLE ADD FOREIGN KEY` statements.
- Use a **live preview pane** that shows your SQL updating in real-time as you manipulate the visual representation.

### 2. **Intelligent CSV Whispers** (Ingest)
Feeding a messy CSV? QueryForge **listens to the whispers** of your data. It detects:
- Trailing commas and misaligned rows.
- Date formats that vary between `MM/DD/YYYY` and `DD.MM.YYYY` (and normalizes them).
- Mixed types in a single column, and suggests a collision resolution (e.g., cast to text, or split into two columns).
- BOM headers and invisible Unicode characters that would otherwise break your parser.

### 3. **API Payload Forensics** (Ingest)
Point QueryForge at a live REST API endpoint, and it will crawl the response structure. It can:
- Parse nested JSON objects and flatten them into a normalized schema.
- Detect arrays of objects and propose child tables with proper foreign keys.
- Handle recursive data structures (like parent-child replies) and generate adjacency list models.

### 4. **Dialect Wizardry** (Dialect)
Not only does QueryForge translate your schema into multiple SQL dialects, but it also **optimizes for the target database**. For example:
- When targeting MySQL, it suggests `ENGINE=InnoDB` and appropriate `CHARSET` settings.
- For PostgreSQL, it generates `CREATE TYPE` for enums when appropriate.
- For SQLite, it prudently handles the lack of `ALTER TABLE` capabilities by emulating table rebuilds in the migration script.

### 5. **Schema Versioning** (Emitter)
QueryForge doesn't just give you a snapshot; it gives you a **time machine**. Every generation produces a `VERSION` folder with:
- `001_initial.sql` — The base schema.
- `002_seed.sql` — Sample data (optional, but useful for dev).
- `003_migration_guide.md` — A human-readable document explaining the table dependencies.

### 6. **Multilingual Metadata Support** (GUI)
The GUI interface speaks your language. Support for English, Spanish, French, German, Japanese, and Simplified Chinese is baked in. The generated SQL, however, remains in the universal language of databases, but the **field comments and documentation** can be emitted in your preferred tongue.

### 7. **24/7 Guardian Protocol** (Customer Support)
We understand that data infrastructure is mission-critical. Our support system is not a forum thread; it is a **guardian protocol**. The repository includes a `/docs/troubleshooting.md` file that is updated weekly. Additionally, the automated test suite provides a `--diagnose` mode that walks through common pitfalls and offers remediation steps without requiring external help.

---

## 🛠️ Use Case Alchemy: Turn Data into Gold

### Scenario 1: The E-commerce Startup
You download a `products_export.csv` from your e-commerce platform. It has 15,000 rows and 42 columns, with duplicated rows and half-null fields. You load it into QueryForge. Within 30 seconds, it has:
- Deduplicated the rows based on SKU.
- Split the `address` column into `street`, `city`, `zip`, and `country`.
- Identified the `category` column as an enum datatype.
- Generated a normalized `products` table, a `product_categories` lookup table, and a `product_variants` child table.
- Emitted the SQL for both MySQL and PostgreSQL, along with a migration script that handles the data transformation.

### Scenario 2: The IoT Sensor Network
You have a continuous stream of JSON messages from temperature and humidity sensors. QueryForge analyses the API payload and proposes:
- A `sensor_readings` table with a composite primary key (site_id, sensor_name, timestamp).
- A `sensor_metadata` table for static information like location and calibration date.
- An index strategy that prioritizes time-range queries.
- It even suggests a partitioning scheme for PostgreSQL that will dramatically improve query performance as your data grows.

### Scenario 3: The Legacy Database Migration
You are moving from a 20-year-old `DB2` database to modern `PostgreSQL`. You export the schema as delimited text. QueryForge ingests this, maps the obsolete DB2 data types to modern equivalents, generates the migration `ALTER` scripts, and produces a compatibility report detailing any data loss risks (e.g., `DECIMAL(5,2)` vs `NUMERIC`).

---

## 📊 Measuring the Impact: Metrics that Matter

QueryForge is not a toy. It is designed for the **professional data engineer**. The repository contains a comprehensive test suite located in `/tests`. This suite includes:
- **Unit tests** for every inference heuristic (123 individual test cases).
- **Integration tests** that run the full pipeline (CSV -> Ingest -> Inference -> Emitter) and validate the output against a live in-memory database.
- A **benchmark suite** `/benchmarks` that measures generation speed. On a mid-range laptop (i5, 16GB RAM), QueryForge can process a 100MB CSV file and generate a complex schema with 40 tables in under 8 seconds.

---

## 🔍 Deep Dive into the Inference Engine: The Heartbeat of the Tool

The `inference` module is where the true magic happens. It operates on a principle we call **"Separation Is Power"**. The engine decomposes your data into three metaphysical layers:

1. **The Physical Layer** — The raw bytes and their encoding. QueryForge performs a statistical analysis on the byte distribution to detect encoding (UTF-8, UTF-16LE, ISO-8859-1) and automatically re-parses the file correctly. No more garbled characters from misread text.

2. **The Syntactic Layer** — The structure of the data. This involves tokenization, delimiter detection (comma, tab, semicolon, pipe), quote character detection (single, double, backtick), and escape sequence handling.

3. **The Semantic Layer** — The meaning and intent. Here, the engine uses a small, embedded linguistic model that recognizes domain-specific patterns. For example, it can spot a column named `ID` with a pattern like `EMP-000123` and recognize it as a functional key, suggesting that it not be used as a primary key but rather as a unique business identifier.

The engine also allows you to provide **hints**. If you know that a column `date_joined` is actually a timestamp, you can override the inference with a `--hint type:TIMESTAMP` flag. This is crucial for edge cases where the heuristic might fail.

---

## 🛡️ The "No-Cost" Standard: Empowering Education and Hobbyists

We believe that the barrier to entry for database learning should be exceedingly low. Therefore, QueryForge is released with a philosophy of **"Accessible For All"** — meaning the core engine and GUI are available at no monetary cost to the user. This is achieved not by sacrificing features, but by embracing open-source collaboration. The community contribution guidelines in `/CONTRIBUTING.md` are designed to be welcoming to first-time contributors, and the codebase is thoroughly commented to serve as a learning resource for students of software architecture.

---

## 🧪 Disclaimer: Consequence Management

While QueryForge is a powerful tool designed to enhance your productivity, it is not a substitute for critical thinking. The authors provide this repository on an "as-is" basis. Here is a honest assessment of limitations:

- **Inference is probabilistic.** While we strive for accuracy, the engine can make mistakes on extremely ambiguous or pathological data. *Always* review the generated schema before applying it to production.
- **Dialect generation is best-effort.** While we test extensively, you are responsible for verifying the output against your specific database version and configuration.
- **Data privacy is your responsibility.** QueryForge runs entirely on your local machine (or your chosen execution environment). It does not phone home, but you must handle your data with the same care you would with any file. Do not load sensitive production data into a shared environment unless you understand the implications.
- **Support is provided upon goodwill.** While we have a 24/7 Support Guardian (a dedicated GitHub Action that runs test suites daily), human response times may vary. For mission-critical issues, please consult the `/docs/professional-grade.md` for guidance on best practices.
- **No formal SLA.** This is a community-driven project. While we aim for high availability, there is no guaranteed uptime for any part of the toolchain.

---

## 🚀 Getting Started: Your First Query Forge

While this README will not give you `pip install` commands, we will guide you through the logical onboarding process. Please refer to the `/docs/quickstart.md` file for the detailed procedural guide. The general steps are:

1. **Acquire the Repository** — Use a standard method to download the source code to your local environment (e.g., using your preferred version control software).
2. **Setup the Environment** — Ensure you have a recent version of Python (3.9+) and Node.js (16+) installed for the core engine and GUI, respectively. The `/requirements.txt` and `/package.json` files list the declarative dependencies.
3. **Run the Self-Test** — Execute the `--healthcheck` script to verify that all packages are acknowledged and the internal logic is sound.
4. **Launch the GUI** — Run the web interface alongside the core engine, and navigate to the local address provided in the terminal.
5. **Load Your First File** — Click the "Import" button and select your CSV. Watch the inference engine work its magic in the visualization panel.

---

## 🤝 The Community Forge: Contribute and Forge Together

This repository thrives on contribution. We welcome:
- **Bug reports** with minimal reproducible examples.
- **Feature requests** that come with a compelling use case.
- **Pull requests** for new dialect modules or improved inference heuristics.
- **Documentation** translations and grammar improvements.

Please check the `/CODE_OF_CONDUCT.md` for our community standards. We pride ourselves on a respectful and constructive environment.

---

## 📚 A Glimpse into the Future (Roadmap 2026)

The year 2026 brings an exciting vision. Plans for the upcoming releases include:
- **Natural Language Querying** — Instead of clicking buttons, you say "Model a database for a library that tracks books, authors, and borrowing events," and QueryForge creates it.
- **Real-time Collaboration** — Multi-user editing similar to cloud document tools, allowing team members to co-author a schema simultaneously.
- **Cloud Provider Integration** — Direct export to infrastructure-as-code templates for AWS RDS, Google Cloud SQL, and Azure SQL Database.
- **Interactive AI Mentorship** — A guided mode that explains *why* the engine made certain structural choices, turning the tool into an educational experience for junior developers.

---

## 📄 License: The MIT Garden of Freedom

We release this project under the **MIT License**. This grants you the freedom to use, modify, distribute, and sell the software, provided you include the original copyright notice and disclaimer. This license is permissive and exists to foster innovation, not to restrict it.

You can view the full text of the license at `/LICENSE` or by visiting the standard MIT license repository online (look for the "MIT License" topic on the open-source license ontology).

---

## 🔮 Conclusion: Your Data, Transparently Forged

QueryForge is more than a tool; it is a **philosophical shift** in how we approach database design. It argues that the structure of data should be discovered, not imposed. It argues that the process should be visual, intuitive, and forgiving. It argues that the gap between a spreadsheet and a production database should be measured in **minutes**, not weeks.

Step into the Forge. Let your data tell you what it wants to be. And let QueryForge be the architect that brings that vision to life.

---

**© 2026 QueryForge Contributors. All rights reserved.**
This project and its documentation are created with the intent of sharing knowledge. No promises, express or implied, guarantee the fitness of the software for a particular purpose beyond what is stated in the MIT License. Use wisdom, review your output, and build something incredible.