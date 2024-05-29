# Git Basics

## Basic Git Workflow

[Git Basic Commands CheatSheet](https://www.theodinproject.com/lessons/foundations-git-basics#cheatsheet)

The name “origin” is both the default and the convention for the remote repository.

...for now it is advised to make any changes via your local files then commit and push them using Git commands in your terminal once ready...

### Git Best Practices
Two helpful best practices to consider are atomic commits and leveraging those atomic commits to make your commit messages more useful to future collaborators.

An atomic commit is a commit that includes changes related to only one feature or task of your program. There are two main reasons for doing this: first, if something you change turns out to cause some problems, it is easy to revert the specific change without losing other changes; and second, it enables you to write better commit messages.

---

## Knowledge Check
**Q1.** How do you create a new repository on GitHub?

**A1.** We can create a new repository on Github by clicking the "new repository" button on the website.

**Q2.** How do you copy a repository onto your local machine from GitHub?

**A2.** To "clone"(copy) a repo onto our local machine from Github, we need to navigate to the page of that repository on GitHub. After clicking the "code" button on the page, we copy the "SSH" key. After that we use "**git clone**" command on our terminal. The command we type on terminal will look like this: "git clone git@github.com:USER-NAME/REPOSITORY-NAME.git"

**Q3.** What is the default name of your remote connection?

**A3.** "origin".

**Q4.** Explain what origin is in git push origin main.

**A4.** It's the name of our remote repository on GitHub.

**Q5.** Explain what main is in git push origin main.

**A5.** It's name of the branch that we will push to on the remote repository.

**Q6.** Explain the two-stage system that Git uses to save files.

**A6.** When using Git, the files which we have made changes to on our directory are in **modified** state. We can move the files we have modified to the staging area, then which the state of those files will become **staged**. We can commit the files we have staged. Then those files will be **committed**.

**Q7.** How do you check the status of your current repository?

**A7.** With the command "git status".

**Q8.** How do you add files to the staging area in git?

**A8.** Use "git add . " to add all the files in the current working directory to the staging area, use "git add <file-name.extension>" to add a particular file into the staging area.

**Q9.** How do you commit the files in the staging area and add a descriptive message?

**A9.** git commit -m "the message"

**Q10.** How do you push your changes to your repository on GitHub?

**A10.** With the command "git push" or "git push origin main" to be more spesific.

**Q11.** How do you look at the history of your previous commits?

**A11.** With the command "git log".



