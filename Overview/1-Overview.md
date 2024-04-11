# Overview

This is an opinionated approach to publishing a module to the PowerShell Gallery.

This is intended to be a starting point, but you can go much farther with it.

We are not tempting demo gods or conference WiFi in this session!

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

## Quick Note

- This isn't going to be an in depth Github Actions workflow writing session.
- This isn't going to be a PowerShell module creation session.

We'll touch lightly on some of the topics, but out focus is the validation and deployment.



