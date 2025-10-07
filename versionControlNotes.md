## Couple notes on routine git commands

check your remotes
`git remote -v` 
- origin is my repo
- upstream is uni src


#### pulling new labs
pull from uni src
`git fetch upstream`
switch to branch you want to merge new lab into (example:`main`)
`git checkout main` or `git branch main`
merge into my local branch
`git merge upstream/main`

#### pushing changes
`git push orign main`

# Don't overpush to main
do regular work on seperate branch and periodically merge with an up-to-date `main`

- ensure upstream is merged into main
- then merge `working-branch` into `main`

### typical update cycle
good habit to do this before every work session
- `git fetch upstream`
- `git checkout main`
- `git merge upstream/main`
- `git push origin main`
- `git checkout my-work`
- `git rebase main   # or git merge main`
- `git push origin my-work`

copyable format:

git fetch upstream
git checkout main
git merge upstream/main
git push origin main
git checkout my-work
git rebase main   # or git merge main
git push origin my-work

