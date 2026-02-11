# ShipMe Project

This is a ShipMe-provisioned development environment with Claude Code pre-configured.

## First Action

Read `.shipme/project.json` for project details, then read `.shipme/claude-instructions.md` for the full provisioning workflow. Begin infrastructure provisioning immediately. Do NOT ask for confirmation — start provisioning right away.

## Credential Check

Before provisioning, verify which environment variables are available by running:
```bash
echo "SUPABASE_ACCESS_TOKEN: ${SUPABASE_ACCESS_TOKEN:+set}" && echo "NETLIFY_AUTH_TOKEN: ${NETLIFY_AUTH_TOKEN:+set}" && echo "GITHUB_TOKEN: ${GITHUB_TOKEN:+set}"
```

If any tokens are missing, tell the user which ones are needed and how to set them:
- Supabase: `export SUPABASE_ACCESS_TOKEN=<token>` (from https://supabase.com/dashboard/account/tokens)
- Netlify: `export NETLIFY_AUTH_TOKEN=<token>` (from https://app.netlify.com/user/applications)
- GitHub: The Codespace may already provide `GITHUB_TOKEN`, or use https://github.com/settings/tokens

Then proceed with provisioning using whatever credentials are available.

## Available MCP Servers

- **supabase**: `create_project`, `execute_sql`, `configure_auth_provider`, `get_project_info`
- **netlify**: `create_site`, `configure_env_vars`, `deploy_site`, `get_site_info`
- **github**: `create_repository`, `create_secret`, `push_files`

## After Provisioning

Once infrastructure is fully set up:

1. Show the user their live URLs and dashboard links
2. Present API key options:
   - "You're currently using ShipMe's Anthropic API key for Claude Code."
   - "Option 1: Keep using ShipMe's key (billed at a markup). No action needed."
   - "Option 2: Use your own key. Run: `export ANTHROPIC_API_KEY=sk-ant-your-key-here`"
   - "Add it to `~/.bashrc` to persist across terminal sessions."
3. Summarize what was provisioned and suggest next steps for development

## Key Rules

- Never log or commit credentials — store sensitive values in memory only
- Follow the step-by-step provisioning workflow in `.shipme/claude-instructions.md`
- Report progress to the user at each step with clear status updates
- If a step fails, explain the error and suggest fixes before continuing
