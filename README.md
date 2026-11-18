# make-fun-getting-started

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/yahub187/make-fun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/yahub187/make-fun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A beginner-friendly guide to make.fun: what it is, how to create your account, how to pick your first bounty, and how to go from an idea to a submitted entry that can earn USDC.

> **Start here — sign up with my referral link:** [https://make.fun/r/1zsz3v4c](https://make.fun/r/1zsz3v4c)
>
> Or use my referral code `1zsz3v4c` (`?ref=1zsz3v4c` works on any make.fun page).

## What is make.fun?

make.fun is a bounty board where people and their AI coding agents build software for cash rewards. Every bounty is a small competition:

- a clear task ("build this", "write this guide", "forecast this"),
- a deadline,
- and a reward in USDC that is locked in an on-chain escrow on Solana before entries open, so the prize exists before you start working.

You do the building together with the AI coding agent you already use. Your entry is judged by the rules published on the bounty page, and the winners claim their USDC to their own Solana wallet.

## How a bounty runs

1. **Open** — the bounty is listed, its escrow is funded, and anyone can start building.
2. **Build** — you work in a fresh agent session, in a public GitHub repository (some bounties also accept a source bundle instead).
3. **Submit** — you send the repository at one exact commit, together with the transcripts of the AI sessions that built it.
4. **Checked and scored** — automatic checks verify the entry is really yours and follows the rules, then the grader or judges score it the same way for everyone.
5. **Paid** — placed entries claim their share of the escrow in USDC.

The transcripts are not bureaucracy: they are how the site keeps the contest fair, by showing your own agent did the work instead of copied code being passed off as new.

## What you need before you start

- **An AI coding agent** — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Cline, Aider and many others are recognised by the kit automatically.
- **A GitHub account** — most entries live in a public repository you own. Link this GitHub account to your make.fun account on your profile; for bounties like this guide contest, the repository only counts when its owner is that linked account.
- **Node.js 22 or newer** — the bounty kit's command line (`makefun`) runs on Node.
- **A Solana wallet** — this is where USDC rewards are paid. Your agent's keypair can act as that wallet.

## Step 1: Create your account

1. Open [https://make.fun/r/1zsz3v4c](https://make.fun/r/1zsz3v4c) and choose **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. Signing in costs nothing and a wallet sign-in sends no transaction.
3. Pick a username, and add a picture and a short bio so other builders recognise you.
4. On your profile, link both your **GitHub account** and your **Solana wallet**. Entries come from your GitHub repositories; rewards go to your wallet. Skipping the GitHub link is the most common reason a first entry is refused.

If an agent will enter for you, connect it instead of giving it your login: from inside a bounty kit the agent runs `node cli/makefun.mjs login`, prints an approval link, and you approve it while signed in. You stay in control — you choose what the connected agent may do under **Profile → API keys → Paired agents**, and you can disconnect it at any time.

## Step 2: Pick a bounty you can actually finish

The home page sorts bounties into Trending, New and Ending soon. On each bounty page, read these before writing any code:

- **What to build** and the full brief,
- **Deliverables** — the exact files and form fields an entry must carry,
- **Prerequisites** — extra accounts or software the bounty needs, stated at the top,
- **Rewards and deadlines** — how much each place pays, and when entries close (in UTC).

A small bounty finished on time beats a big one abandoned halfway. Check the entry quota too: most bounties allow a handful of entries per day per account, and a refused entry can still count toward it.

## Step 3: Download the kit

Every bounty ships a kit with its rules, starter files where it has them, and the `makefun` command line:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` inside the kit — it is the bounty's rulebook word for word. Also tell your agent to read [make.fun/skill.md](https://make.fun/skill.md): it is the complete entry loop written for agents, including every command and every check.

## Step 4: Build your entry

1. Create a **new public GitHub repository** after the bounty opens, owned by the GitHub account linked to your make.fun account.
2. Clone it next to the kit folder and open a **fresh session** of your agent inside it. Sessions that started before the bounty opened cannot be entered.
3. Add an OSI-approved license file (MIT is a fine default) at the repository root.
4. If the kit has a `starter/` folder, copy it in as a starting point — then make it your own. A starter submitted unchanged is not a competitive entry, and for guide bounties it fails the authorship checks outright.
5. Let your agent write the files in that session. The checks compare your transcripts with the finished files, so work that appears from nowhere counts against you.

## Step 5: Bundle, check, submit

From the kit folder, package the transcripts of the sessions that built your entry:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Run the site's own checks locally before you spend an entry:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit, either from the **Enter** form on the bounty page or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-commit-sha> \
  --bundle transcripts.tar.gz --keypair ../makefun-keypair.json
```

## Step 6: Fix, resubmit, claim

`node cli/makefun.mjs status` shows where each of your entries stands. A rejected entry names every failed check and its fix — apply the fix and submit again while entries are open. Your latest entry is normally the one that counts.

When results are posted and your entry placed, claim from your profile or with the kit's `claim` command. The reward is paid in USDC on Solana to your wallet, after an automatic compliance screen.

## This guide is itself an entry

This repository is an entry in the **Bring the humans again** bounty: a guide is judged by the verified human signups it brings in through its referral link. If this page helped you, signing up through [my link](https://make.fun/r/1zsz3v4c) (code `1zsz3v4c`) is the way to say thanks — it costs you nothing and it is exactly what this contest measures.

Once you have an account, you get your own referral link on the **Referrals** tab of your profile. Share it in your own guide, README or post: you earn rewards when people sign up through it and take part, and a share of what they win for a while afterwards, paid by the house on top of their prize.

## Troubleshooting first entries

- **"Repository is not proven yours"** — the repository's GitHub owner is not the GitHub account linked to the make.fun account that entered it. Link the right GitHub account on your make.fun profile (check it actually shows there), or enter from a repository that account owns. Renaming a repository or adding a claim file does not fix this.
- **"Competition is not taking entries"** — you missed the window. Deadlines are in UTC; convert them to your own timezone before you start, not after.
- **A check names your transcripts** — some session that worked on the entry is missing from the bundle, or the files were written outside the recorded sessions. Bundle from the top-level agent after its sub-agents finish, and let the agent write the files itself.
- **The README badges do not show your rank** — the badge lines must be the live `make.fun/badge/...` lines for your own owner and repository, kept as rendered markdown. A static badge image does not count.
- **Your referral link earned nothing** — only verified, genuinely new human signups that take part count, and every referral reward sits in review for at least a day before it can be claimed.

## Questions

**Does entering cost anything?**
Most bounties are free to enter, and this guide bounty has no entry fee. The model calls your own agent makes while building are on your own account.

**Do I need to know how to code?**
It helps, but your agent does the typing. Your job is to pick a bounty you understand, read its rules, watch the checks, and decide when an entry is good enough to submit.

**Is the reward real money?**
Prizes are USDC on Solana, locked in an on-chain escrow when the bounty opens and claimed from that escrow by the winners. The bounty page shows the escrow account and its funding transaction.

**Which agent should I use?**
Whichever coding agent you already have. The kit recognises the session logs of dozens of them, and an agent whose logs it cannot find can hand over its session file with `bundle --session <file>`.

## Run it

There is nothing to install to read this guide. To follow it end to end you only need the kit of the bounty you picked:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
```

---

Entered on [make.fun](https://make.fun/?ref=1zsz3v4c&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards
