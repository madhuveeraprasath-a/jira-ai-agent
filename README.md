# jira-ai-agent

An AI-powered debugging agent that fetches Jira ticket details, scans the codebase, and surfaces relevant files with suggested changes — significantly reducing debug time.

## How It Works

1. Provide a Jira ticket ID
2. Agent fetches ticket description, comments, and metadata via **Atlassian MCP**
3. Agent scans the codebase for files relevant to the issue
4. Returns a ranked list of files with suggested changes and reasoning

## Tech Stack

- **Claude AI** — reasoning and code analysis
- **Atlassian MCP** — Jira ticket fetching
- **Chrome DevTools MCP** — performance profiling and debugging
- **Node.js / TypeScript**

## Features

- Automatic Jira context extraction (title, description, comments, labels)
- Codebase file relevance scoring
- Suggested diffs with explanations
- Works with monorepos and multi-package setups

## Setup

```bash
git clone https://github.com/madhuveeraprasath-a/jira-ai-agent.git
cd jira-ai-agent
npm install
```

Configure your environment:

```env
ANTHROPIC_API_KEY=your_key
JIRA_BASE_URL=https://your-org.atlassian.net
JIRA_EMAIL=your@email.com
JIRA_API_TOKEN=your_token
```

Run the agent:

```bash
npm run agent -- --ticket PROJ-1234
```

## Example Output

```
Ticket: PROJ-1234 — Login page slow on first load

Relevant files:
  1. src/bootstrap.ts         (score: 0.92) — 59 scripts loaded eagerly
  2. src/shell/app.module.ts  (score: 0.87) — Module Federation remotes config
  3. webpack.config.js        (score: 0.74) — Missing lazy chunk boundaries

Suggested fix: Defer non-critical remotes in bootstrap.ts using dynamic import()
```

## Built At

Originally built and used at **Whatfix** to debug customer-facing issues in the Digital Adoption Platform. Reduced average debug time significantly by eliminating manual Jira → codebase context switching.

## License

MIT
