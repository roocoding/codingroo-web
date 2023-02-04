---
date: 2023-01-29T23:14:25+10:00
draft: false
title: "Deleting a Git Submodule"
categories: ["Git", "Development"]
---

To delete a submodule from a Git repository, follow these steps:

1. Delete the relevant section from the '.gitmodules' file.
2. Stage the changes to the '.gitmodules' file: `git add .gitmodules`
3. Delete the relevant section from '.git/config'.
4. Run the command `git rm --cached path/to/submodule` (no trailing slash).
5. Commit the changes: `git commit -m "Removed submodule <name>"`
6. Delete the now untracked submodule files: `rm -rf path/to/submodule`
7. Commit the deletion of the submodule files: `git commit -m "Removed files of submodule <name>"`

Note: This will not delete the submodule repository from the remote server.

