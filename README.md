# CyberSource Developer MCP

Let AI write CyberSource integration code directly in your application. This MCP server provides real-time SDK documentation and code generation assistance, enabling your AI assistant to help you integrate any CyberSource API using official SDKs.

## What is This?

This MCP (Model Context Protocol) server connects your AI assistant to live CyberSource SDK documentation. Instead of searching docs manually, your AI can:

- **Write code directly** for your CyberSource API Integrations
- **Access real-time** SDK documentation, method signatures, and models
- **Generate working code** using official CyberSource SDKs
- **Code Generation**: Supports **Java**, **Python**, **Node.js**, **PHP**, and **Ruby** (other languages coming soon)
- **MLE Support**: Helps you integrate or upgrade to Message Level Encryption (MLE) as mandated by CyberSource, with per-API MLE requirement details

Your AI assistant becomes a CyberSource integration expert that writes production-ready code in your application.

## Quick Setup

### 1. Install the Server

#### Option 1: Using pipx (Recommended - Automatic Isolation)

pipx automatically creates an isolated environment and prevents dependency conflicts:

```bash
# Install pipx (one-time setup)
pip install pipx
pipx ensurepath

# Install CyberSource Developer MCP
pipx install cybersource-developer-mcp

# Verify installation
cybersource-developer-mcp --help
```

**Why pipx?**
- ✅ Automatic environment isolation (no manual venv management)
- ✅ Zero dependency conflicts with other Python packages
- ✅ Standard approach for MCP servers
- ✅ Simple one-command installation

#### Option 2: Using uvx (Modern Alternative)

uvx allows running the server without installation:

```bash
# Install uv (one-time setup)
pip install uv

# Run directly (no installation step needed!)
uvx cybersource-developer-mcp start

# With options
uvx cybersource-developer-mcp start --data-dir /custom/path --enable-logging
```

**Why uvx?**
- ✅ No installation step required
- ✅ Automatic isolation
- ✅ Very fast execution
- ✅ Modern tooling

#### Option 3: Using pip (Not Recommended Without Virtual Environment)

If you prefer pip, create a virtual environment first to avoid conflicts:

```bash
# Create and activate virtual environment
python -m venv mcp-env
source mcp-env/bin/activate  # Windows: mcp-env\Scripts\activate

# Install the package
pip install cybersource-developer-mcp

# Verify installation
cybersource-developer-mcp --help
```

**Note:** Using pip without a virtual environment may cause dependency conflicts with other packages.

### 2. Configure Your AI Assistant

#### For Cline (VS Code Extension)

**Standard configuration** (works with pipx or pip installation):

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "timeout": 300,
      "command": "cybersource-developer-mcp",
      "args": ["start"],
      "env": {}
    }
  }
}
```

> **💡 About the timeout**: The first time you ask about a specific SDK language, the server needs to fetch and prepare the documentation, which can take a few minutes (e.g., PHP may take up to ~3 minutes). The 300-second timeout ensures this initial setup completes without interruption. After that, all responses are near-instant since everything is cached locally.

**Using uvx** (no installation needed):

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "timeout": 300,
      "command": "uvx",
      "args": ["cybersource-developer-mcp", "start"],
      "env": {}
    }
  }
}
```

**With custom data directory**:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "type": "stdio",
      "command": "cybersource-developer-mcp",
      "args": ["start", "--data-dir", "/custom/path"],
      "env": {}
    }
  }
}
```

**With logging enabled**:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "type": "stdio",
      "command": "cybersource-developer-mcp",
      "args": ["start", "--enable-logging"],
      "env": {}
    }
  }
}
```

#### For Claude Desktop

Add this to your Claude Desktop MCP configuration:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "type": "stdio",
      "command": "cybersource-developer-mcp",
      "args": ["start"],
      "env": {}
    }
  }
}
```

### 3. Start Using It

That's it! Your AI assistant can now help you with CyberSource integrations. Just ask questions like:

- "Show me how to create a payment using the CyberSource Java SDK"
- "What parameters does the PaymentsApi accept?"
- "Help me set up authentication for CyberSource"
- "Generate a payment capture example in Python"

## What Can It Do?

### 🔍 SDK API Documentation
Get complete documentation in SDK for any CyberSource API class with method signatures, parameters, and examples.

**Example**: Ask "What methods are available in PaymentsApi?"

### 📦 Model Details
Understand request and response models with property definitions and data types.

**Example**: Ask "What fields does PaymentRequest need?"

### 📋 API Discovery
Browse all available CyberSource APIs with endpoint mappings and descriptions.

**Example**: Ask "What APIs are available for payment processing?"

### 📖 Setup Guides
Access SDK installation, authentication, and configuration documentation.

**Example**: Ask "How do I set up CyberSource authentication in Java?"

### 🔐 MLE (Message Level Encryption) Support
Identify which APIs require or support MLE as mandated by CyberSource. Get guidance on integrating or upgrading your existing code to meet MLE requirements using the CyberSource SDK, including per-API MLE configuration details.

**Example**: Ask "Which APIs require MLE?" or "Help me enable MLE for the Payments API"

### 💻 Code Templates
Get code structure templates for common integration patterns.

**Example**: Ask "Show me a basic payment integration template"

## Configuration Options

### Custom Data Directory

By default, SDKs are downloaded to `~/.cybersource_developer_mcp/`. To use a different location:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "command": "cybersource-developer-mcp",
      "args": ["start", "--data-dir", "/your/custom/path"]
    }
  }
}
```

### Enable Logging

To enable detailed logging for troubleshooting:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "command": "cybersource-developer-mcp",
      "args": ["start", "--enable-logging"]
    }
  }
}
```

Logs will be saved to `~/.cybersource_developer_mcp/logs/mcp_server.log`

### GitHub Token (Optional)

For faster SDK downloads and higher API rate limits, add a GitHub token:

```json
{
  "mcpServers": {
    "cybersource-developer-mcp": {
      "command": "cybersource-developer-mcp",
      "args": ["start"],
      "env": {
        "GITHUB_TOKEN": "your_github_token_here"
      }
    }
  }
}
```

## How It Works

1. **First Time**: When you ask about a CyberSource API, the server automatically downloads the SDK documentation
2. **Cached**: Subsequent requests are instant - no re-downloading needed
3. **Always Current**: The server can check for and use the latest SDK versions
4. **Multi-Language**: Works with Java, Python, PHP, Node.js, and Ruby (.NET and .NET Standard coming soon)

## Requirements

- **Python 3.10 or higher**
- **Internet connection** (for initial SDK downloads)
- **Windows Users**: Enable long path support (see [Windows Long Path Fix](#windows-long-path-errors) below)

## Troubleshooting

### Server Won't Start

1. Check Python version: `python --version` (must be 3.10+)
2. Reinstall based on your installation method:
   - **pipx**: `pipx reinstall cybersource-developer-mcp`
   - **pip**: `pip install --upgrade cybersource-developer-mcp`
   - **uvx**: Just rerun `uvx cybersource-developer-mcp start`
3. Check logs: `~/.cybersource_developer_mcp/logs/mcp_server.log` (if logging enabled)

### AI Assistant Can't Find APIs

1. Ensure the server is running in your MCP configuration
2. Restart your AI assistant after adding the configuration
3. Try asking "List available CyberSource APIs for latest version"

### SDK Download Issues

1. Check internet connection
2. Verify GitHub is accessible
3. Add a GitHub token (see Configuration Options above)
4. Check disk space in `~/.cybersource_developer_mcp/`

### Windows Long Path Errors

Windows has a 260-character path limit by default. Enable long path support:

1. Open Registry Editor (regedit)
2. Navigate to: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem`
3. Set `LongPathsEnabled` to `1`
4. Restart your computer

Or run in an elevated PowerShell: `New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force`

### Corporate Network Issues

If you're behind a corporate proxy or firewall:

```bash
# Set custom CA bundle
export REQUESTS_CA_BUNDLE=/path/to/corporate/ca-bundle.crt
```

Then add this to your MCP configuration:
```json
{
  "env": {
    "REQUESTS_CA_BUNDLE": "/path/to/corporate/ca-bundle.crt"
  }
}
```

## Example Conversations

Here are some ways to use this with your AI assistant:

**Basic Payment Integration**
> "I need to create a payment using CyberSource Java SDK. Show me how."

**Understanding APIs**
> "What's the difference between PaymentsApi and CaptureApi?"

**Model Details**
> "What fields are required in the PaymentRequest model?"

**Authentication Setup**
> "How do I configure HTTP Signature authentication for CyberSource?"

**Multi-Step Integration**
> "Help me build a complete payment flow with authorization and capture in Python."

**Version-Specific Help**
> "Show me the PaymentsApi documentation for version 0.0.82"

**MLE Integration**
> "Which CyberSource APIs require MLE and how do I enable it in my SDK configuration?"

**MLE Upgrade**
> "Help me upgrade my existing payment integration to support MLE as required by CyberSource."

## Data Storage

The server stores data in `~/.cybersource_developer_mcp/` by default:

```
~/.cybersource_developer_mcp/
├── cybs-sdk-github-code/          # Downloaded SDK documentation
├── pre-processed-json/            # Cached Details
└── logs/                          # Server logs (if enabled)
```

You can safely delete this directory to start fresh. The server will re-download what it needs.

## Supported SDK Languages

| Language | SDK Documentation | Code Generation | Latest Version Auto-Detection |
|----------|---------------|-----------------|------------------------------|
| Java | ✅ Full Support | ✅ Available | Yes |
| Python | ✅ Full Support | ✅ Available | Yes |
| PHP | ✅ Full Support | ✅ Available | Yes |
| Node.js | ✅ Full Support | ✅ Available | Yes |
| Ruby | ✅ Full Support | ✅ Available | Yes |
| .NET | 🚧 Coming Soon | 🚧 Coming Soon | Yes |
| .NET Standard | 🚧 Coming Soon | 🚧 Coming Soon | Yes |

**Note**: SDK documentation and code generation templates are available for Java, Python, Node.js, PHP, and Ruby. Support for .NET and .NET Standard is coming soon.

## Privacy & Security

- **No Data Sent**: Your code and conversations stay between you and your AI assistant
- **Local Storage**: All SDKs and documentation are stored locally on your machine
- **GitHub Access**: Only downloads public CyberSource SDK repositories
- **Optional Token**: GitHub token is only needed for higher download limits

## Need Help?

- **Issues**: Report problems on [GitHub Issues](https://github.com/CyberSource/cybersource-developer-mcp/issues)
- **Updates**: Check [CHANGELOG.md](https://github.com/CyberSource/cybersource-developer-mcp/blob/master/CHANGELOG.md) for version history

## Links

- **MCP Documentation**: https://modelcontextprotocol.io
- **CyberSource Developer Center**: https://developer.cybersource.com
- **GitHub Repository**: https://github.com/CyberSource/cybersource-developer-mcp
---

**Note**: This MCP server provides SDK documentation and code assistance. For production implementations, always refer to official CyberSource documentation and follow security best practices.

## AI-Generated Code Disclaimer

**Important**: This tool uses AI to assist with code generation and documentation. Please note:

- **No Liability**: CyberSource is not liable for any code generated by AI assistants using this MCP server
- **Verification Required**: You must thoroughly review, test, and validate all AI-generated code before use
- **Your Responsibility**: It is your responsibility to ensure generated code meets your security, compliance, and business requirements
- **Testing Mandatory**: All code must be tested in non-production environments before deployment to production
- **Security Review**: Conduct proper security reviews and follow your organization's code review processes
- **No Warranty**: The generated code is provided "as-is" without any warranties or guarantees of correctness, security, or fitness for any purpose

**Best Practices**:
- Always review generated code line-by-line
- Test thoroughly in development and staging environments
- Follow your organization's security and compliance guidelines
- Keep credentials and sensitive data secure (never expose API keys in code)
- Consult official CyberSource documentation for authoritative guidance
- Engage with CyberSource support for production-critical implementations

By using this tool, you acknowledge that you are solely responsible for any code deployed to production systems.
