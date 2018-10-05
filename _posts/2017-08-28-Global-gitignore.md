---
layout: post
title: Global gitignore
---

```.gitignore``` is the git config file where we can declare files and folder to exclude from git commits, such as log files, build files and system generated files. There is a set of certain files which we may need to exclude from the every project and it is a tedious task to add those files in ```.gitignore``` manually for each project. To avoid this we can create a global ```.gitignore``` file.

Create a ```.gitignore``` file in the home directory

```
touch .gitignore
```

And then declare the global ```.gitignore```

```
git config --global core.excludesfile ~/.gitignore
```

[Here](https://github.com/dev-miche/dotfiles/blob/master/.gitignore) is the example of my global ```.gitignore```.
