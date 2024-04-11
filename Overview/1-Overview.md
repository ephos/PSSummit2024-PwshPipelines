# Overview

This is an opinionated approach to publishing a module to the PowerShell Gallery.

---

## Pre-Reqs

1. This assumes you have a PowerShell module already.
  a. Ideally it should have the structure we want for this particular CI/CD pipeline.
2. Github Account _(free)_
3. PowerShell Gallery Account _(free)_

If you have a flat module, the concepts here will still work, but your `Pester` tests and build will need to be updated.

---

So what is in play for what we're about to see?

1. A PowerShell Module
2. A Git repository in **Github**
3. A PowerShell Gallery account and API key
4. Our code validation process
  a. We're all using `PSScriptAnalyzer` and `Pester` to validate our code, right?
5. Github actions to validate, and when ready, deploy our code to the PSGallery!




## 5 - Updating Code and Deploying to PSGallery

If you want you can likely remove the extra validation run.
In this case the robots are running the validation workflow for me so I don't care how many times we clobber it.

```bash
vlc 5-feature_branch_deploy.mp4
```

## 6 - Mission Accomplished

Note: It can take a few minutes for your module to show up in the PSGallery.  If you don't see it right away, don't worry!

```powershell
Find-Module -Name PSSummitDemo

vlc 6-module_automatically_deployed.mp4
```

