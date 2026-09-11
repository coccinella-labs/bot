<p align="center">
  <img src="https://raw.githubusercontent.com/Coccinella-Labs/bot/main/.github/assets/thumbnail.png" alt="bot" width="100%">
</p>

# Coccinella Labs Auto Bot

Automation bot for managing coccinella-labs organization repositories.

## Overview

This bot provides automated tasks for the coccinella-labs organization through GitHub Actions workflows that run automatically or on-demand.

## Features

### GitHub Actions Workflows

#### 1. Auto-Bot Workflow (.github/workflows/auto-bot.yml)

Automatically runs based on:

- **Schedule**: Daily at midnight (`0 0 * * *`)
- **Repository Dispatch**: When config repo is updated
- **Manual Trigger**: Workflow dispatch with action selection

#### Actions Available

| Action | Description |
|--------|-------------|
| `sync` | Compare config vs GitHub repos |
| `update` | Update all repos automatically |
| `backup` | Create backup of all repos |
| `report` | Generate daily report |

## Usage

### Automatic (Scheduled)

The workflow runs automatically every day at midnight.

### Manual Trigger

1. Go to https://github.com/coccinella-labs/bot/actions
2. Click "Run workflow"
3. Select action: sync, update, backup, or report

### Trigger from Config Changes

Update `repos.json` in config repo → triggers auto-update!

## Workflows

### Daily Sync
- Runs at midnight every day
- Compares config repos vs actual GitHub repos
- Reports any discrepancies

### Update All Repos
- Clones all repos
- Makes specified changes
- Commits and pushes to all repos

### Backup
- Creates mirror clones of all repos
- Archives as .tar.gz
- Uploads as artifact

### Report
- Generates daily statistics
- Lists public vs private repos
- Maintains history

## Setup

No additional setup needed! The workflows use GitHub's built-in token.

## How It Works

```
Config Repo (repos.json)
       ↓
  Repository Dispatch
       ↓
  Auto-Bot Workflow
       ↓
  Updates All Repos
       ↓
  Commits & Pushes
```

## Repositories Managed

See [coccinella-labs/config/repos.json](https://github.com/coccinella-labs/config/blob/main/repos.json)

Managed repos are defined by the config repo (currently 14 in the managed subset).