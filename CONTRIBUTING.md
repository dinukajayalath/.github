# CONTRIBUTING.md
- This is from the .github folder

#  Branching strategy 
gitGraph LR:
  options {
    "nodeSpacing": 150,
    "commitSpacing": 60,
    "mainBranchName": "main"
  }
  commit id: "init"
  %% protected branches
  branch unstable
  checkout unstable
  commit id: "dev setup"

  %% larger work: dev_{YOUR_NAME}
  branch dev_dinuka
  checkout dev_dinuka
  commit id: "work 1"
  commit id: "work 2"
  checkout unstable
  merge dev_dinuka id: "merge dev_{YOUR_NAME}"

  %% smaller changes: feature / bugfix
  branch feature/A
  checkout feature/A
  commit id: "A1"
  commit id: "A2"
  checkout unstable
  merge feature/A

  branch bugfix/B
  checkout bugfix/B
  commit id: "fix B"
  checkout unstable
  merge bugfix/B

  %% release & hotfix flow
  checkout main
  commit type: HIGHLIGHT id: "release v2.0" tag: "v2.0"
  branch hotfix/v2.1
  checkout hotfix/v2.1
  commit id: "hotfix v2.1"
  checkout main
  merge hotfix/v2.1 id: "main after hotfix" tag: "v2.1"
  checkout unstable
  merge main id: "sync unstable"
