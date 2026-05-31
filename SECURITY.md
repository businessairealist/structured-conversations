# Security Policy

## Security Posture

This plugin operates as a set of Claude skills — it contains no executable code, no MCP server connections, and no hook automation. All functionality is delivered through markdown instruction files (SKILL.md) and reference documents.

## Security Properties

### No Hardcoded Secrets
- The plugin contains no API keys, tokens, passwords, or credentials
- No environment variables are required or consumed
- No authentication is performed by any component

### Input Handling
- The plugin has no hooks, so no automated input interception occurs
- All user input is processed by Claude's standard conversation handler
- Skills provide instructions for Claude to follow — they do not execute code directly

### No Blind Tool Passthrough
- The plugin defines no MCP servers or tool configurations
- No external services are called
- No data leaves the user's local environment through plugin mechanisms

### No Executable Code
- The plugin contains only markdown (.md) and JSON (.json) files
- No scripts, binaries, or executable content is included
- All workflow logic is expressed as natural-language instructions for Claude

## Reporting

If you discover a security concern with this plugin, contact the plugin author.
