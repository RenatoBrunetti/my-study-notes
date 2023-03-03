# Git
[main](../../README.md) | [general](../README.md) | [git](README.md)

## Configuration
```sh
# List git config
git config --list

# Edit global git config
git config --global --edit

# Set default git editor
git config --global core.editor nano
git config --global core.editor vim
git config --global core.editor code --wait
```

---

## Config
```sh
# .gitconfig

[credential]
	helper = osxkeychain
[user]
	email = <email>
	name = <name>
[core]
	editor = nano
[push]
  # Ensure annotated tags
	followTags = true
[alias]
  s = !git status -s
  c = !git commit -m
  ac = !git add --all && git commit -m
  l = !git --no-pager log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

---

## Conventions
> [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

---
## Workflow

### Remote Repository
```sh
# Add remote repository origin
git remote add origin git@github.com:<UserName>/<repository-name>.git
```

### Branch
```sh
# List branches
git branch

# List current user branches
git branch -a

# Create local branch and switch in it
git checkout -b <Branch-Name>

# Switch branch
git checkout <Branch-Name>

# Push local branch to origin
git push origin <Branch-Name>
```

### Log
```sh
# Show a commit log list
git log

# show a one line commit log list
git log --oneline
```

### Tag
```sh
# List tags
git tag

# Add an annotated tag with message
git tag -a "1.0.0" -m "1.0.0"
```

### Push
```sh
# Push with all tags (lightweight and annotated)
git push origin main --tags

# Push with only annotated tags
git push origin main --follow-tags
```

### Submodules
```sh
# Start a submodule
git submodule init

# Check a submodule status
git submodule status

# Add a new submodule
git submodule add <repository-url.git>

# Update and pull repositories for the first time
git submodule update --init --recursive

# Update and pull repositories from remote
git submodule update --recursive --remote
```
