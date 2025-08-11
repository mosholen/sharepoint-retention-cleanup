# sharepoint-retention-cleanup
Automated cleanup script for SharePoint Online document libraries where Microsoft Purview retention auto-delete cannot run due to search exclusion. Recursively scans folders, deletes files older than a given threshold, and removes empty folders using Microsoft Graph API
