
# FlowiseAI

[![License: MIT](https://img.shields.io/github/license/FlowiseAI/Flowise)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/FlowiseAI/Flowise)](https://github.com/FlowiseAI/Flowise/releases)
[![Docker Pulls](https://img.shields.io/docker/pulls/flowise/flowise)](https://hub.docker.com/r/flowise/flowise)
[![Join Discord](https://img.shields.io/discord/123456789012345678)](https://discord.com/invite/flowise)

Flowise is an open-source, visual low-code framework to build AI applications. It enables developers and non-technical users alike to create powerful AI workflows and applications without extensive coding, by leveraging a visual drag-and-drop interface.

---

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Running with Docker](#running-with-docker)
  - [Running with NPM](#running-with-npm)
- [Creating AI Workflows](#creating-ai-workflows)
  - [Nodes](#nodes)
  - [Triggers](#triggers)
  - [Integrations](#integrations)
- [API Usage](#api-usage)
- [Self-hosting](#self-hosting)
- [Community & Support](#community--support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Visual AI Workflow Builder**: Use the drag-and-drop interface to create AI-powered workflows and applications.
- **Low-Code Environment**: Build and deploy AI applications without needing deep coding knowledge.
- **Customizable AI Models**: Integrate custom AI models or use pre-built ones to enhance workflows.
- **Integrations**: Easily connect your workflows with external services, APIs, databases, and more.
- **Self-hosted**: Flowise can be hosted on your infrastructure, ensuring complete data privacy.
- **Scalable**: Built for cloud-native deployment and scalable across distributed systems.
- **AI-Powered Automation**: Automate tasks using machine learning models, natural language processing (NLP), and more.

---

## Getting Started

### Installation

There are multiple ways to install and run Flowise depending on your setup and preference.

### Running with Docker

Docker is the easiest way to run Flowise. If you don’t have Docker installed, follow the instructions [here](https://docs.docker.com/get-docker/).

1. Pull the Flowise image:
   ```bash
   docker pull flowise/flowise
   ```

2. Run Flowise:
   ```bash
   docker run -d -p 3000:3000 flowise/flowise
   ```

3. Access Flowise by navigating to `http://localhost:3000` in your web browser.

### Running with NPM

You can also install Flowise using Node.js.

1. Install Flowise globally:
   ```bash
   npm install -g flowise
   ```

2. Start Flowise:
   ```bash
   flowise start
   ```

3. Access Flowise at `http://localhost:3000`.

---

## Creating AI Workflows

Once Flowise is up and running, you can start building AI workflows using the visual interface.

### Nodes

Workflows in Flowise are created by connecting nodes. Each node represents a task or action, such as data input, AI model execution, or external service integration.

### Triggers

Triggers initiate workflows based on external events. You can configure triggers like:
- **HTTP trigger**: Start workflows via an HTTP request.
- **Webhook trigger**: Start workflows when a webhook event is received.
- **Scheduled trigger**: Run workflows at scheduled intervals.

### Integrations

Flowise integrates with multiple external services, enabling users to build robust AI-powered applications that connect to:
- Databases (e.g., MySQL, PostgreSQL)
- APIs
- SaaS platforms (e.g., Google Cloud, AWS, OpenAI)

---

## API Usage

Flowise also provides an API to control workflows and automate processes programmatically. The API enables you to trigger workflows, retrieve data, and monitor their execution via HTTP endpoints.

### Example API Request

```bash
curl -X POST http://localhost:3000/api/v1/workflows/execute
```

Refer to the [API documentation](https://docs.flowise.com/api) for detailed instructions on how to interact with Flowise programmatically.

---

## Self-hosting

Flowise can be self-hosted on your infrastructure, offering complete control over your environment and data privacy. Self-hosting enables you to:
- Ensure data security
- Customize configurations and environment variables
- Scale the application to meet performance needs

### Self-hosting options

- **Docker**: Deploy Flowise on Docker for easy containerized hosting.
- **Cloud platforms**: Host Flowise on cloud providers like AWS, Google Cloud, or Azure.

Check out the [self-hosting documentation](https://docs.flowise.com/self-hosting) for more information.

---

## Community & Support

Flowise has an active community where you can find support, report bugs, and discuss feature requests:

- **Discord**: Join the [Flowise Discord](https://discord.com/invite/flowise) community for live discussions.
- **GitHub Issues**: Report bugs or request new features in the [GitHub Issues](https://github.com/FlowiseAI/Flowise/issues) section.
- **Forum**: Participate in discussions on the [Flowise Forum](https://community.flowise.com).

---

## Contributing

We welcome contributions from the community! To get started, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes and ensure all tests pass.
4. Submit a pull request.

Please refer to our [contributing guide](CONTRIBUTING.md) for more information.

---

## License

Flowise is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Stay Updated

- Official Website: [https://flowise.com](https://flowise.com)
- Documentation: [https://docs.flowise.com](https://docs.flowise.com)
