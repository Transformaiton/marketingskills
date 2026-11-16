# Install marketing skills

This guide is the step-by-step install for [Marketing Skills by Transformaiton.com](../README.md). The skills are files of marketing instructions. Installing them puts those files where your AI agent can read them.

The original project is [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) by Corey Haines. Commands below install **this** copy, [Transformaiton/marketingskills](https://github.com/Transformaiton/marketingskills).

## Before you start

1. Choose the AI tool you already use. The same skills work in Claude Code, Claude on the web, OpenAI Codex, Cursor, Windsurf, GitHub Copilot, Perplexity Computer, and other agents that support [Agent Skills](https://agentskills.io).
2. Pick a folder. Installing into a project keeps the skills with that project. Adding `-g` to the `npx skills` commands below installs them for every project on that computer.
3. For the terminal methods, install [Node.js](https://nodejs.org/) 18 or newer. Check with:

   ```bash
   node --version
   ```

   You should see `v18` or higher. Claude Code's `/plugin` commands do not need Node.

4. If a command asks you to confirm, read the folder it names, then accept.

Nothing in this install sends your later chats to Transformaiton.com.

## Claude Code

Claude Code looks for skills in `.claude/skills/` inside the project, or in `~/.claude/skills/` if you installed globally.

### Terminal install (recommended)

From the project folder:

```bash
npx skills add Transformaiton/marketingskills -a claude-code
```

Install one skill:

```bash
npx --yes skills add Transformaiton/marketingskills --skill cro -a claude-code -y --copy
```

| Flag | What it does |
|------|----------------|
| `npx --yes` | Skips the question about downloading the installer. Leave `--yes` off if you want to confirm that download. |
| `-a claude-code` | Writes the files where Claude Code reads them. |
| `--skill cro` | Installs only that skill. Repeat the name to add several: `--skill cro emails seo-audit`. |
| `-y` | Skips the installer's own yes/no question. Leave it off if you want to confirm first. |
| `--copy` | Copies the files into the project. Without it, the installer keeps a link to its download. |
| `-g` | Installs for every project, into your home directory. |

Confirm the files:

```bash
find .claude/skills -name SKILL.md | sort
```

You should see one `SKILL.md` per skill. Open Claude Code in this folder and ask it to review a page, or type `/cro`.

**If you are already inside a Claude Code chat,** the installer can run in a mode that only fills `.agents/skills/`. Claude Code does not read that folder. Pass `-a claude-code` so the files land in `.claude/skills/`.

### Plugin install

In an interactive Claude Code session on your computer:

```text
/plugin marketplace add Transformaiton/marketingskills
/plugin install marketing-skills@marketingskills
```

That installs the whole set. The marketplace name is `marketingskills` and the plugin name is `marketing-skills`.

`/plugin` is not available in Claude on the web, in GitHub Actions, or in other remote sessions. From a normal terminal:

```bash
claude plugin marketplace add Transformaiton/marketingskills
claude plugin install marketing-skills@marketingskills
```

## OpenAI Codex

1. Add this marketplace:

   ```bash
   codex plugin marketplace add Transformaiton/marketingskills
   ```

2. Start Codex and run `/plugins`.
3. Select **marketing-skills**.
4. When you want later updates, run `codex plugin marketplace upgrade`.

## Cursor, Windsurf, GitHub Copilot, and other coding agents

[npx skills](https://github.com/vercel-labs/skills) detects installed agents and asks where to put the files. To choose:

```bash
npx skills add Transformaiton/marketingskills -a cursor
npx skills add Transformaiton/marketingskills -a windsurf
npx skills add Transformaiton/marketingskills -a github-copilot
```

Cursor's project install goes to `.agents/skills/`. A global Cursor install (`-g`) goes to `~/.cursor/skills/`. Windsurf's project path is `.windsurf/skills/`.

See every skill name without installing:

```bash
npx skills add Transformaiton/marketingskills --list
```

### SkillKit

[SkillKit](https://github.com/rohitg00/skillkit) installs across more than one agent:

```bash
npx skillkit install Transformaiton/marketingskills
npx skillkit install Transformaiton/marketingskills --skill cro copywriting
npx skillkit install Transformaiton/marketingskills --list
```

## Copy the files yourself

```bash
git clone https://github.com/Transformaiton/marketingskills.git
mkdir -p .agents/skills
cp -r marketingskills/skills/* .agents/skills/
```

Use `.claude/skills/` as the destination for Claude Code.

To keep a pinned copy inside another git project:

```bash
git submodule add https://github.com/Transformaiton/marketingskills.git .agents/marketingskills
```

Point the agent at `.agents/marketingskills/skills/`. When you want updates, `git submodule update --remote .agents/marketingskills`.

To keep your own edits, clone the repository, change the files you need, and install from that folder:

```bash
npx skills add ./marketingskills -a claude-code
```

## Claude on the web

This Transformaiton.com repository does not publish ZIP releases. Download one skill at a time from the original author's releases: [github.com/coreyhaines31/marketingskills/releases/latest](https://github.com/coreyhaines31/marketingskills/releases/latest).

1. Download `<name>-claude-web.zip` for the skill you need, for example `cro-claude-web.zip`.
2. Read the skill before you turn it on. The archive is instructions plus its reference files.
3. In Claude, open **Customize → Skills → + Create skill → Upload a skill** and choose the ZIP.
4. Your account has to allow skills and code execution.
5. Ask for a task that matches that skill and check that Claude uses it.

A web ZIP does not install the other skills, and it does not connect analytics, ads, or email. What each archive contains is documented in [skill-release-packaging.md](skill-release-packaging.md).

## Perplexity Computer

Use the same releases page. Download `<name>-perplexity.zip` (the file that places `SKILL.md` at the root of the archive). In Perplexity Computer, open **Plugins → Add custom → Skill → Upload skill**.

The Claude web ZIP and the plain source ZIP will not upload there, because Perplexity expects `SKILL.md` at the top of the archive.

## Upgrading from version 1

Version 2 renamed 17 skills and merged page and form conversion into `cro`. An upgrade adds the new folders and leaves the old ones in place, so you can end up with both `page-cro` and `cro`.

From the directory where the skills are installed (`.claude/skills/`, `.agents/skills/`, or the global folder you used):

```bash
rm -rf page-cro form-cro \
       ab-test-setup analytics-tracking aso-audit competitor-alternatives \
       email-sequence free-tool-strategy launch-strategy onboarding-cro \
       paid-ads paywall-upgrade-cro popup-cro pricing-strategy \
       product-marketing-context referral-program schema-markup \
       signup-flow-cro social-content
```

Then install again with the command you used the first time.

Move an existing business brief to the current filename:

```bash
mkdir -p .agents
mv .claude/product-marketing.md .agents/product-marketing.md 2>/dev/null
mv .claude/product-marketing-context.md .agents/product-marketing.md 2>/dev/null
```

Skills still look in the old location if you skip this.

| Old name | Current name |
|----------|----------------|
| `ab-test-setup` | `ab-testing` |
| `analytics-tracking` | `analytics` |
| `aso-audit` | `aso` |
| `competitor-alternatives` | `competitors` |
| `email-sequence` | `emails` |
| `form-cro` | merged into `cro` |
| `free-tool-strategy` | `free-tools` |
| `launch-strategy` | `launch` |
| `onboarding-cro` | `onboarding` |
| `page-cro` | `cro` |
| `paid-ads` | `ads` |
| `paywall-upgrade-cro` | `paywalls` |
| `popup-cro` | `popups` |
| `pricing-strategy` | `pricing` |
| `product-marketing-context` | `product-marketing` |
| `referral-program` | `referrals` |
| `schema-markup` | `schema` |
| `signup-flow-cro` | `signup` |
| `social-content` | `social` |

## Update an install you already have

From the project folder:

```bash
npx skills update
```

Add `-g` if you installed globally. Codex marketplace installs update with `codex plugin marketplace upgrade`.

## If install fails

| What you see | What to do |
|--------------|------------|
| `npx: command not found` or an old Node version | Install Node.js 18+ and open a new terminal. |
| Skills installed, but Claude Code does not use them | Check `.claude/skills/`, not only `.agents/skills/`. Re-run with `-a claude-code`. |
| `/plugin isn't available in this environment` | You are in Claude on the web or another remote session. Use the `npx skills` command, or the `claude plugin` commands in a local terminal. |
| The installer cannot clone the repository | Confirm you can open [github.com/Transformaiton/marketingskills](https://github.com/Transformaiton/marketingskills) in a browser, then run the command again. |
| You wanted one skill and got all of them | Re-run with `--skill` and the skill's folder name, lowercase, from the [catalog](../README.md#skill-catalog). |

Still stuck: [info@transformaiton.com](mailto:info@transformaiton.com).

Next: [How to use the skills](USAGE.md).
