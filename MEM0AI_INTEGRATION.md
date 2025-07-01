# mem0ai Repository Integration Guide

This document provides detailed instructions for integrating repositories from the mem0ai organization into this central repository.

## Overview

The mem0ai integration workflow automates the process of cloning 17 specific repositories from the mem0ai organization, removing their git history, and integrating them as subfolders in this central repository.

## Repositories to be Integrated

The following 17 repositories are configured for integration:

1. **mem0** - Core mem0 framework
2. **embedchainjs** - JavaScript implementation of embedchain
3. **community-showcase** - Community examples and showcases
4. **dotgithub** - Organization-wide GitHub configurations
5. **qna-bot-template-py** - Python Q&A bot template
6. **qna-bot-template-js** - JavaScript Q&A bot template
7. **chat-bot-template-py** - Python chat bot template
8. **embedchain-admin** - Administration interface for embedchain
9. **examples** - Example implementations and use cases
10. **friend-integration** - Friend integration components
11. **autogen** - AutoGen framework integration
12. **mem0-chrome-extension** - Chrome browser extension
13. **companion-nextjs-starter** - Next.js starter template
14. **mem0-mcp** - Model Context Protocol implementation
15. **personalized-deep-research** - Personalized research tools
16. **deep-research** - Deep research framework
17. **grok3-api** - Grok3 API integration

## Running the Integration

### Prerequisites

- Repository access to ZoneCog/mem0ai-central
- Appropriate GitHub permissions for running workflows
- Access to mem0ai organization repositories

### Steps

1. **Navigate to GitHub Actions**
   - Go to the repository on GitHub
   - Click on the "Actions" tab
   - Find "Integrate mem0ai Repositories" workflow

2. **Run the Workflow**
   - Click "Run workflow"
   - Choose options:
     - **Force sync**: Enable to overwrite existing repositories (optional)
   - Click "Run workflow" button

3. **Monitor Progress**
   - Watch the workflow execution in real-time
   - Check logs for any errors or warnings
   - Verify LFS integrity checks pass

4. **Review Results**
   - Check the automatically created branch (e.g., `mem0ai-integration`)
   - Review the generated pull request
   - Verify all repositories were successfully integrated

## Workflow Features

### Automatic Branch Creation
- Creates branches with automatic versioning
- Uses pattern: `mem0ai-integration`, `mem0ai-integration-v2`, etc.
- Force sync option allows overwriting existing branches

### Git LFS Support
- Full Git LFS support throughout the process
- Comprehensive integrity checking
- Automatic recovery for missing LFS objects
- Pre-push validation to prevent corruption

### Error Handling
- Graceful handling of missing or inaccessible repositories
- Continues processing other repositories if one fails
- Detailed logging for troubleshooting

### Automatic Pull Request Creation
- Creates PR with detailed description
- Lists all integrated repositories
- Ready for review and merge

## Troubleshooting

### Common Issues

1. **Repository Not Found**
   - Verify repository exists in mem0ai organization
   - Check repository visibility (public vs private)
   - Ensure proper authentication

2. **LFS Issues**
   - Check LFS storage quota
   - Verify LFS objects are properly pushed to source repos
   - Review LFS integrity check logs

3. **Permission Errors**
   - Ensure GitHub token has appropriate permissions
   - Check organization access settings
   - Verify workflow permissions

### Manual Recovery

If the workflow fails partway through:

1. Check which repositories were successfully integrated
2. Enable "Force sync" option for re-run
3. Or manually clean up and re-run specific repositories

## File Structure After Integration

After successful integration, the repository structure will be:

```
mem0ai-central/
├── .github/
│   └── workflows/
│       └── mem0ai-integration.yml
├── mem0/                    # Integrated repository
├── embedchainjs/           # Integrated repository
├── community-showcase/     # Integrated repository
├── .github/                # Integrated repository (from mem0ai)
├── qna-bot-template-py/    # Integrated repository
├── [... all other repositories ...]
├── .gitattributes          # LFS tracking configuration
├── LFS_WORKFLOW.md         # LFS documentation
└── README.md              # Main repository documentation
```

## Maintenance

### Re-running Integration

To update integrated repositories:

1. Enable "Force sync" option
2. Run the workflow again
3. This will overwrite existing repositories with latest versions

### Adding New Repositories

To add new repositories to the integration:

1. Edit `.github/workflows/mem0ai-integration.yml`
2. Add repository name to the `REPO_LIST` variable
3. Update this documentation
4. Commit changes and run workflow

## Security Considerations

- Git history is completely removed from integrated repositories
- Original repository references are maintained in commit messages
- LFS objects are preserved and validated
- All changes are made through pull requests for review