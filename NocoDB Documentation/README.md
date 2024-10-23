
# NocoDB

[![License: AGPL v3](https://img.shields.io/github/license/nocodb/nocodb)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/nocodb/nocodb)](https://github.com/nocodb/nocodb/releases)
[![Docker Pulls](https://img.shields.io/docker/pulls/nocodb/nocodb)](https://hub.docker.com/r/nocodb/nocodb)
[![Join Discord](https://img.shields.io/discord/879715321393623070)](https://discord.com/invite/4fm7pgB)

NocoDB is an open-source Airtable alternative that transforms any relational database (MySQL, PostgreSQL, SQL Server, MariaDB, and others) into a no-code platform with a spreadsheet-like interface. It is designed for non-technical users to work seamlessly with databases while allowing technical users to manage backend processes.

---

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Running with Docker](#running-with-docker)
  - [Running with NPM](#running-with-npm)
- [Supported Databases](#supported-databases)
- [Usage](#usage)
  - [Connect Your Database](#connect-your-database)
  - [Collaborate](#collaborate)
  - [Automate](#automate)
  - [APIs](#apis)
- [Community & Support](#community--support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **No-code database interface**: Turn your relational database into a spreadsheet-like interface that can be used by anyone, even with no technical background.
- **Multi-database support**: Supports MySQL, PostgreSQL, MariaDB, SQLite, Microsoft SQL Server, Amazon Redshift, and many other SQL databases.
- **Collaboration**: Share, manage, and collaborate with team members in real-time.
- **Customizable views**: Create grid, gallery, Kanban, and calendar views of your data.
- **API Generator**: Automatically generate REST and GraphQL APIs for your database.
- **Automations**: Set up workflows and integrations to automate tasks within NocoDB or with third-party apps via Zapier, Integromat, or custom APIs.
- **Self-hosted**: NocoDB can be deployed on your server, giving you full control over your data and platform.
- **Cloud-native**: Can also be hosted on platforms like AWS, Azure, or DigitalOcean for scalability.
- **Extensible**: Customize NocoDB using plugins or integrate it with external applications.

---

## Getting Started

### Installation

There are multiple ways to install and run NocoDB depending on your setup and preference.

### Running with Docker

The easiest way to get started with NocoDB is by using Docker. If you don't have Docker installed, follow the instructions [here](https://docs.docker.com/get-docker/).

1. Pull the NocoDB image:
   ```bash
   docker pull nocodb/nocodb
   ```

2. Run NocoDB:
   ```bash
   docker run -d -p 8080:8080 nocodb/nocodb
   ```

3. Access NocoDB by opening your browser and navigating to `http://localhost:8080`.

For more advanced Docker configurations, visit the [Docker documentation](https://hub.docker.com/r/nocodb/nocodb).

### Running with NPM

You can also install and run NocoDB using Node.js.

1. Install NocoDB via NPM:
   ```bash
   npx create-nocodb-app
   ```

2. Run NocoDB:
   ```bash
   npx nocodb
   ```

3. Access NocoDB on `http://localhost:8080`.

> **Note**: Ensure that you have [Node.js](https://nodejs.org/en/download/) and NPM installed.

---

## Supported Databases

NocoDB supports a variety of SQL databases:

- MySQL
- PostgreSQL
- MariaDB
- SQLite
- Microsoft SQL Server
- Amazon Redshift
- And more!

Connect to any of these databases and instantly turn them into a smart spreadsheet for collaborative work.

---

## Usage

Once NocoDB is up and running, here's how to use it effectively.

### Connect Your Database

1. Open the NocoDB UI and click on "Connect Database."
2. Select the type of database you want to connect (MySQL, PostgreSQL, etc.).
3. Enter the database credentials (host, port, username, password).
4. Click "Connect" and your database schema will automatically load.

### Collaborate

Invite team members to your project, and work together in real-time. NocoDB offers a spreadsheet-style interface that is easy to navigate and edit for everyone, even those with no database experience.

- Assign user roles and permissions.
- Track changes and version control.
- Leave comments on records.

### Automate

NocoDB allows you to automate workflows and create custom triggers:

- Use built-in automations for workflows (e.g., on new row insert, update, or delete).
- Integrate with third-party tools like Zapier and Integromat for more complex automation.
- Trigger custom API calls or run scripts in response to changes.

### APIs

NocoDB automatically generates RESTful and GraphQL APIs for your database tables. You can interact with your database programmatically without writing a single line of code.

- **REST API**: All database tables are exposed via REST endpoints.
- **GraphQL API**: The schema is also accessible via GraphQL for more flexible queries.

API documentation is automatically generated, making it easy to integrate your database with external applications.

---

## Community & Support

NocoDB is a rapidly growing community-driven project. There are multiple ways to get involved and seek help:

- **Discord**: Join our [Discord](https://discord.com/invite/4fm7pgB) community to discuss NocoDB, share your ideas, or get support.
- **GitHub Issues**: Report bugs or suggest features on the [GitHub Issues](https://github.com/nocodb/nocodb/issues) page.
- **Twitter**: Follow us on [Twitter](https://twitter.com/Noco_db) for updates.

---

## Contributing

We welcome contributions from the community! To get started, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes and ensure all tests pass.
4. Submit a pull request.

Please read our [contributing guide](CONTRIBUTING.md) for more details.

---

## License

NocoDB is licensed under the GNU Affero General Public License v3.0. See the [LICENSE](LICENSE) file for details.

---

## Stay Updated

- Official Website: [https://www.nocodb.com](https://www.nocodb.com)
- Documentation: [https://docs.nocodb.com](https://docs.nocodb.com)
