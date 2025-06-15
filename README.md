## Locker File: Open WebUI Starter
Author: IamObservable, MaxFrenzy
Created: 06-05-2025
### Locker Launch Command

```
locker --build b0034-2323-2323-3344-29823
```

### Locker Summary

Spin up your own professional, pre-configured AI stack on your own subdomain—faster than you can say "Ollama!"  
This Locker builds and configures a complete, modular AI environment around [Open WebUI](https://www.openwebui.com), a powerful, self-hosted interface for working with local language models.

Included is a full suite of production-ready components:

- Secure public access with Cloudflare Zero Trust Tunnels
- A reverse-proxied, load-balanced web server (Nginx)
- High-speed caching (Redis), vector search (PgVector), and a Postgres database
- Private web search with SearxNG
- Document extraction via Tika and Docling
- Natural text-to-speech using Edge TTS
- Tool and API extensibility via MCP
- Automatic container updates with Watchtower

It’s the fastest way to go from an empty terminal to a full-featured private AI assistant you can access from anywhere.

**Requirements:**
- A domain name (e.g. yourdomain.com)
- DNS for your domain pointed at [Cloudflare](https://www.cloudflare.com) (Free)
- NVIDIA Gpu?

**Time Check:**
If you're already using Cloudflare and have your domain pointed to it, setup time from Zero Trust Tunnel creation to chatting with your AI is **under 30 minutes**. All the complex setup has been automated for you. You’re stepping into a system refined through months of configuring, testing, and learning—delivered in minutes.

### What’s Inside the Locker?

#### [**Cloudflare**](https://www.cloudflare.com/)

Cloudflare provides a free way to create a secure tunnel to make your OpenWebUI instance available to you from outside your local network. In other words, this connects your domain name to your local machine running OpenWebUI in a safe way that doesn't expose the rest of your network.

This allows you to:

- Access your AI server from anywhere you have an internet connection
- Invite users or collaborators without dealing with VPNs or port forwarding
- Protect your home network while giving controlled public access to OpenWebUI

Cloudflare’s Zero Trust Tunnel makes this possible on their **free plan**, and it integrates cleanly into the stack with minimal configuration. It’s fast, secure, and battle-tested. 
  
#### [**Docling**](https://github.com/docling-project/docling-serve)

Docling is a document processing library designed to transform a wide range of file formats—including PDFs, Word documents, spreadsheets, HTML, and images—into structured data such as JSON or Markdown.

Within OpenWebUI, Docling is one of several available methods (in addition to the default content extraction engine and others like Tika) for robust file handling and content extraction. It's especially helpful when working with diverse or complex file types that need to be embedded, summarized, or queried using LLMs.

Why it's included:

- Offers flexible extraction beyond basic plaintext
- Supports multiple file types, even complex documents
- Enhances OpenWebUI’s native file handling features

In short, it’s a powerful behind-the-scenes upgrade to how OpenWebUI deals with your documents.

#### [**Edge TTS**](https://github.com/rany2/edge-tts)

This text-to-speech component provides access to Microsoft Edge's online TTS service—completely free. It greatly enhances OpenWebUI’s default voice capabilities by offering more expressive, natural-sounding options.

You can preview available voices on [this playground](https://tts.travisvn.com/) and use them by simply copying the voice name into your OpenWebUI settings.

Why it's included:

- Significantly higher-quality voice output vs the default
- Dozens of voices available across multiple languages and tones
- No subscription or API key needed—it just works

Edge TTS provides a polished, more human-like AI assistant experience with minimal setup. 
  
#### [**MCP Server**](https://modelcontextprotocol.io/introduction)

The OpenWebUI MCP server unlocks additional functionality and takes advantage of a new open protocol that standardizes how applications provide context to LLMs. In practical language, it opens up an entire world of new tools that can be used easily—without needing to understand APIs, endpoints, or schemas.

You can simply talk to your AI and:

- Get the current time (models don’t know it)
- Ask questions about your Postgres database
- Use other connected tools in natural language

This project includes two starter tools:

- **Time Tool**: Essential for any system that wants accurate responses tied to current date/time.
- **Postgres Query Tool**: Lets you explore your database by asking questions like, "What tables are available?" or "What’s in the logs table?"

Why it's included:

- Extends OpenWebUI’s capabilities with modular, plug-and-play tools
- Encourages a more conversational, assistant-like experience
- Makes AI truly useful for real-world tasks and automation

MCP turns your local LLM into a flexible, evolving assistant that can grow with your needs without code. 
  
#### [**Nginx**](https://nginx.org/)

Nginx is a high-performance, open-source web server known for its ability to handle a large number of concurrent connections efficiently. In this stack, Nginx acts as a:

- **Reverse Proxy**: It directs incoming traffic to the right services behind the scenes.
- **Load Balancer**: It ensures traffic is evenly distributed across services for better reliability.
- **Caching Layer**: It boosts performance and reduces strain on backend systems.

Why it's included:

- Professional-grade traffic management out of the box
- Flexible enough to scale with growing usage
- Well-supported and widely adopted in the industry

In short, it’s the backbone of secure, performant access to your AI stack over the web. 
  
#### [**Ollama**](https://ollama.com/)

Ollama is a groundbreaking platform that democratizes access to large language models (LLMs) by enabling users to run them locally on their machines.

A [list of models](https://ollama.com/search) is available on Ollama's website. By default, this Locker includes access to **Qwen3-0.6B**, a reasoning model known for showing its thought process in OpenWebUI. It also interacts intuitively with tools and external modules.

Why it's included:

- Local, offline access to powerful open-source LLMs
- More privacy and control compared to cloud-based models
- Easy model swapping—experiment, compare, and upgrade as needed

The model provided here is meant as a **starting point**, not a definitive answer. The world of models is vast—each with unique strengths, system requirements, and quirks when used within OpenWebUI.

We recommend:

- Researching the models that interest you
- Exploring community feedback and benchmarks
- Matching your hardware capabilities to model demands

Ollama makes your AI environment modular, private, personal, and fast—because it's running right on your machine. 
  
#### [**OpenWebUI**](https://openwebui.com/)

Open WebUI is an extensible, feature-rich, and user-friendly self-hosted AI platform designed to operate entirely offline. It’s the core interface of this stack and acts as the control center for interacting with language models and tools.

OpenWebUI offers far more than just a chat interface:

- Built-in support for local and remote LLMs
- Natural language interfaces to tools and APIs
- Document upload and summarization
- Role-based access, user management, and sessions
- Embedding and retrieval with vector stores like pgvector
- Modular plugin system and extensible UI

Why it’s included:

- It’s the visual and functional foundation of the Locker
- A fast, modern interface with constant updates and a great developer community
- Designed for local-first, privacy-respecting AI deployment

We recommend exploring their [full feature list](https://docs.openwebui.com/features/) to understand everything this platform enables. You’ll quickly see why this stack was built around it. 
  
#### [**PostgreSQL + PgVector**](https://www.postgresql.org/)

PostgreSQL is a powerful, production-grade relational database—and when combined with [PgVector](https://github.com/pgvector/pgvector), it becomes a foundation for working with embeddings and vector search inside OpenWebUI.

This stack replaces the default SQLite backend with Postgres for several reasons:

- Better performance under load
- Increased reliability and scalability
- Support for advanced features like RAG (Retrieval-Augmented Generation) and knowledge base embedding

Why it’s included:

- Enables long-term memory features within OpenWebUI
- Supports richer AI workflows like semantic search and retrieval
- Offers industry-standard data integrity and structure

As your projects grow more complex or you begin storing more documents, chat logs, and web data, this upgrade becomes essential for both speed and flexibility. 
  
#### [**Redis**](https://redis.io/)

Redis is famous for being an extremely fast in-memory data store. Its speed comes from the fact that it serves all data directly from memory, making it perfect for caching, queuing, and real-time analytics.

Why it's included:

- Boosts performance for time-sensitive operations
- Commonly used for caching AI responses or tool output
- Durable with optional disk persistence

It’s a key component in many high-performance stacks, and here it supports OpenWebUI’s backend needs for speed and reliability. You can even access its web UI at `yoursite.com/redis` to monitor and explore its behavior in real time.
  
#### [**SearxNG**](https://docs.searxng.org/)

SearxNG is a free, self-hosted metasearch engine that integrates with OpenWebUI’s web search functionality. It lets you submit queries from your own local instance to a curated set of public search engines, returning results without the typical tracking, ads, or profiling found in browser-based search.

Why it’s included:

- **Privacy-conscious**: Queries are sent from your local SearxNG instance to search engines, avoiding tracking and fingerprinting tied to your browser or identity
- **Performance**: Local querying means faster and more reliable results
- **Customization**: You can choose which engines it pulls from and how it filters results

While it powers web search inside OpenWebUI, it can also act as a standalone search engine for your browser—just point it to `yoursite.com/searxng` and enjoy a private search experience with results pulled from across the internet. 

#### [**Tika**](https://tika.apache.org/)

Apache Tika is a toolkit that detects and extracts metadata and text from over a thousand different file types, including PDFs, Word documents, spreadsheets, HTML, and more.

In this stack, Tika serves as an alternative or supplement to Docling and OpenWebUI’s default document parser.

Why it’s included:

- **Broad compatibility** with obscure or edge-case formats
- **Reliable extraction** even from poorly structured or embedded content
- **Multiple engines** provide fallback options—so one failure doesn’t block your workflow

Tika increases resilience and improves document processing accuracy, especially in environments dealing with varied or unstructured data. 
  
#### [**Watchtower**](https://github.com/containrrr/watchtower)

Watchtower is an automated Docker container updater. It monitors your running containers and checks if there are new versions of the images they’re based on. If an update is found, it will gracefully stop the old container and start the new one.

Why it's included:

- **Hands-free updates**: Keep OpenWebUI and its supporting tools fresh without manual intervention
- **Easy to configure**: Set update frequency, target containers, and send notifications
- **Production-safe**: Restarts containers one at a time to avoid downtime

Watchtower makes maintaining your stack easy and efficient—perfect for both development and long-running production setups. It comes pre-configured to send notifications to your discord.

### Setup Notes

If you don’t yet have a domain, [Cloudflare Registrar](https://www.cloudflare.com/products/registrar/) offers domains at wholesale cost (no markup). They also include DNS services for free.

If your domain is registered elsewhere (e.g., GoDaddy), you’ll need to update your nameservers. Once your domain is added to Cloudflare, they’ll show you the new nameservers to enter (e.g., `johnny.ns.cloudflare.com`, `meg.ns.cloudflare.com`). Update your registrar’s settings to point there and you're done.

