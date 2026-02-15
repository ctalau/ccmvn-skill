# ccmvn-skill

A Claude Code skill for running Maven builds using the `ccmvn` tool, which provides Maven proxy support for sandboxed environments.

## Installation

Install this skill in Claude Code:

```bash
npx skills add ccmvn-skill
```

Or install globally:

```bash
npm install -g ccmvn-skill
```

## Usage

Once installed, use the skill in Claude Code with:

```bash
/ccmvn clean install
/ccmvn package
/ccmvn test
```

Or directly:

```bash
npx ccmvn clean install
```

## What This Skill Does

This skill provides Claude Code with knowledge about:

- How to run Maven builds using the `ccmvn` proxy tool
- Maven command syntax and common goals
- Troubleshooting Maven builds in sandboxed environments
- How the three-layer proxy architecture works
- Best practices for building Java projects with Maven

## How ccmvn Works

The `ccmvn` tool creates a three-layer proxy chain to enable Maven to access Maven Central in restricted sandbox environments:

```
Maven → Local Proxy → Upstream Sandbox Proxy → Maven Central
       (HTTP)        (HTTP CONNECT)         (HTTP/2 over TLS)
```

This architecture allows Maven to work when:
- Outbound HTTPS is blocked
- DNS resolution is unavailable
- The environment requires JWT authentication

## Prerequisites

- Maven 3.x installed on the system
- Node.js (for the proxy server)
- The `ccmvn` npm package: `npm install -g ccmvn`
- (In sandboxed environments) Proper `HTTPS_PROXY` environment variable configuration

## Related Projects

- [ccmvn](https://github.com/ctalau/ccmvn) - The Maven proxy tool this skill documents
- [Claude Code](https://code.claude.com) - The IDE this skill is designed for

## License

MIT
