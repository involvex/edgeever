<div align="center">
  <h1>
    <img src="assets/brand/edgeever-icon.svg" alt="EdgeEver Logo" width="40" align="absmiddle" /> EdgeEver
  </h1>
  <p>
    <b>Open-source, AI-native self-hosted knowledge base and Evernote alternative</b>
  </p>
  <p>
    <a href="https://github.com/tianma-if/edgeever/stargazers"><img src="https://img.shields.io/github/stars/tianma-if/edgeever?style=social" alt="GitHub Stars" /></a>
    <a href="https://github.com/tianma-if/edgeever/network/members"><img src="https://img.shields.io/github/forks/tianma-if/edgeever?style=social" alt="GitHub Forks" /></a>
    <a href="https://github.com/tianma-if/edgeever/pkgs/container/edgeever"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fghcr-badge.elias.eu.org%2Fapi%2Ftianma-if%2Fedgeever%2Fedgeever&query=downloadCount&style=social&logo=docker&label=Docker%20Pulls" alt="Docker Pulls" /></a>
    <a href="https://www.producthunt.com/products/edgeever?utm_source=other&utm_medium=social"><img src="https://img.shields.io/badge/Product%20Hunt-ea532a?style=social&logo=product-hunt" alt="Product Hunt" /></a>
    <a href="https://afdian.com/a/tianma-if"><img src="https://img.shields.io/badge/Support%20Us-946ce6?style=social&logo=github-sponsors" alt="Support" /></a>
  </p>
  <p>
    <b>English</b> | <a href="README.zh-TW.md">Traditional Chinese</a> | <a href="README.md">Original</a> | <a href="README.ja.md">Japanese</a>
  </p>
  <p>
    <a href="https://t.me/+wwUx1BYLrIdiZjY1">💬 Telegram Group</a> &nbsp;|&nbsp;
    <a href="https://demo.edgeever.org">🌐 Live Demo</a> &nbsp;|&nbsp;
    <a href="#client-downloads">📱 Client Downloads</a>
  </p>
</div>

EdgeEver is a modern, open-source notes and knowledge base workspace. It revives the beloved Evernote-style three-pane layout while offering an open data architecture and seamless AI Agent integration for complete ownership and smart productivity.

> 💡 **Serverless & 100% Free Forever**
> EdgeEver can run within Cloudflare's free quotas with no server purchase or VPS maintenance. Users who prefer a VPS, NAS, or home server can deploy the same application with Docker.

> ⭐ If EdgeEver is useful to you, consider giving it a Star. Your support helps more people discover the project.

## Why EdgeEver

Many long-time **Evernote** users simply want a **reliable, open, and fast** personal knowledge base. However, existing mainstream solutions all present tradeoffs:

* **Evernote**: It has grown increasingly bloated with commercial ads and unnecessary features, degrading performance. Data export is cumbersome, free tiers are heavily restricted, and AI/MCP features require costly subscriptions.
* **Obsidian**: Open files, closed-source core. Official Sync is paid and third-party sync is tedious; relying entirely on flat local file scanning causes noticeable cold-start and search lag once notes reach thousands or heavy plugins are loaded; storing images and attachments alongside notes quickly bloats vaults, making mobile sync sluggish and leaving orphaned files behind; and it is overly heavy for lightweight, capture-anywhere use.
* **Memos & Stream Notes**: Clean and simple, but their social-timeline layouts differ fundamentally from the structured productivity of a classic three-pane workflow.
* **SiYuan & Block-based PKMs**: Powerful with self-hosting support, but their granular "block-level" architecture imposes noticeable cognitive overhead for quick daily capture and continuous prose writing. Furthermore, they lack a true zero-cost serverless deployment tier, and multi-device sync relies on paid official subscriptions or paying extra to unlock S3/WebDAV sync features with your own storage.

**EdgeEver fills this gap**: The entire stack is open source, including sync and self-hosting. It keeps the three-pane layout you know, stays silky-smooth and lightweight even with 10,000+ notes, and ships native AI agents with zero-cost deployment.

> 💡 **Recommended Workflow:**
> Capture inspiration seamlessly across all devices and organize deeply in the classic three-pane view. Powered by native MCP, it not only lets AI agents retrieve and synthesize your knowledge, but also connects with your favorite productivity tools like Notion and Feishu. Publish anywhere with one-click formatting—100% self-hosted at zero cost, building an open and truly owned second brain.

## Online Demo

- Demo: [https://demo.edgeever.org](https://demo.edgeever.org)

The public demo resets every day at 3:00 AM (UTC+8) and restores sample notes. Do not store private content there.

## Client Downloads

<p>
  <a href="https://github.com/tianma-if/edgeever/releases/latest"><img src="assets/readme/platforms/macos.svg" alt="Download EdgeEver for macOS" width="40" height="40" /></a>&nbsp;&nbsp;
  <a href="https://github.com/tianma-if/edgeever/releases/latest"><img src="assets/readme/platforms/windows.svg" alt="Download EdgeEver for Windows" width="40" height="40" /></a>&nbsp;&nbsp;
  <a href="https://github.com/tianma-if/edgeever/releases/latest"><img src="assets/readme/platforms/tux.svg" alt="Download the EdgeEver Linux x86_64 AppImage Preview" width="40" height="40" /></a>&nbsp;&nbsp;
  <a href="https://play.google.com/store/apps/details?id=org.edgeever.mobile"><img src="assets/readme/platforms/google-play.svg" alt="Download EdgeEver for Android from Google Play" width="40" height="40" /></a>&nbsp;&nbsp;
  <a href="https://apps.apple.com/us/app/edgeever/id6792625631"><img src="assets/readme/platforms/app-store.svg" alt="Download EdgeEver for iOS from the App Store" width="40" height="40" /></a>
</p>

> The iOS app requires an Apple ID from outside mainland China.

## Features

- **Deploy Your Way**: Run on Cloudflare's free serverless platform or with Docker on a VPS, NAS, or home server. Based on Cloudflare's free storage allowances, a personal deployment can hold roughly 150,000 short notes and 50,000 images; Docker storage scales on demand to easily support millions of notes and a vast image library.
- **Open Data, No Vendor Lock-in**: Built on standard SQLite with complete REST API, MCP, and CLI access. Your knowledge is stored transparently and accessible anytime without being locked to a single app.
- **Lossless ZIP Backup & Portability**: Export your complete library as a clean archive containing Markdown, Front Matter, nested folders, relative attachment links, and version histories for instant restoration anywhere.
- **Native AI Agent Synergy**: Deep integration with Model Context Protocol (MCP) allows AI Agents like Claude Code, Codex, Antigravity, and WorkBuddy to read, organize, and summarize your notes, or sync seamlessly with Notion and Feishu Bitable.
- **Bring Your Own AI Models**: Connect OpenAI, Anthropic, or Gemini-compatible services and third-party API relays to empower your editor with smart note summarization, key point extraction, proofreading, translation, and text continuation on full notes or selected text.
- **Rich Plugin API**: Extend EdgeEver with the [Plugin API](docs/plugin-development.md).
- **Unlimited Multi-Device Sync**: No commercial device caps or paywalls. Enjoy seamless synchronization across PC, tablet, and mobile via web, PWA, or browser.
- **Classic Three-Pane Layout & Focus Mode**: Clean navigation featuring notebook trees, note lists, and an expansive editor, with a desktop focus mode to eliminate distractions.
- **Light, Lasting Desktop Performance**: Switching notes does not keep old images and documents in memory, and the desktop app stays responsive after sitting in the background.
- **Unlimited Nested Notebooks**: Organize your knowledge with arbitrary folder depth.
- **One-Click Rich Copy for Newsletters & Blogs**: Designed for creators to convert notes into beautifully formatted rich text with inline CSS, ready to paste directly into Substack, Medium, WordPress, or newsletter editors without extra tools.
- **Seamless Dual-View Editor**: Switch effortlessly between intuitive rich text editing and Markdown source code on desktop.
- **Convenient Single-Note Export**: Export the current note directly as Markdown, HTML, or PDF for standalone storage, sharing, or publishing.
- **Native Mermaid Diagram Rendering**: Render clear flowcharts, sequence diagrams, and mind maps directly in notes, preserving clean, editable source code across Markdown and rich text views.
- **Visual Diagram Notes**: Ditch external drawing tools and sketch mind maps, flowcharts, and architecture diagrams directly in notes. Backed by a structured IR, the built-in assistant and external AI agents can generate and refine diagrams from a single prompt, complete with smart auto-layout, cross-device sync, and vector export. See the [visual diagram notes design](docs/visual-diagram-notes.md).
- **Revision History**: Inspect and restore previous iterations of your notes with built-in version tracking.
- **Public Note Sharing**: Share a note publicly and stop sharing it at any time. Optionally protect the link with an auto-generated access password.
- **Seamless Content Capture**: Capture articles, web content, and media from your browser across all platforms.
- **Smart Local Image Compression**: Client-side WebP compression reduces file sizes by 50%-90% before uploading, saving storage and speeding up page loads without extra server costs.
- **Universal File Attachments**: Attach and preview PDFs, Office documents, zip files, audio, and video directly within notes. Chunked uploads and streaming safely support files up to 1 GiB.
- **Batch Operations & Flexible Sorting**: Easily merge or relocate multiple notes, with drag-and-drop notebook reordering.
- **Offline Drafts & Queueing**: Draft and edit uninterrupted while offline; changes automatically sync once reconnected.
- **Brute-Force Login Protection**: Server-side account- and IP-based failed-login throttling with automatic cooldowns helps protect private notes against brute-force and password-spraying attacks.
- **Multi-Tenant Account Isolation**: Host multiple user accounts on a single instance with strictly partitioned spaces and clean admin account management.
- **Everywhere You Need It**: Available on the Web, Android, macOS, Windows, Linux, and iOS; with web clipper support for Chrome, Edge, and Firefox.

## Deployment

Cloudflare is the recommended zero-server deployment. Docker is available for users who prefer a VPS, NAS, or home server.

For Cloudflare, choose either of the following online deployment options:

### Option A: Deploy with an AI Agent (Recommended)

Copy the prompt below directly into an AI Agent (such as Codex, Claude, Cursor, WorkBuddy, Antigravity, OpenClaw, Hermes Agent, etc.). During execution, if access to GitHub or Cloudflare is required, review the requested permissions and follow the prompts to authorize access.

```text
Deploy EdgeEver entirely through GitHub and Cloudflare:
1. Fork https://github.com/tianma-if/edgeever.
2. Create D1 database named `edgeever` and R2 bucket named `edgeever-resources` in Cloudflare.
3. In Workers & Pages, create a Worker named `edgeever` from the Fork's `main` branch.
   Use the repository root, keep Cloudflare's default Workers Builds deploy command,
   and ensure its API token can read and edit D1. Select Save and Deploy.
4. After the Worker is created, add the user's chosen password as the runtime Secret
   `EDGE_EVER_AUTH_PASSWORD` (preferably at least 32 characters).
   The username defaults to `admin`.
   If the user specifies another, set `EDGE_EVER_AUTH_USERNAME` as a Workers Builds
   variable before the next build.
5. Run the build again, verify `/api/health` and `/api/openapi.json`, then log in
   with that administrator username and password.
6. Enable and manually run the GitHub Actions workflow named `Update deployed EdgeEver`
   once so the Fork can automatically receive future stable releases and fixes.
```

### Option B: Manual Online Deployment

Complete setup in 6 web steps:

1. **Fork the Repository**: Click **Fork** at the top right of GitHub to fork EdgeEver into your personal account.
2. **Create Cloudflare Resources**: Create D1 database `edgeever` and R2 bucket `edgeever-resources`.
3. **Import & Configure the Project**: Create a Worker named `edgeever` from the Fork's `main` branch in Cloudflare **Workers & Pages**. Use the repository root and keep Cloudflare's default Workers Builds deploy command. Ensure its API token can read and edit D1.
4. **Choose the Administrator Password**: Choose an administrator password, preferably at least 32 characters. Once the Worker is created, save it as the runtime Secret `EDGE_EVER_AUTH_PASSWORD`.
5. **Build & Verify**: Save and Deploy creates the Worker and starts a build. If it fails due to missing administrator Secret, add it from step 4 and retry. Once deployed, confirm `/api/health` returns `200`, then log in with your username and password.
6. **Enable Automatic Updates**: Open the Fork's **Actions** tab, click **I understand my workflows, go ahead and enable them**, then manually run **Update deployed EdgeEver** once to enable automatic future updates.

### Option C: Docker on a VPS or NAS

Use the GitHub-hosted installer and the official GHCR image:

```sh
curl -fsSL https://edgeever.org/install.sh | bash
```

The command pulls the latest image, generates an administrator password, starts EdgeEver with Docker Compose, and schedules daily automatic updates.

See [DOCKER_STORAGE_GUIDE.md](DOCKER_STORAGE_GUIDE.md) for persistent storage configuration and [deploy-docker.md](docs/deploy-docker.md) for manual deployment options.

---

## Multi-Account Login

Once deployed, a single instance supports multi-account login.

The instance administrator can create, disable, or reset member accounts in **Profile** -> **User accounts**. Each member gets a fully isolated personal workspace, including notebooks, notes, attachments, Trash, import/export, and MCP tokens.

## Browser Web Clipper

The Web Clipper is officially published for Chrome, Microsoft Edge, and Firefox. Install it from the store for your browser:

<p>
  <a href="https://chromewebstore.google.com/detail/edgeever-web-clipper/gjadpfmanienmlofajibkfkkpfdkclgo"><img src="https://raw.githubusercontent.com/alrra/browser-logos/58881b84c4d73adc03c06fa2c275a7abee02d935/src/chrome/chrome.svg" alt="Install EdgeEver Web Clipper for Google Chrome" width="36" height="36" /></a>&nbsp;&nbsp;
  <a href="https://chromewebstore.google.com/detail/edgeever-web-clipper/gjadpfmanienmlofajibkfkkpfdkclgo"><img src="https://raw.githubusercontent.com/alrra/browser-logos/58881b84c4d73adc03c06fa2c275a7abee02d935/src/edge/edge.svg" alt="Install EdgeEver Web Clipper for Microsoft Edge" width="36" height="36" /></a>&nbsp;&nbsp;
  <a href="https://addons.mozilla.org/firefox/addon/edgeever-web-clipper/"><img src="https://raw.githubusercontent.com/alrra/browser-logos/58881b84c4d73adc03c06fa2c275a7abee02d935/src/firefox/firefox.svg" alt="Install EdgeEver Web Clipper for Firefox" width="36" height="36" /></a>
</p>

## Community and Feedback

- Bugs, feature requests, and deployment issues: [GitHub Issues](https://github.com/tianma-if/edgeever/issues)
- Code contributions: read the [Contribution Guide](CONTRIBUTING.md).

### Telegram Community

Welcome to the EdgeEver community. Join us to discuss the EdgeEver experience, real-world AI Agent applications, cost-effective or free AI resources, and automation workflows.

👉 [Join the EdgeEver Telegram group](https://t.me/+wwUx1BYLrIdiZjY1)

## Plugins and Themes

Web and desktop apps support functional plugins and custom themes, installable from the official marketplace, GitHub, or a Manifest URL, with seamless sync across your workspace. Developers can extend capabilities using `@edgeever/plugin-api`; see the [plugin development guide](docs/plugin-development.md).

## Tech Stack

- Bun workspace monorepo with Web, API, official site, and shared type package.
- Frontend: Vite, React, React Router, TanStack Query, Tailwind CSS, shadcn/ui, and Radix UI.
- Editor: TipTap / ProseMirror with Markdown support; PWA uses vite-plugin-pwa, Workbox, and Dexie.
- Android app: Expo + React Native with SQLite local storage and incremental sync.
- iOS app: Native SwiftUI (iOS 17+) with TipTap EditorBundle, GRDB local mirror/outbox.
- Native desktop app: Electron + Rust sidecar with consistent cross-platform experience and high-performance local data services.
- Web clipper: Manifest V3, Mozilla Readability, and Turndown for Chrome, Edge, and Firefox.
- Backend: Hono/Zod business application with REST API and Remote MCP; Cloudflare uses Workers/D1/R2, while Docker uses Bun/SQLite/local files or S3.
- Official site: Astro static site, deployable to Cloudflare Pages.

## Quick Start

```sh
bun install
bun run dev
```

Local development signs in automatically; fresh databases use `owner` / `edgeever-local-dev`. Log out to test the login screen.

## Project Structure

```text
apps/web          Vite + React frontend, PWA, offline drafts, and sync queue
apps/extension    Chrome/Edge/Firefox Manifest V3 web clipper
apps/api          Cloudflare Worker + Hono API, MCP endpoint
apps/mobile       Expo + React Native Android app
apps/ios          Native SwiftUI iOS app
apps/desktop      Electron desktop shell, preload bridge, and native packaging
apps/site         Astro official website
packages/client   Shared API client for web and mobile apps
packages/shared   Shared types, Zod schemas, TipTap / Markdown conversion
crates/desktop-sidecar
                   Rust sidecar for local SQLite, offline data, and backups
scripts           Wrangler wrapper, password hash, CLI, MCP stdio bridge
migrations        Shared append-only database migrations
docs              Architecture, migration, and deployment docs
.github/workflows CI for web, mobile, iOS, desktop packaging, and deployment
wrangler.toml     Cloudflare Workers, Assets, D1, R2 configuration
```

## Content Formats

EdgeEver stores note content in three forms:

```text
content_json      TipTap/ProseMirror document, the editor source of truth
content_markdown  API, Agent, import, and export format
content_text      Search, summary, and indexing text
```

Open **Profile** -> **Import and export** to export or import an EdgeEver ZIP archive. Its `notes/` directory is directly readable and portable as Markdown.

## MCP (Model Context Protocol)

Create an API token in **Profile** -> **MCP settings** and give it to your AI Agent. The Agent can then securely manage your knowledge base within your account permissions. It supports both text notes and diagram notes with full CRUD capabilities, note templates, AI instructions, and connections with tools such as Notion databases and Feishu Bitable.

## Image Compression

Image compression happens in the Web client before upload. When enabled, PNG, JPEG, WebP, and AVIF files are converted to WebP when beneficial, with the longest edge limited to `2560px`.

EdgeEver avoids Worker-side image processing to reduce compute usage. REST API and MCP upload paths store file content without additional server-side compression.

## Advanced Object Storage

The instance owner can configure S3-compatible object storage under **Settings → Advanced → OSS object storage**.

## Migration

Migrate notes from other platforms to EdgeEver:

- **Evernote Migration**: See [docs/evernote-migration-guide.md](docs/evernote-migration-guide.md)
- **flomo Migration**: See [docs/flomo-migration-guide.md](docs/flomo-migration-guide.md)
- **Memos Migration**: See [docs/memos-migration-guide.md](docs/memos-migration-guide.md)
- **Notion Migration**: See [docs/notion-migration-guide.md](docs/notion-migration-guide.md)

## Docker Deployment

Docker runs the same frontend, API routes, services, authentication, MCP implementation, and migrations as Cloudflare. The container uses SQLite with local files or S3-compatible attachment storage. See [Deploy EdgeEver with Docker](docs/deploy-docker.md) and [Self-hosting and Docker architecture](docs/self-hosting-architecture.md). For persistent storage setup, see [DOCKER_STORAGE_GUIDE.md](DOCKER_STORAGE_GUIDE.md).

## Acknowledgements

- EdgeEver's note-taking product design was informed by Evernote.
- Mind-map and visual-diagram notes design was informed by XMind and ProcessOn.
- Editor theme typography draws from obsidian-minimal, Outline, and other public works.

## Trademark and Brand Use

The EdgeEver name, logo, and other brand identifiers distinguish the official project. Forks and modified versions may state that they are based on EdgeEver, but must not imply official status. The open-source license does not grant trademark rights.

## Disclaimer

EdgeEver is an independent open-source note-taking application. It is not affiliated with, authorized, sponsored, or endorsed by Evernote Corporation.

EdgeEver is self-hosted software. Except for official demo instances, project maintainers do not host, control, or review user content.
