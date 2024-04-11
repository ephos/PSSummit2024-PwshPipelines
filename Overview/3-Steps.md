# Steps 

These are the steps each video walks through.

## 1 - Setup the Github Repo

We need to get this up with Git and Github.

```bash
vlc ../1-Github_Repo/1-create_github_repo.mp4
```

You can also create the repo with the Github CLI `gh`.  

## 2 - Setup Your PSGallery API Key and Repo Secret

```bash
vlc ../2-PSGallery_GithubActionsSecret/2-ps_gallery_api_gh_action_secret.mp4
```

You may have noticed that nothing ran when we pushed our actions to the **main** branch.
This is because we don't want to deploy on changes to our actions, if you do change your action.

In the example below you would need to remove the paths-ignore section.

```yml
# pwsh-module-deploy.yml
on:
  push:
    branches:
      - main
    paths-ignore:
      - .github/**    
```

## 3 - Add the Github Workflows to the Repo

Now we can add the workflows for the Github Actions.

```bash
vlc ../3-Create_Github_Workflows/3-add_gh_workflows.mp4
```

## 4 - Running the Validation Action

You can run the workflow.

```bash
vlc ../4-Run_Github_Actions/4-gh_action_run.mp4
```

## 5 - Updating Code and Deploying to PSGallery

If you want you can likely remove the extra validation run.
In this case the robots are running the validation workflow for me so I don't care how many times we clobber it.

```bash
../5-Deploy_a_FeatureBranch/5-feature_branch_deploy.mp4
```

## 6 - Mission Accomplished

Note: It can take a few minutes for your module to show up in the PSGallery.  If you don't see it right away, don't worry!

```powershell
Find-Module -Name PSSummitDemo

../6-Module_Deployed/6-module_automatically_deployed.mp4

```

