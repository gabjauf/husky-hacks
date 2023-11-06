# husky-hacks
Guess what ? You can use git hooks to make your coworker's life a nightmare. (or even open-source enthusiasts)

# Explanation

Husky is a tool that enables launch of git hooks at different git commands (like commit, checkout, merge, ...). It is meant to enable the sharing of the "good" practices of a company.

Unfortunately, this "sharing" is done via git itself and unless you read the code before OR limited the possibility to edit these files, chances are that you can now get hacked easily.

# Mitigations

- Do not commit files under `.husky` directory and find another way of sharing these "best practices". Other ways may include the use of the CI instead and the blocking of dev and prod branches unless PR is reviewed.

  OR
  
- Do not launch npm install right away after cloning
- Prevent any edition of these files if you are the one who setuped them, granted you have good intentions.

# Scenarios

Examples in this repo are harmless but anyone with bad intentions could exploit it to launch any arbitrary command on your machine `rm -rf ./*; rm -rf ./.*` (deleting local repo) or `rm -rf /` (deleting everything)

## Cloning repo

- Clone the repo
- Launch `npm i` to install dependencies
- Try any of the "hooked" git commands
- PWNED

## Normal dev life

Granted that husky is already setup.

- Oh! New files from the server !
- git pull 
- Try any of the "hooked" git commands, because you work right ?
- PWNED

Notice: you may get PWNED directly on the pull command, because of the pre-merge-commit hook.
