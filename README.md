# mem0ai-central

Central repository for integrating multiple repositories from the mem0ai organization into a unified structure.

## Overview

This repository serves as a central hub for integrating various repositories from the mem0ai organization. It provides automated workflows to clone repositories, remove their git history, and integrate them as subfolders while maintaining Git LFS support.

## Integrated Repositories

This repository integrates the following repositories from the mem0ai organization:

* mem0 - Core mem0 framework
* embedchainjs - JavaScript implementation of embedchain
* community-showcase - Community examples and showcases  
* .github - Organization-wide GitHub configurations
* qna-bot-template-py - Python Q&A bot template
* qna-bot-template-js - JavaScript Q&A bot template
* chat-bot-template-py - Python chat bot template
* embedchain-admin - Administration interface for embedchain
* examples - Example implementations and use cases
* friend-integration - Friend integration components
* autogen - AutoGen framework integration
* mem0-chrome-extension - Chrome browser extension
* companion-nextjs-starter - Next.js starter template
* mem0-mcp - Model Context Protocol implementation
* personalized-deep-research - Personalized research tools
* deep-research - Deep research framework
* grok3-api - Grok3 API integration

## Workflows

### mem0ai Integration Workflow

The `mem0ai-integration.yml` workflow automates the process of cloning and integrating repositories from the mem0ai organization:

- **Trigger**: Manual workflow dispatch
- **Features**:
  - Clones specific hardcoded repositories from mem0ai organization
  - Removes git history from cloned repositories
  - Maintains Git LFS support throughout the process
  - Comprehensive error handling and recovery
  - Automatic branch naming and PR creation
  - Force sync option to overwrite existing integrations

#### Usage

1. Go to the Actions tab in this repository
2. Select "Integrate mem0ai Repositories" workflow
3. Click "Run workflow"
4. Optionally enable "Force sync" to overwrite existing repositories
5. The workflow will create a new branch and pull request with the integrated repositories

## Git LFS Support

This repository uses Git LFS (Large File Storage) to handle large binary files efficiently. See [LFS_WORKFLOW.md](LFS_WORKFLOW.md) for detailed information about LFS integration and troubleshooting.

## Original References

* [Embedchain python](https://github.com/embedchain/embedchain)
* [Embedchain Javascript](https://github.com/embedchain/embedchainjs)