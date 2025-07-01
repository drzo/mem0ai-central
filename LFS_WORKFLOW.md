# Git LFS Workflow Documentation

## Overview

This repository uses Git LFS (Large File Storage) to handle large binary files efficiently. The fetchsync workflow has been enhanced with comprehensive LFS support to prevent push failures due to missing LFS objects.

## LFS Integration Points

### 1. Repository Checkout
- Uses `lfs: true` parameter in `actions/checkout@v4`
- Automatically fetches LFS objects during checkout

### 2. LFS Setup and Initialization
- Installs Git LFS in the workflow environment
- Fetches all LFS objects with `git lfs fetch --all`
- Checks out LFS objects with `git lfs checkout`

### 3. LFS Integrity Validation
- Performs comprehensive integrity checks before operations
- Validates all tracked LFS files are materialized
- Attempts automatic recovery for missing LFS objects

### 4. Repository Synchronization
- Sets up LFS for each cloned repository
- Fetches and validates LFS objects before processing
- Ensures LFS files are materialized before removing .git directory

### 5. Pre-Push Validation
- Final integrity check before push operations
- Validates all LFS files are present and non-empty
- Aborts push if critical LFS files are missing

## Error Handling and Recovery

### Automatic Recovery Steps
1. **Missing LFS Files**: Attempts `git lfs pull` and `git lfs checkout`
2. **Empty LFS Files**: Re-fetches objects from LFS storage
3. **Validation Failures**: Provides detailed error messages for manual intervention

### Failure Scenarios
- **FATAL**: When LFS objects cannot be recovered after multiple attempts
- **CRITICAL**: When LFS files are missing or empty before push
- **WARNING**: When LFS files are missing during sync (with recovery attempt)

## File Tracking Patterns

The `.gitattributes` file defines which files are tracked by LFS:
- Binary executables (`.exe`, `.dll`, `.so`, etc.)
- Large media files (images, videos, audio)
- Archives and compressed files
- Large documents
- Specific paths like `autogen/dotnet/website/images/articles/*`

## Workflow Steps

### Standard Flow
1. **Checkout** → LFS objects fetched automatically
2. **LFS Setup** → Install and configure LFS
3. **Integrity Check** → Validate all LFS objects present
4. **Repository Sync** → Process repos with LFS support
5. **Pre-Push Validation** → Final integrity check
6. **Push** → Submit changes with validated LFS objects

### Recovery Flow
1. **Detection** → Missing LFS files identified
2. **Recovery** → `git lfs fetch --all` and `git lfs checkout`
3. **Re-validation** → Confirm recovery successful
4. **Continue/Abort** → Proceed if recovered, abort if failed

## Troubleshooting

### Common Issues
1. **LFS objects not found**: Ensure upstream repository has LFS objects pushed
2. **Authentication errors**: Verify LFS access permissions
3. **Storage quota exceeded**: Check LFS storage limits

### Manual Recovery
If automatic recovery fails:
1. Manually fetch specific files: `git lfs pull path/to/file`
2. Re-add missing files: `git add file && git commit`
3. Verify LFS tracking: `git lfs ls-files`

## Best Practices

1. **Always track large files with LFS** before first commit
2. **Use `.gitattributes`** to define LFS patterns consistently
3. **Test LFS setup** in development before production workflows
4. **Monitor LFS storage usage** to avoid quota issues
5. **Document LFS requirements** for contributors

## Cognitive Architecture Integration

This LFS implementation follows the recursive cognitive framework:
- **Memory System**: Persistent LFS object storage
- **Task System**: Automated workflow orchestration
- **AI System**: Intelligent error detection and recovery
- **Autonomy System**: Self-healing LFS validation

The system achieves distributed cognition through multi-layer validation and autonomous recovery mechanisms.