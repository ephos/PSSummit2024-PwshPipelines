# PowerShell Module Pipeline

---

## Prerequisites 

This assumes you have a PowerShell module already.
Ideally it should have the structure we want for this particular CI/CD pipeline.
The structure will keep function files as their own _*.ps1_ files separated by public and private use.

We'll review the structure.

---

What we need:

1. A PowerShell Module with the Correct Structure
2. A Git repository in **Github**
3. Steps to take with `PSScriptAnalyzer` and `Pester` to validate our code
4. Github actions to validate, and when ready, deploy our code to the PSGallery!

---

### Review of the Module and Structure

Our module simulates the following:

- We have a private function not exposed to users
- We have a module dependency in use and declared in the module manifest
- Our module is structure in a way that will really enable benefits of this CI/CD process

Our functions are silly but do the following:

- Private `Get-Message`: Get's a random Sim City 2000 loading message
- Public `Get-GithubTlsInfo`: Gets the Github certificate details
  * This module relies on _PSTCPIP_ as a dependency
- Public `Get-SumOfNumbers`: Will take 2 `[Int]` and add them
- Public `Out-SummitMessage`: Will output a `[PSCustomObject]` with a Message and Secondary message
  * This function calls the `Get-Message` Private function

We also have:

- Pester Tests!

This module structure is setup so that everything in _src_ is what is shipped.
EVERYTHING ELSE GETS LEFT BEHIND!!!

- Why would we want to ship our Pester tests that are only used for dev? We don't.
- Why would we want to ship .git / .github / ReadMe.md etc?  We don't.
- Only ship what is in "_src_", that is your module!
- If you have Pester or Markdown that needs to ship, include it somewhere in src!

There is also debate on if you want to use _src_ or just use the module name, this is up to you!
I like _src_ because it gets a fun icon in certain programs.

Review the module.

```powershell
# Inside the module
Push-Location ./PSSummitDemo/

# Review our structure
vim .
```

`Plaster` is a great way to scaffold this if needed.

---

### How We Validate Locally, is How We Validate Everywhere

We have Pester tests, we'll wire those up to our Github action soon to validate.

Before we do let's test them locally.  We can also run PSScriptAnalyzer. 

```powershell
# Run Pester and Script Analyzer
Invoke-Pester -Output Detailed
Invoke-ScriptAnalyzer -Path ./src/ -Recurse
```

--- 

## 1 - Git'n to Git, A.K.A. Getting it to Github

We need to get this up with Git and Github.

```bash
vlc ./1-create_github_repo.mp4
```

You can also create the repo with the Github CLI `gh`.  

---

## 2 - Setup Your PSGallery API Key and Repo Secret

```bash
vlc ./2-ps_gallery_api_gh_action_secret.mp4
```

You may have noticed that nothing ran when we pushed our actions to the **main** branch.
This is because we don't want to deploy on changes to our actions, if you do change your action.

```yml
# pwsh-module-deploy.yml
on:
  push:
    branches:
      - main
    paths-ignore:
      - .github/**
```

---

## 3 - Add the Github Workflows to the Repo

Now we can add the workflows for the Github Actions.

```bash
vlc 3-add_gh_workflows.mp4
```

---

## 4 - Running the Validation Action

You can run the workflow.

```bash
vlc 4-gh_action_run.mp4
```


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

