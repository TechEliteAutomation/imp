The error message "src refspec main does not match any" indicates that Git can't find a local branch named "main" to push to GitHub. This typically occurs when you've initialized a new repository but haven't created any commits yet, or when your repository's default branch is named differently (like "master" instead of "main").

Let's resolve this issue with the following steps:

## Check Current Branch

First, check which branch you're currently on:

```bash
git branch
```

If this shows no branches or shows a different branch name (like "master"), we'll need to create the main branch.

## Create the Main Branch

Create and switch to the main branch:

```bash
git checkout -b main
```

## Create Initial Content

Ensure you have some content to commit:

```bash
echo "# bin" > README.md
```

## Complete Initial Commit and Push

Now perform the initial commit and push:

```bash
git add .
git commit -m "Initial commit"
git push -u origin main --force
```

## For All Repositories

Repeat this process for each repository:

```bash
# For bld repository
cd ~/s/bld
git checkout -b main
echo "# bld" > README.md
git add .
git commit -m "Initial commit"
git push -u origin main --force

# For doc repository
cd ~/s/doc
git checkout -b main
echo "# doc" > README.md
git add .
git commit -m "Initial commit"
git push -u origin main --force

# For web repository
cd ~/s/web
git checkout -b main
echo "# web" > README.md
git add .
git commit -m "Initial commit"
git push -u origin main --force
```

After completing these steps, all repositories should be properly initialized with a main branch and pushed to GitHub.

[u@h bld]$ echo "# bld" > README.md
[u@h bld]$ git add .
warning: adding embedded git repository: geany-themes
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint: 	git submodule add <url> geany-themes
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint: 	git rm --cached geany-themes
hint:
hint: See "git help submodule" for more information.
hint: Disable this message with "git config set advice.addEmbeddedRepo false"
warning: adding embedded git repository: nerd-fonts-jetbrains-mono
warning: adding embedded git repository: slstatus
warning: adding embedded git repository: yay
[u@h bld]$
