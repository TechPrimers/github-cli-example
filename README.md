# Github CLI Example
 
## Installation
- CLI can be installed using the steps mentioned in [https://cli.github.com/](https://cli.github.com/)

## Command used
1. Authenticate the Github CLI `gh` with your github.com account using `gh auth login`
```
❯ gh auth login

? What account do you want to log into? GitHub.com
- Logging into github.com
? You're already logged into github.com as MovingToWeb. Do you want to re-authenticate? Yes
? How would you like to authenticate? Login with a web browser

! First copy your one-time code: F960-6144
- Press Enter to open github.com in your browser...
✓ Authentication complete. Press Enter to continue...

? Choose default git protocol HTTPS
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as MovingToWeb
```

2. Create new repo using `gh repo create`. `TechPrimers/` denotes the organization under which the repository needs to be created.
```
❯ gh repo create TechPrimers/github-cli-example

? Visibility Public
? This will create 'TechPrimers/github-cli-example' in your current directory. Continue?  Yes
✓ Created repository TechPrimers/github-cli-example on GitHub
? Create a local project directory for TechPrimers/github-cli-example? Yes
Initialized empty Git repository in /Users/ajay/Documents/code/github-cli-example/.git/
✓ Initialized repository in './github-cli-example/'
```

3. Add a new file in the empty repo, commit it and push it to remote repository (github.com)

```
❯ cd github-cli-example

❯ vi README.md

❯ git add .

❯ git commit -am "[add] new file"
[main (root-commit) ccb0927] [add] new file
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

❯ git push --set-upstream origin main
Username for 'https://github.com': MovingToWeb
Password for 'https://MovingToWeb@github.com':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 246 bytes | 246.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/TechPrimers/github-cli-example.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

❯ gh repo view
```

4. Get documentation/help from the CLI directly using `--help` or `help` command
```
❯ gh config --help

Usage:  gh config [flags]

Available commands:
  get
  set

❯ gh help
Work seamlessly with GitHub from the command line.

USAGE
  gh <command> <subcommand> [flags]

CORE COMMANDS
  gist:       Create gists
  issue:      Manage issues
  pr:         Manage pull requests
  release:    Manage GitHub releases
  repo:       Create, clone, fork, and view repositories

ADDITIONAL COMMANDS
  alias:      Create command shortcuts
  api:        Make an authenticated GitHub API request
  auth:       Login, logout, and refresh your authentication
  completion: Generate shell completion scripts
  config:     Manage configuration for gh
  help:       Help about any command

FLAGS
  --help      Show help for command
  --version   Show gh version

EXAMPLES
  $ gh issue create
  $ gh repo clone cli/cli
  $ gh pr checkout 321

ENVIRONMENT VARIABLES
  See 'gh help environment' for the list of supported environment variables.

LEARN MORE
  Use 'gh <command> <subcommand> --help' for more information about a command.
  Read the manual at https://cli.github.com/manual

FEEDBACK
  Open an issue using 'gh issue create -R cli/cli'
```

5. Let's create a new issue to work on a new feature
```
❯ gh issue create

Creating issue in TechPrimers/github-cli-example

? Title Create a new feature
? Body <Received>
? What's next? Submit
https://github.com/TechPrimers/github-cli-example/issues/1
```

6. Let's create a feature branch and add the implementation of the feature in it.
```
❯ git checkout -b feature-1
Switched to a new branch 'feature-1'

❯ vi README.md

❯ git commit -am "[update] modified readme file"
[feature-1 f60a6c4] [update] modified readme file
 1 file changed, 2 insertions(+)

❯ git push --set-upstream origin feature-1
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 307 bytes | 307.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'feature-1' on GitHub by visiting:
remote:      https://github.com/TechPrimers/github-cli-example/pull/new/feature-1
remote:
To https://github.com/TechPrimers/github-cli-example.git
 * [new branch]      feature-1 -> feature-1
Branch 'feature-1' set up to track remote branch 'feature-1' from 'origin'.
```

7. To get the list of issue, use `list` command
```
❯ gh issue list
```

8. To create a pull request from the feature branch to the main branch, we can use `gh pr create`
```
❯ gh pr create

Creating pull request for feature-1 into main in TechPrimers/github-cli-example

? Title Added new Feature for issue-1
? Body <Received>
? What's next? Submit
https://github.com/TechPrimers/github-cli-example/pull/2
```

9. Use `list` to list the pull requests for the repo
```
❯ gh pr list
```

10. Finally merging the pull request can be done by `gh pr merge`
```
❯ gh pr merge

? What merge method would you like to use? Create a merge commit
? Delete the branch locally and on GitHub? Yes
✔ Merged pull request #2 (Added new Feature for issue-1)
✔ Deleted branch feature-1 and switched to branch main
```

## References
- [Github manual](https://cli.github.com/manual/)
