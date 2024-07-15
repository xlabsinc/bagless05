##### gh cli login
  ```
  gh auth login --with-token <<<$(cat ../token.txt | head -1)
  ```

##### check the status, private repos
  ```
  gh auth status

  export GH_ORG="xlabsinc" # xbalaji/xbalajipge/xb01/xb02/xbalajiv
  export GH_USER=$(gh auth status 2>&1 | grep "Logged in" | sed -e 's,\(.*github.com as \)\([a-z0-9A-Z]\+\)\(.*\),\2,g')
  export GH_REPO=$(basename ${PWD})

  gh repo -L 100 list ${GH_ORG}
  ```

##### configure the protocol to use ssh, to avoid https auth prompt and list config, tune as per need
  ```
  gh config set git_protocol ssh
  gh config list
  ```

##### initialize local git repo and add files locally
  ```
  git config --global init.defaultBranch main  && echo "#### PWD: $PWD" >> README.md
  git init . && git add . && git commit -m "Initial commit"
  ```

##### create remote repo using gh cli
  ```
  gh repo create --private "git@github.com:${GH_ORG}/${GH_REPO}"

  e.g:
  gh repo create --private git@github.com:xlabsinc/pub
  ```

##### configure the repo with the remote repo
  ```
  grep clone $HOME/.ssh/config # to find the line for using with create
  GH_RURL=$(grep -w "clone git@github.*${GH_ORG}" $HOME/.ssh/config | sed -e 's,\(.* git@github\)\(.*\)\/\(.*\),git@github\2,g')/${GH_REPO}
  git remote add origin "${GH_RURL}.git" && git branch -M main

  e.g:
  git remote add origin git@github-xlabsinc:xlabsinc/pub.git && git branch -M main
  ```


##### now push the changes to the remote repo
  ```
  git push --set-upstream origin main
  ```

##### list the permissions for the users in this repo
  ```
  gh api  "repos/${GH_ORG}/${GH_REPO}/collaborators" --jq '.[] | [.login, .role_name]'

  e.g:
  gh api  "repos/xlabsinc/pub/collaborators" --jq '.[] | [.login, .role_name]'
  ```

##### give permission for others to manage this repo, when part of organization
  ```
  gh api --method=PUT "repos/${GH_ORG}/${GH_REPO}/collaborators/xb02" -f permission="admin"

  e.g:
  gh api --method=PUT "repos/xlabsinc/openaichat/collaborators/xb02" -f permission="admin"
  ```

##### give permission for others to manage this repo, when part of organization
  ```
  gh api --method=PUT "orgs/${GH_ORG}/teams/xbalaji-accounts/repos/${GH_ORG}/${GH_REPO}" -f permission="admin"

  e.g:
  gh api --method=PUT "orgs/xlabsinc/teams/xbalaji-accounts/repos/xlabsinc/openaichat" -f permission="admin"
  ```

----
