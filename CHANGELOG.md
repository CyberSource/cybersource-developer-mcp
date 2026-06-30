# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.0.2]

### Added
- .NET (C#) language support — generate CyberSource SDKs in C#, with smart auto-detection
- JWT Shared Secret (JWT with symmetric) authentication — supported in code generation across all languages
- PyPI badges added to README

### Security
- Fixed GitHub PAT credential leak in error logs
- Additional security hardening

## [0.0.1]

### Added
- Initial release of CyberSource Developer MCP Server
- AI-powered code generation for CyberSource API integrations using official SDKs
- Code generation support for Java, Python, Node.js, PHP, and Ruby
- Real-time SDK documentation access including API class details, method signatures, parameters, and return types
- Request and response model documentation with property definitions and data types
- API discovery to browse all available CyberSource APIs with endpoint mappings and descriptions
- MLE (Message Level Encryption) configuration support in SDK — identify which APIs require or support request/response MLE, with per-API MLE capability details
- SDK setup and authentication guides (HTTP Signature, JWT, etc.)
- Code structure templates for common CyberSource integration patterns

### MCP Tools
- `get_api_class_details` — Retrieve API class documentation
- `get_model_class_details` — Retrieve model class documentation
- `list_available_apis` — List all available API classes
- `get_sdk_overview` — Get SDK setup and configuration guide
- `get_code_template` — Get code structure templates

### Infrastructure
- Automatic latest SDK version resolution with version-specific documentation
- Intelligent local caching for SDK downloads — first request fetches, subsequent requests are instant
- Multiple installation methods: pipx (recommended), uvx, and pip
- Configurable data directory for SDK storage (`--data-dir`)
- Optional logging for troubleshooting (`--enable-logging`)
- Optional GitHub token support for faster SDK downloads and higher API rate limits
- Cross-platform support including Windows long path handling
- Corporate network/proxy support via custom CA bundle configuration
- Compatible with Cline (VS Code), Claude Desktop, and other MCP-compatible AI assistants
- Privacy-first design — all data stored locally, no code or conversations sent externally

[0.0.2]: https://github.com/cybersource/cybersource-developer-mcp/releases/tag/v0.0.2
[0.0.1]: https://github.com/cybersource/cybersource-developer-mcp/releases/tag/v0.0.1
