# Sanity Check Report

This report details the findings of a sanity check performed on the n8n-course project.

## Issues Found

### 1. Broken Links

*   **File**: `5_Symbols/Reading-Data-from-Google-Sheets/README.md`
    *   **Link**: `https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.googlesheets/`
    *   **Status**: Broken (404 Not Found)
*   **File**: `5_Symbols/Writing-Data-to-Google-Sheets/README.md`
    *   **Link**: `https://docs.n8n.io/integrations/builtin/cli-nodes/n8n-nodes-base.googlesheets/`
    *   **Status**: Broken (404 Not Found)

### 2. Link Inconsistencies

*   **File**: `5_Symbols/README.md`
    *   **Issue**: The links for "IF Node Advanced" and "The IF Node - Adding Logic" both point to the same file: `The-IF-Node-Adding-Logic-to-Your-Workflows/README.md`. This might be intentional, but it is worth reviewing.

### 3. Fixed Issues

The following issues have been fixed during the sanity check:

*   **File**: `5_Symbols/README.md`
    *   **Issue**: The link to `Lecture 17 - The IF Node` was broken and has been updated to point to the correct location.
    *   **Issue**: The link to `Project - Automated Discord/Slack Notifications` was missing URL encoding for the space.
*   **File**: `index.html`
    *   **Issue**: The link to `5_Symbols/Project%20-%20Automated%20Discord/Slack%20Notifications/README.md` was missing URL encoding for the space.
    *   **Issue**: The link to `5_Symbols/Viewing%20Your%20Workflow's%20Data/README.md` had an unencoded apostrophe.

## Recommendations

*   The broken links to the n8n Google Sheets node documentation should be updated to the correct URL. A search on the n8n documentation website should provide the correct link.
*   Review the duplicate links in `5_Symbols/README.md` to ensure that this is the intended behavior.
