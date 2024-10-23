
# n8n

[![License: Apache 2.0](https://img.shields.io/github/license/n8n-io/n8n)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/n8n-io/n8n)](https://github.com/n8n-io/n8n/releases)
[![Docker Pulls](https://img.shields.io/docker/pulls/n8nio/n8n)](https://hub.docker.com/r/n8nio/n8n)
[![Join Discord](https://img.shields.io/discord/763807565482344448)](https://discord.com/invite/3TqWzX5EzA)

n8n is a free and open workflow automation tool that enables you to automate tasks, processes, and workflows with powerful integrations. n8n offers a visual, node-based interface to create workflows and can be self-hosted for full control of data privacy.

---

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Running with Docker](#running-with-docker)
  - [Running with NPM](#running-with-npm)
- [Creating Workflows](#creating-workflows)
  - [Nodes](#nodes)
  - [Triggers](#triggers)
  - [Integrations](#integrations)
- [Using the API](#using-the-api)
- [Self-hosting](#self-hosting)
- [Community & Support](#community--support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Workflow Automation**: Build automated workflows using a visual interface without any coding required.
- **Integrations**: Connect with over 200+ services, including databases, SaaS applications, APIs, and more.
- **Triggers & Events**: Use triggers like webhooks, time events, or other external events to start your workflow.
- **Node-based Structure**: Each integration and action in a workflow is represented by a node.
- **API Access**: Extend and integrate n8n workflows programmatically through its API.
- **Self-hosted**: Full control of your data with self-hosting options.
- **Scalable**: n8n is cloud-native and can scale across multiple environments.
- **Security**: Control where and how your workflows run with full transparency into your data.

---

## Getting Started

### Installation

There are multiple ways to install and run n8n depending on your preferred setup.

### Running with Docker

The recommended way to run n8n is by using Docker. If you don’t have Docker installed, follow the instructions [here](https://docs.docker.com/get-docker/).

1. Pull the n8n image:
   ```bash
   docker pull n8nio/n8n
   ```

2. Run n8n:
   ```bash
   docker run -d -p 5678:5678 n8nio/n8n
   ```

3. Access n8n by opening your browser and navigating to `http://localhost:5678`.

### Running with NPM

You can also install n8n using Node.js.

1. Install n8n globally:
   ```bash
   npm install n8n -g
   ```

2. Start n8n:
   ```bash
   n8n
   ```

3. Access n8n at `http://localhost:5678`.

---

## Creating Workflows

Once n8n is up and running, you can begin creating your workflows.

### Nodes

Workflows in n8n consist of nodes. Each node performs a specific action, such as sending an HTTP request, querying a database, or manipulating data.

### Triggers

Triggers are special nodes that start a workflow when an event occurs. For example:
- **Webhook trigger**: Start the workflow when a webhook is received.
- **Cron trigger**: Execute the workflow on a scheduled time.

### Integrations

n8n supports integrations with more than 200 services and APIs. Some popular integrations include:
- Slack
- GitHub
- Google Sheets
- Airtable
- MySQL/PostgreSQL

You can easily combine different integrations in a workflow to automate processes across various platforms.

---

## Using the API

n8n also provides an API to interact with workflows programmatically. You can trigger workflows, retrieve data, or control the workflow execution with REST API endpoints.

Example API usage:
```bash
curl -X POST http://localhost:5678/api/v1/workflows/execute
```

API documentation is available to guide you in integrating n8n with external systems.

---

## Self-hosting

n8n can be self-hosted for those who prefer full control over their workflows and data. Self-hosting allows you to:
- Ensure data privacy
- Customize environment settings
- Scale the infrastructure based on your needs

### Self-hosting options

- **Docker**: Easily deploy and manage n8n with Docker.
- **Cloud providers**: Host n8n on platforms such as AWS, DigitalOcean, or Azure.

Refer to the [Self-hosting documentation](https://docs.n8n.io) for in-depth guides and examples.

---

## Community & Support

n8n has an active community where you can seek support, report issues, or contribute to discussions:

- **Discord**: Join the [Discord](https://discord.com/invite/3TqWzX5EzA) community for live discussions.
- **GitHub Issues**: Report bugs or request features in the [GitHub Issues](https://github.com/n8n-io/n8n/issues) section.
- **Forum**: Participate in the official [n8n forum](https://community.n8n.io) for broader discussions.

---

## Contributing

We welcome contributions from the community! To get started:

1. Fork the repository.
2. Create a branch for your feature or bugfix.
3. Make your changes and ensure all tests pass.
4. Submit a pull request.

Read the [contributing guide](CONTRIBUTING.md) for more details.

---

## License

n8n is licensed under the Apache 2.0 License. See the [LICENSE](LICENSE) file for more information.

---

## Stay Updated

- Official Website: [https://n8n.io](https://n8n.io)
- Documentation: [https://docs.n8n.io](https://docs.n8n.io)
