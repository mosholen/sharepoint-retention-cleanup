# SharePoint Retention Cleanup – Automated Document Library Cleanup
Automated cleanup script for SharePoint Online document libraries where Microsoft Purview retention auto-delete cannot run due to search exclusion. Recursively scans folders, deletes files older than a given threshold, and removes empty folders using Microsoft Graph API


This project is a C# script file directly using dotnet run "filename.cs" that uses the **Microsoft Graph API** to delete files and folders in a SharePoint Online document library based on file age.  
It was built specifically for scenarios where **Microsoft Purview Retention** auto-delete cannot run due to search exclusion, or where you want to manually trigger cleanup.

You can set this up as a schedule task to run it.

## 🎯 Why this script was created
This tool was made to address a known limitation with **Microsoft Purview Retention** when a SharePoint site is excluded from search:

> Purview retention (auto-labels/auto-delete based on KQL/adaptive scope) relies on the search index to find content.  
> If a SharePoint site is set to *“Do not allow this site to appear in search results”*, such auto-rules will not work.  
> You must either scope the policy **statically** (explicit URL/location) or use a cleanup script like this.

This tool is designed for exactly such cases – when automated deletion won’t run because the site is excluded from search, or when you want to run a controlled cleanup.

---

## dependencies
- [.NET 10.0.0-preview](https://dotnet.microsoft.com/)
- [Microsoft Graph SDK](https://learn.microsoft.com/graph/sdks/sdks-overview)
- [Azure.Identity](https://learn.microsoft.com/dotnet/api/azure.identity)
- [Microsoft.Extensions.Logging.Console](https://learn.microsoft.com/dotnet/core/extensions/console-log-formatter)
- [DotNetEnv](https://github.com/tonerdo/dotnet-env) for `.env` file loading

---

## Setup

1. **Clone the repo**  
   ```bash
   git clone https://github.com/<username>/sharepoint-retention-cleanup.git
   cd sharepoint-retention-cleanup


4. **Run the script**
   ```bash
   dotnet run delete_sharepoint_items_and_folders.cs --drive "driveID" --root "rootID" --months 3

5. You can optionaly use ```--dry-run```  for testing
