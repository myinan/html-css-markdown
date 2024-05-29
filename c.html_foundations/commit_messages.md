# Commit Messages

## Bad vs. good commits
When it comes to writing commits, it is crucial to know how to write them effectively. Here’s an example of a bad commit message:

```
fix a bug
```
Even though it describes what you did, the message is too vague, which leaves the other developers on your team confused. A good commit message will explain the why behind your changes. In other words, a commit message describes what problem your changes solve and how it solves them.

Effective commits consist of two separate parts: a subject, and a body:

### Subject
A brief summary of the change you made to the project. Note: GitHub has a 72-character limit so we recommend keeping your commits’ subject to within this amount.

### Body
A concise yet clear description of what you did.

Describe the problem your commit solves and how.
Now that we learned the secret to creating a good commit message, let’s try and fix the commit message from earlier:

```
Add missing link and alt text to the company's logo

Screen readers won't read the images to users with disabilities without this information
```

Ahh, that’s better! :) Now, developers can gain a better understanding of this commit message because it does the following:

Provides a subject that specifies your code’s action (e.g., “Add missing link and alt text the company’s logo”)
Contains a body that provides a concise yet clear description of why the commit needed to be made (e.g., “Screen readers won’t read the images to users with disabilities without this information”)
Separates the subject from the body with a new/blank line. This is a best practice we highly recommend following. It makes commit messages easier for other developers to read.

## When to commit

A good way to view a commit is like a “snapshot” of your code at the moment that it was made. That version of your code up to that point will be saved for you to revert back to or look back at.

When writing code, it’s considered best practice to commit every time you have a meaningful change in the code. This will create a timeline of your progress and show that your finished code didn’t appear out of nowhere.

In other words, make a commit if you get a piece of code you are working on to function like you want it to, fix a typo, or fix a bug. As you gain experience, you will develop a better feel for what should be committed!

There will come a time when you are working on a project and you FINALLY get something just right (this would be a good time to commit), and then maybe 30 seconds to a few days later it breaks. You have no idea what you changed, everything looks to be the same and you don’t remember editing that line, but alas, it isn’t working how you want it anymore. You’d be able to go back through your commit history and either revert your code back to the last commit you made when you first got that part working or go back and see what your code looked like at that point in time.

## The seven rules of a great Git commit message

1. Separate subject from body with a blank line
1. Limit the subject line to 50 characters
1. Capitalize the subject line
1. Do not end the subject line with a period
1. Use the imperative mood in the subject line
1. Wrap the body at 72 characters
1. Use the body to explain what and why vs. how

## Basic Git Workflow

[Git Basic Commands CheatSheet](https://www.theodinproject.com/lessons/foundations-git-basics#cheatsheet)

The name “origin” is both the default and the convention for the remote repository.

...for now it is advised to make any changes via your local files then commit and push them using Git commands in your terminal once ready...

### Git Best Practices
Two helpful best practices to consider are atomic commits and leveraging those atomic commits to make your commit messages more useful to future collaborators.

An atomic commit is a commit that includes changes related to only one feature or task of your program. There are two main reasons for doing this: first, if something you change turns out to cause some problems, it is easy to revert the specific change without losing other changes; and second, it enables you to write better commit messages.

### Changing the Git Commit Message Editor

If you are using Visual Studio Code, there’s a way to ensure that if you use git commit without the message flag (-m), you won’t get stuck writing your commit message in Vim.

Changing the default message editor is a good idea in case you accidentally omit the flag, unless you prefer using Vim. There is no downside to changing it, because you will have the option to write your commit messages in the terminal or in the comfort of VS Code.

The following command will set this configuration. Type (or copy & paste) this command into your terminal and hit Enter.

```
git config --global core.editor "code --wait"
```

There will be no confirmation or any output on the terminal after entering this command.

With that done, you can now choose to use either git commit -m <your message here> or git commit to type your message with Visual Studio Code!

To make a commit with Visual Studio Code as the text editor, just type git commit. After you hit Enter a new tab in VS Code will open for you to write your commit message. You may provide more details on multiple lines as part of your commit message. After typing your commit message, save it Ctrl + S (or Mac equivalent) and close the tab. If you return to the command line, you will see your commit message and a summary of your changes.

---

### Knowledge Check

**Q1.** What are two benefits of having well-written commit messages and a good commit history?

**A1.** 1- It makes collaborating with other people easy. 2- It helps you to understand the development process of your project if you come back to it after a couple of months.

**Q2.** How many characters should the subject line of your commit message be?

**A2.** Generally, the subject line of a commit message must be limitted to 50 characters.