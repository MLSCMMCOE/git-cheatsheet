<div style="text-align:center"><img src="https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/without_background.png" height="600" width="600" /></div>
## 10. Git and Github

If you're a beginner, you might think that these two terms mean the same thing - but they're different.

### What is git?

Git is a version control system which lets you track changes you make to your files over time. Git will create a backup of your files on command, and let you go back to every backup you create (like a time traveling machine). You can also make a complete copy of your files, make changes to that copy, and then merge these changes to the original copy.
For example, you could be working on a website's landing page and discover that you do not like the navigation bar. But at the same time, you might not want to start altering its components because it might get worse.

With Git, you can create an identical copy of the entire website code (called a branch) and play around with the navigation bar. Then, when you are satisfied with your changes, you can merge the copy to the original file.

You don't necessarily need to merge that copy, you can keep it entirely separate and make something different.

You are not limited to using Git just for source code files - you can also use it to keep track of text files or even images. This means that Git is not just for developers - anyone can find it helpful.

*Wow that sounds cool, how can I actually do it?*

Well to get started initialize your project, simply run

``` bash
git init
```

This will tell Git to get ready to start watching your files for every change that occurs. It looks like this:

![initialize](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/init.png)

*Ah okay so my files are tracked now? All good, right?*

Not really,

Git does not immediately start tracking every file and folder you give it. It will initially not track any files. git considers your files in an untracked state.

You will need to tell git what files to track using **add** command

### How to add files in Git

To do that, we use this command

```bash
git add <filename>
```

After this git will add the file with the file name you provide it
If you want to add a file named **about.txt**, you will use

```bash
git add about.txt
```

But what if I want to add all files in the folder? Do I keep telling git each and every file??

No, you can tell git to add everything using

```bash
git add .
```

You can check it by using

``` bash
git status
```

It will tell you status of your files

This will put your files from **untracked** to **staged** state. '.' (dot) is short form for current directory.

*Oh no I accidentally added a file that I didn't mean to, what do I do?*
git on the rescue, just tell git to reset

```bash
git reset HEAD <filename>
```

### git commit

Now, about creating that backup of your files, you need to commit the files that you added using

```bash
git commit -m "commit message"
```

![commit](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/commit.png)
When you commit your files git creates a kind of checkpoint, now git has made a backup of your files, you can freely go wild and make breaking changes to your code. In the end you can just revert to this backup or any prior committed changes you made whenever you want.

There are different ways to revert to the latest committed state. You could use

``` bash
git stash
```

This will not only revert but also store your changes into a temporary stash

### Branches

Let's take a look at how to create those copies of your entire code using branches
To create a new branch, run this command:

``` bash
git checkout -b <branch name>
```

![commit](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/branch.png)
This will create a new branch, a complete copy of your code.
It will also replace your current folder to show you contents of this branch.

*Okay, but what happened to my original copy? Is it gone?*

Nope, your original copy is under the branch name master, when you initialize git repository it creates a master branch and uses it as default

You can switch to your master branch using

```bash
git checkout master
```

Notice it's the same command that we used to create a new branch, the only difference is that we are not giving it -b. As you guessed correctly, the -b is used to tell git to create a new branch  

*I made a cool change in the test branch, tested a few things and I have decided to have those changes into the master branch.*

Simply checkout master branch and tell git to merge:

```bash
git merge test
```

It will merge those changes into the master branch

![commit](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/merge.png)

### What is Github

GitHub is an online hosting service for Git repositories. Imagine working on a project at home and while you are away, maybe at a friend's place, you suddenly remember the solution to a code error that has kept you restless for days.

You cannot make these changes because your PC is not with you. But if you have your project hosted on GitHub, you can access and download that project with a command on whatever computer you have access to. Then you can make your changes and push the latest version back to GitHub.In summary, GitHub lets you store your repo on their platform. Another awesome feature that comes with GitHub is the ability to collaborate with other developers from any location.Now that we have created and initialized our project locally, let's push it to GitHub.If you are a beginner, you will come across some new terms like push, commit, add, and so on - but do not be overwhelmed by them. With some practice you will be able to remember these terms and what they do.

### How to push a repository to GitHub

Step 1 - Create a GitHub account

Step 2 - Create a repository on github

To push your current repository to github you will need to authenticate with your github account

You can follow authentication steps over here:
<a
      href="https://docs.github.com/en/get-started/quickstart/set-up-git#setting-up-git"><https://docs.github.com/en/get-started/quickstart/set-up-git#setting-up-git>
</a>

You have an option to change your default branch name when you are uploading your repository the first time.
You can do that by

```bash
git branch -M <branch name>
```

In Git, "origin" is typically the name of the remote repository where you want to store your local repository changes. When you run the command `git remote add origin <remote repository URL>`, you are telling Git to add a new remote repository with the name "origin".

Let's say you have created a new Git repository on GitHub, and the URL of the repository is `https://github.com/yourusername/your-repo.git`.

To add this remote repository to your local Git repository, you can run the following command:

```bash
git remote add origin https://github.com/yourusername/your-repo.git
```

This command tells Git to add a new remote repository with the name "origin" and the URL `https://github.com/yourusername/your-repo.git`. Once you have added the remote repository, you can push your local changes to the remote repository using the `git push` command.

Now make sure you have added and committed your files using git
Once you are done use the command:

```bash
git push origin <branch-name>
```

Here you tell git that you want to push these changes to your remote that you named as origin in the previous steps and you tell git that you would like to push the given branch <branch-name\>

You can check your github repository and you will see your files there.

![commit](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/push.png)

### How to pull changes

Suppose you are working with a friend on a project and you are collaborating on github,
Your friend makes changes and pushes them to the github repository, but you don't have those changes on your computer.
To update the changes you can use:

```bash
git pull origin <branch-name>
```

This will update changes made to the branch <branch-name\>

### How to Clone a repository

Suppose you see someone's code you like and want to use it and see it run for yourself. git provides a easy way to have a repository cloned for you

```bash
 git clone REPOSITORY_HTTPS_URL
 ```

This command downloads the remote repository into your local computer in a folder with the name of the repository.

![commit](https://github.com/MLSCMMCOE/git-cheatsheet/blob/main/pull.png)

<br>

If you have followed up to this point then congratulations, you are good to go.You can now use Git in your projects no matter what programming language you are using. But this is not the end, git is much more than this. These steps you saw are the basics that you will be using most commonly, but we encourage you to find and learn more about features of git using the resources below.
