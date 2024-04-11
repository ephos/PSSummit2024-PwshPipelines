# Module Structure

## Why a Specific Structure?

Our module simulates the following:

- We have a private function not exposed to users
- We have a module dependency (`PSTcpIp`) in use and declared in the module manifest
- Our module is structured in a way that will enable benefits of this CI/CD process
  * This is in part for managing our functions and some Git cleanliness 
  * This is also a huge part of our `Pester` testing strategy

`Plaster` is a great way to make short work of what we're about to review!

## Review of Our Test Module

This structure is for the following reason:

- If it's in _src_ we ship it!
- If it's not in _src_ we leave it behind!

### Source (src)

Everything in "src" is what we ship, this is our module!!!

Note: There is debate around using src vs using the module name. We're using "src"
Note on the note: If you don't use "src" you won't get the fun icon in VS Code.

Our functions are split into public and private! 
They are silly but do the following:

- Private:
  * `Get-Message`: Gets a random Sim City 2000 loading message
- Public: 
  * `Get-GithubTlsInfo`: Gets the Github certificate details
    - This is our function that relies on `PSTcpIp` as a dependency
  * `Get-SumOfNumbers`: Will take 2 `[Int]` and add them
  * `Out-SummitMessage`: Will output a `[PSCustomObject]` with a Message and Secondary message
    - This function calls the `Get-Message` Private function

### Tests (test)

We have `Pester` tests as well!

- Tests for validating module structure
- Some... Okay enough for this this demo 'unit tests'

### Last Thoughts

We have some other things that reside in the root of the module.
These don't need to go to the PSGallery.

- If you DO have Pester or Markdown that needs to ship, include it somewhere in src!
- Why would we want to ship .git / .github / ReadMe.md etc?  We don't.

## Review the Module

```powershell
# Inside the module
Push-Location ../PSSummitDemo/

# Review our structure
nvim .
```
