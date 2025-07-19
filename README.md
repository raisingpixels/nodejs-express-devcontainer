# Node.js Express Parent Developer Devcontainer

A complete VSCode devcontainer setup optimized for Node.js and Express API development by parent developers who code in fragmented time. Build backends safely with AI assistance while protecting your host system from security incidents.

## Quick Start

1. **Clone this repository** into your Node.js project as `.devcontainer/`
2. **Update your details** in `devcontainer.json` (replace email and name in `postCreateCommand`)
3. **Open in VSCode** and select "Reopen in Container" when prompted
4. **Start building APIs** - everything is pre-configured!

## What This Solves

**API Development Made Simple**: No more wrestling with Node versions, global packages, or database connections. Everything works consistently across machines.

**Security Isolation**: Build APIs with AI assistance without exposing your SSH keys, other projects, or host system to malicious packages or security vulnerabilities.

**Backend-Optimized Workflow**: Tools specifically chosen for Express development, API testing, and database integration.

## What's Included

### 🤖 AI Assistants (Your Backend Superpowers)
- **Claude Code** - Perfect for understanding API architecture and debugging complex backend logic
- **GitHub Copilot** - Smart completions for Express routes, middleware, and database queries
- **Copilot Chat** - Ask questions about best practices, debugging, and optimization

### 🚀 Node.js & Express Development
- **TypeScript support** with intelligent imports and error checking
- **Nodemon** for automatic server restarts during development
- **NPM script integration** with visual script explorer
- **Smart file nesting** for package files, environment configs, and Docker setups
- **Auto-formatting** with Prettier and ESLint for consistent code

### 🔧 API Development Tools
- **REST Client** - Test your APIs directly in VSCode without external tools
- **Thunder Client** - Visual API testing with collections and environments
- **OpenAPI/Swagger** - API documentation and schema validation
- **JSON schema validation** for package.json and configuration files

### 🗄️ Database Integration Ready
- **SQL Tools** - Connect to PostgreSQL, MySQL, SQLite databases
- **MongoDB support** - Extensions for NoSQL development
- **Port forwarding** - PostgreSQL (5432), MongoDB (27017) ready to connect
- **Database query tools** built into VSCode

### 👨‍👩‍👧‍👦 Parent Developer Optimizations
- **Auto-save after 1 second** - never lose work when interrupted
- **Smart git commits** - stage and commit in one action
- **Auto dark mode** - switches between "Quiet Light" and "Monokai Dimmed"
- **Enhanced terminal** - persistent command history and beautiful fonts
- **Container isolation** - experiments can't break your host system

## Supported Development

Perfect for building:
- **REST APIs** with Express.js
- **GraphQL services** with Apollo Server
- **Microservices** and serverless functions
- **Database-driven applications** (SQL and NoSQL)
- **Real-time APIs** with WebSockets
- **Authentication services** with JWT/OAuth

## Daily Workflow

### Starting Development
```bash
# Container automatically installs dependencies
npm run dev     # Start development server with nodemon
npm run build   # Build TypeScript to JavaScript
npm test        # Run your test suite
```

## Project Setup Examples

### Express + TypeScript API
```bash
# Initialize new project
npm init -y
npm install express cors helmet morgan
npm install -D @types/express @types/cors typescript nodemon

# Create basic structure
mkdir src
touch src/app.ts src/server.ts
```

### Express + SQLite
```bash
npm install sqlite3 better-sqlite3
npm install -D @types/better-sqlite3
```

### Express + PostgreSQL
```bash
npm install pg
npm install -D @types/pg

# Use Docker Compose for local PostgreSQL
```

## Security Benefits

### What This Container Protects You From
- **Malicious npm packages** that could steal credentials or access files
- **AI-suggested commands** that might be dangerous to your host system
- **Database connection strings** accidentally committed to other projects
- **Environment variable leakage** across different APIs

### How Container Isolation Works
- **Package isolation** - npm packages can't access your host file system
- **Database isolation** - development databases run in containers
- **Credential isolation** - API keys and tokens stay project-specific
- **Network isolation** - services can't connect to unintended local resources

### Safe AI Development
This setup lets you:
- ✅ Ask AI to generate database schemas and migration scripts
- ✅ Experiment with new npm packages without host system risk
- ✅ Try AI-suggested optimization techniques safely
- ✅ Test external API integrations without credential exposure

## Customization

### Adding Database Support
For **PostgreSQL** with Docker Compose:
```yaml
# docker-compose.yml
version: '3.8'
services:
  postgres:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: development
    ports:
      - "5432:5432"
```

For **MongoDB**:
```yaml
# docker-compose.yml
version: '3.8'
services:
  mongodb:
    image: mongo:7
    ports:
      - "27017:27017"
```

### Custom Bash Aliases
Create `.devcontainer/bashrc`:
```bash
# API development shortcuts
alias logs="npm run logs"
alias migrate="npm run db:migrate"
alias seed="npm run db:seed"
alias resetdb="npm run db:reset"

# Testing shortcuts
alias test:unit="npm run test:unit"
alias test:api="npm run test:integration"
alias test:coverage="npm run test -- --coverage"
```

Then add this line to the container mounts:

```json
"source=${localWorkspaceFolder}/.devcontainer/bashrc,target=/home/node/.bashrc,type=bind"
```


### Project-Specific Extensions
Add to the `extensions` array for your needs:

```json
// For GraphQL development
"graphql.vscode-graphql"

// For Redis integration
"cweijan.vscode-redis-client"

// For API documentation
"ms-vscode.vscode-apiconnected-swagger"

// For environment file management
"mikestead.dotenv"
```

### Using Thunder Client
- Visual interface for building requests
- Environment variables for different stages
- Test collections for regression testing
- Response history and validation

## Environment Management

### Development Environment
```bash
# .env.development
NODE_ENV=development
PORT=3000
DATABASE_URL=sqlite:./dev.db
LOG_LEVEL=debug
```

### Container Environment Variables
```json
// In devcontainer.json
"containerEnv": {
  "NODE_ENV": "development",
  "DEBUG": "app:*"
}
```

## Troubleshooting

**Port already in use?**
- Check forwarded ports in devcontainer.json
- Use `lsof -i :3000` to find what's using the port
- Try alternative ports (3001, 8000)

**Database connection issues?**
- Ensure database service is running (Docker Compose)
- Check port forwarding configuration
- Verify connection strings in environment variables

**NPM packages not installing?**
- Rebuild container to refresh package installation
- Check internet connection for package downloads
- Clear npm cache: `npm cache clean --force`

**TypeScript errors?**
- Restart TypeScript server: `Cmd+Shift+P` → "TypeScript: Restart TS Server"
- Check tsconfig.json configuration
- Ensure @types packages are installed

**API testing not working?**
- Verify server is running on expected port
- Check REST Client syntax in .http files
- Use Thunder Client for visual debugging

## Why This Approach Works for Parent Developers

**No Setup Friction**: Clone repo, open container, start coding APIs immediately.

**Experiment Safely**: Try new packages, database schemas, and AI suggestions without breaking your host environment.

**Consistent Environment**: Same setup works on your laptop, partner's computer, or Codespaces.

**Quick Recovery**: If something breaks, rebuild container in 30 seconds instead of hours debugging Node/npm issues.

**Secure by Default**: AI tools and external packages can't access your credentials or other projects.

## The Parent Developer Advantage

This container eliminates the backend-specific time wasters:
- No more Node version conflicts between projects
- No more global package pollution
- No more "works on my machine" database issues
- No more security anxiety when trying new packages

Your precious 15-minute coding windows are spent building features, not fighting with environment setup.

## Contributing

This devcontainer is part of the [raisingpixels.dev](https://raisingpixels.dev) parent developer resources. Found an improvement? Open an issue or PR!

Based on the post: ["The AWS Bill That Wasn't Yours: Why Parent Developers Need AI Security"](https://raisingpixels.dev/the-aws-bill-that-wasnt-yours-why-parent-developers-need-ai-security-and-how-containers-help/)

## License

MIT - Use this however helps your parent developer workflow!

---

*Ready to build APIs safely and efficiently? Copy this devcontainer into your next Node.js project and start developing with confidence.*
