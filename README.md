# 🧱 OpenWebUI (OWUI) - Complete Locker (Nvidia GPU)

**Template ID:** b005baf7-bf60-4841-972c-40b9172c461b  
**Created by:** Iamobservable, MaxFrenzy  
**Created on:** June 2025  

**Locker Create Command:**

```bash
locker create b005baf7-bf60-4841-972c-40b9172c461b
```


## 📚 Table of Contents

1. [Summary](#summary)
2. [Who Is It For?](#who-is-it-for)
3. [Use Cases](#use-cases)
4. [Included Services Overview](#included-services-overview)
5. [Interface & Feature Previews](#interface--feature-previews)
6. [Requirements](#requirements)
7. [Installation](#installation)
8. [Post-Installation Setup](#post-installation-setup)
9. [Learn More](#learn-more)
10. [Project Status](#project-status)



## Summary

This Locker template provides you with a full local AI environment built around OpenWebUI, an extensible, feature-rich, and user-friendly self-hosted AI platform designed to operate entirely offline. The template serves to stand-up the environment around OWUI and provide a privacy focused and free alternative to cloud-based AI platforms like Chat-GPT or Claude. It leverages features within OpenWebUI and provides sane defaults intended to accelerate your experience setting up and using local AI tools. Specifically, intent was directed into providing services for authentication, enhanced file support and document parsing, improved text-to-speech voice options, local web search, tool access with MCP, and more. Built for users who want complete control over their tools, this stack is privacy-respecting, fully self-hosted, and designed to be extended.



## Who Is It For?

* Anyone looking for a locally hosted alternative to Chat-GPT, Claude, or similar AI tools
* Developers working around OpenWebUI or Ollama
* People looking for more control over their data and AI functionality
* Anyone looking to jump start or enhance their OpenWebUI setup and usage experience
* Builders exploring local knowledge stores, voice, web search, or multi-modal workflows



## Use Cases

* Run local LLMs with OpenWebUI and Ollama
* Generate reports and ask questions using your PDFs, Word docs, spreadsheets and other files (via Tika & Docling)
* Talk to your assistant with more natural-sounding voices (EdgeTTS)
* Query data from the web and integrate results into chats (SearxNG)
* Explore MCP tools easily - try out the examples to add time and database knowledge to your AI (MCPO Server)
* Maintain memory, knowledge bases, chat history and document embeddings (Postgres + PgVector)



## Included Services Overview

| Service | Purpose |
|--------|---------|
| [**Auth**](https://github.com/iamobservable/jwt-auth-validator) | JWT validation - gatekeeping for web endpoints |
| [**Docling**](https://github.com/docling-project/docling-serve) | Enhanced document handling for PDFs and other formats |
| [**Edge TTS**](https://github.com/rany2/edge-tts) | Text-to-speech using natural sounding voices |
| [**MCP Server**](https://modelcontextprotocol.io/introduction) | Integrates tools (e.g., time, database information) via API |
| [**Nginx**](https://nginx.org/) | Reverse proxy for routing traffic and load balancing |
| [**Ollama**](https://ollama.com/) | Local model runtime for accessing open-source AI models |
| [**OpenWebUI**](https://openwebui.com/) | Main interface for AI chat & tool usage |
| [**PgVector**](https://github.com/pgvector/pgvector) | Embedding store for RAG and storage queries |
| [**Postgres**](https://www.postgresql.org/) | Primary database for persistence |
| [**Redis**](https://redis.io/) | Cache and index store for SearxNG |
| [**SearxNG**](https://docs.searxng.org/) | Local meta search engine with scraping |
| [**Tika**](https://tika.apache.org/) | Document parser for data extraction |
| [**Watchtower**](https://github.com/containrrr/watchtower) | Auto-updates containers silently and can send notifications to Discord |


## Interface & Feature Previews
If you're familiar with Chat-GPT, the OpenWebUI interface is incredibly similar and operates in much the same way. Below you can see a side-by-side of the OWUI web inteface next to Chat-GPT. Access to adding files, initiating a web search, starting a voice call, and entering text can all be accessed in a familiar fashion.

![owui-complete-locker-chat-gpt-comparison2](https://github.com/user-attachments/assets/1af1a8a4-88b1-48a7-bf41-ade115ab5d87)

The OpenWebUI Complete Locker adds a personal instance of Searxng, a local meta search engine for use as a standalone web search utility or to enhance AI models with web info. 

![owui-complete-locker-searxng-landing](https://github.com/user-attachments/assets/e2074aaf-3393-49d9-83f8-6403463186c2)


*Additional screenshots of web search, document parsing, chat interface, and voice conversation coming soon.*


## Requirements

* Windows 10/11 (with [WSL](https://learn.microsoft.com/en-us/windows/wsl/) installed) or Linux
* [Docker](https://www.locker.com/) - Docker Desktop recommended. If you don't have Docker installed, Docker Desktop will install the WSL environment for you on Windows installations.
* NVIDIA GPU - The OpenWebUI Complete Locker template has been configured to use Nvidia GPUs. 
* [Locker](https://github.com/iamobservable/locker)



## Installation

Before beginning installation, confirm that:

* Docker is installed
* WSL is installed (if using Windows)
* Locker is installed

### 1. Run the create command:

```bash
locker create b005baf7-bf60-4841-972c-40b9172c461b
```

You’ll be prompted to fill:

| Field             | Example     | Description                                        |
| ----------------- | ----------- | -------------------------------------------------- |
| Host              | `localhost` | Address where the stack will run - localhost or IP |
| Port              | `4000`      | Web port for accessing OpenWebUI                   |
| Secret Key        | `secretkey` | A unique key for authentication across services    |
| Database Name     | `owui`      | Postgres DB name                                   |
| Database User     | `postgres`  | Postgres user                                      |
| Database Password | `postgres`  | Postgres password                                  |

![owui-complete-locker-install-linux](https://github.com/user-attachments/assets/71084e72-fd72-468d-9042-2e4a73530482)

After the environment has been configured, you'll be returned to the command line.

![owui-complete-locker-post-install-screen](https://github.com/user-attachments/assets/0302e543-1882-49d2-a961-7ac1109f4ad1)


### 2. Run Docker Compose Up

```bash
docker compose up -d
```

![owui-complete-locker-docker-compose-up](https://github.com/user-attachments/assets/05de2769-7756-4955-86f1-ef3cbef198f9)

After you run the command, the output will show the containers being created and started.

![owui-complete-locker-installation-complete](https://github.com/user-attachments/assets/b8971923-a15b-4a35-a3ef-0b4734d47228)


### 3. Verify in Docker Desktop

Open Docker Desktop to confirm all containers are up and running.

![owui-complete-locker-docker-desktop-containers](https://github.com/user-attachments/assets/9c95e010-c391-45f4-b94e-b8ed8ed29503)


### 4. Launch OpenWebUI

Open a browser and visit `localhost:4000` (or your custom IP/port).

![owui-landing-page](https://github.com/user-attachments/assets/e7fa5c5d-fbdf-4b6f-af39-29b4f5c63076)


### 5. Create Admin Credentials

After clicking "get started", OpenWebUI will prompt you to create your administrator account. Enter appropriate user info and proceed.

![owui-admin-setup](https://github.com/user-attachments/assets/b6032ddd-1f89-40c1-8942-ab6eb8895758)


### 6. Start a Chat

Send a message! By default, [Qwen3:0.6B](https://ollama.com/library/qwen3:0.6b) is pulled from Ollama as part of this setup. If the pull was successful, you should be able to begin chatting. 

![owui-complete-locker-hello-qwen3](https://github.com/user-attachments/assets/b53a98c1-0273-4738-99bf-b18cfae29c5b)

Additional models can be pulled from within the Admin panel of the OWUI interface under `models` or by using Ollama directly.

![owui-admin-settings-models](https://github.com/user-attachments/assets/540a1833-8442-402f-a606-1e9a945b5f33)
 
A [list of models](https://ollama.com/search) is available on Ollama's website. By default, this Locker includes access to [**Qwen3-0.6B**](https://ollama.com/library/qwen3:0.6b), a reasoning model known for showing its thought process in OpenWebUI. It also interacts intuitively with tools and external modules. The model provided here is meant as a **starting point**, not a definitive answer. The world of models is vast—each with unique strengths, system requirements, and quirks when used within OpenWebUI.

For more information on accessing models:

- [OpenWebUI documentation on models](https://docs.openwebui.com/features/workspace/models)
- [Ollama documentation from GitHub](https://github.com/ollama/ollama)

Continue on to the post-installation setup below for final configuration steps.

## Post-Installation Setup

### **MCP Servers**

Model Context Protocol (MCP) is a configurable set of tools, resources, prompts, samplings, and roots. They provide a structured way to expose local functionality to the LLM. Examples are providing access to the local file system, searching the internet, interacting with git or github, and much more.

#### **Manual entry (MUST COMPLETE)**

The configuration for tools currently requires a manual step to complete. At this time, we are unable to automate this portion of the setup. In order to use the two default tools, it is required to add them manually. **They will NOT** automatically load using the environment variable TOOL\_SERVER\_CONNECTIONS within the openwebui.env file, despite being present.

Add the following two URLs using the Settings -> Tools -> General interface. This can also be set in the Admin Settings as well.

*Note - the default postgres tool is configured to access your OpenWebUI postgres database. While this is read-only, the tool server that is defined allows any user with the credentials added to the `env/mcpo.env`to access the database tables. If anything should be restricted, make sure to do so ahead of time.*

```
http://mcposerver:8000/time
```

```
http://mcposerver:8000/postgres
```
![owui-settings-tools](https://github.com/user-attachments/assets/3ef404b1-6a6c-4262-9036-ff48d971db91)

![owui-settings-tools-add-connection](https://github.com/user-attachments/assets/cfb6c255-7251-4577-8878-7567dad6208c)


**Initial configuration**

Configurations for MCP services can be found in your install directory under `conf/mcpo/config.json`. Links below in the table describe the default configuration.

*Note - the time tool is configured using uvx instead of directly with the python binary, as the repository describes.*

You may expand on the tools available to your interface. A few examples are listed below.

| Tool                                                                               | Description                                                                                                                                             | Configuration                                                                                                              |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| [time](https://github.com/modelcontextprotocol/servers/tree/main/src/time)         | Provides current time values for configured timezone | config/mcpo/config.json                                                                                                    |
| [postgres](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres) | Provides SQL querying for the configured database (defaults to OpenWebUI)                                                                               | config/mcpo/config.json |

#### **MCP Server Discovery**

If you are looking for tools to add, the following three MCP Server sources are a great place to look. It may even inspire you to create your own over time!

* [Model Context Protocol servers](https://github.com/modelcontextprotocol/servers?tab=readme-ov-file#model-context-protocol-servers)
* [Awesome MCP Servers](https://mcpservers.org/)
* [Smithery](https://smithery.ai/)

---

## Learn More

To learn more about the services included in this Locker template, explore the links below.

* **[Cloudflare](https://www.cloudflare.com/)**: Platform providing anonymous proxying and SSL certificates
* **[Docling](https://github.com/docling-project/docling-serve)**: Simplifies document processing, parsing diverse formats — including advanced PDF understanding — and providing seamless integrations with the gen AI ecosystem (created by IBM)
* **[Edge TTS](https://github.com/rany2/edge-tts)**: Python module that uses Microsoft Edge's online text-to-speech service
* **[MCP Server](https://modelcontextprotocol.io/introduction)**: Open protocol that standardizes how applications provide context to LLMs
* **[Nginx](https://nginx.org/)**: Web server, reverse proxy, load balancer, mail proxy, and HTTP cache
* **[Ollama](https://ollama.com/)**: Local service API serving open source large language models
* **[OpenWebUI](https://openwebui.com/)**: Open WebUI is an extensible, feature-rich, and user-friendly self-hosted AI platform designed to operate entirely offline
* **[PostgreSQL](https://www.postgresql.org/)** / **[PgVector](https://github.com/pgvector/pgvector)**: A free and open-source relational database management system (RDBMS) with vector capabilities for embeddings
* **[Redis](https://redis.io/)**: In-memory data structure store used as a database, cache, and message broker
* **[SearxNG](https://docs.searxng.org/)**: Free internet metasearch engine used for tool integration with OpenWebUI
* **[Tika](https://tika.apache.org/)**: Toolkit for extracting metadata and text from various file formats
* **[Watchtower](https://github.com/containrrr/watchtower)**: Automated Docker container for updating container images automatically

To learn more about Locker, check out the project on GitHub:

**[Locker](https://github.com/iamobservable/locker)** — A command line tool for building pre-configured/curated AI environments.

## Project Status

This README and Locker template are provided as-is and represent a complete, functional starting point for WebUI experimentation. While future updates may be limited, issues or suggestions are welcome via GitHub.
