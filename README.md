# Getting-Started-with-Github-and-R
A brief tutorial on using Github with R and Rstudio. Note: the tutorial closely follows [Happy Git with R](https://happygitwithr.com/index.html). The instructions below assume the following:

1. You have [R](https://cloud.r-project.org/) and [RStudio](https://www.rstudio.com/products/rstudio/) installed

2. You have created a [Github account](https://github.com/join)

After ensuring the above, it is important to check whether you have Git installed. See below.

## What is Github?
Github is a hosting service for Git. A hosting service provides an online repository for your Git-based projects on the internet. It allows other people to see your stuff, sync up with you, and perhaps even make changes. It's a lot like Dropbox but much, much better.

## What is Git?
Git is a [version control system](https://en.wikipedia.org/wiki/Version_control). Its original purpose was to help groups of developers work collaboratively on big software projects. Git manages the evolution of a set of files – called a repository – in a logical, highly structured way. As explained by the very helpful [Happy Git with R](https://happygitwithr.com/big-picture.html), a version control system (i.e., Git) can be thought of as analogous to the “Track Changes” features from Microsoft Word. More importantly, it is helps you maintain stable versions of your model or data analysis, since the R version and packages used are kept 'as is' when you initiate the project.

# Install Git
The easiest way to download Git is directly. You can find the latest stable version of Git on the website: https://git-scm.com/downloads

You can also check if you have Git already installed by writing the following in your shell:
```{git}
which git
git --version
```
This shows where your git files may be located.

### Note: Mac users
If you have already installed XCode during your R installation (which is required) first check that you have Git (you probably do):
```{git}
git --version
git config
```
Accept the offer! Click on “Install”.

Note: after upgrading macOS, you might need to re-do the above and/or re-agree to the Xcode license agreement. 

## Configure Git
In your terminal, write the following, one at a time:
```{git}
git config --global user.name 'Jane Doe'
git config --global user.email 'jane@example.com'
git config --global --list
```
**Note: substitute your name and the email associated with your GitHub account!**

## Create Security Protocol
Here we have to set up [SSH keys](https://en.wikipedia.org/wiki/Ssh-keygen). We advise the following instructions for beginners. If you are more advanced and want to follow the recommended Github security protocols, follow these instructions: https://happygitwithr.com/ssh-keys.html#option-2-set-up-from-the-shell 

To check, open RStudio and go to Tools > Global Options…> Git/SVN. If you see something like ~/.ssh/id_rsa in the SSH RSA Key box, you definitely have existing keys.If nothing shoes up, go to your terminal and type the following:
```{git}
ls -al ~/.ssh/
```
If you are told ~/.ssh/ doesn’t exist, you don’t have SSH keys!

### Create an SSH key pair
Go to Tools > Global Options…> Git/SVN > Create RSA Key…

RStudio then prompts you for a passphrase. It is optional, but also a best practice. Configuring your system for smooth operation with a passphrase-protected key introduces more moving parts. If you’re completely new at all this, skip the passphrase (or use HTTPS!) and implement it next time, when you are more comfortable with system configuration. I did not use a passphrase at first, but I do now, and record it in a password manager.

Click “Create” and RStudio will generate an SSH key pair, stored in the files ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub.

Note: **do not use HTTPS** as Github no longer supports HTTPS authentication.

# Connect Git and GitHub
This section will ensure that your computer is able to 'talk' to Github, using Git. If it doesn't, you have likely made an error during installation and configuration.

## Make a repo on GitHub
Go to https://github.com and make sure you are logged in.

Near “Repositories”, click the big green “New” button. Or, if you are on your own profile page, click on “Repositories”, then click the big green “New” button.

How to fill this in:
- Repository template: No template.
- Repository name: myrepo or whatever you wish (we’ll delete this soon).
- Description: “Repository for testing my Git/GitHub setup” or similar. It’s nice to have something here, so you’ll see it appear in the README.
- Choose 'Public'.
- Initialize this repository with: Add a README file.

Click the big green button that says “Create repository”.

Now click the big green button that says “<> Code”.

Copy a clone URL to your clipboard. **Note: since we're using an SSH protocol, make sure to copy the SSH URL**.

## Clone the test GitHub repository to your computer via RStudio
In RStudio, start a new Project:
- File > New Project > Version Control > Git. In “Repository URL”, paste the URL of your new GitHub repository. It will be something like this 
```{git}
https://github.com/janedoe/myrepo.git.
```
- Don't see an option to get the Project from Version Control? Restart RStudio and try again. Still no luck? See [chapter 13](https://happygitwithr.com/rstudio-see-git.html) of Happy Git with R for trouble shooting Git and RStudio

- Accept the default project directory name, e.g. myrepo, which coincides with the GitHub repo name.
- Take charge of – or at least notice! – where the Project will be saved locally. A common mistake is to have no idea where you are saving files or what your working directory is.
- Check “Open in new session”, as that’s what you’ll usually do in real life.
- Click “Create Project”.

You should find yourself in a new local RStudio Project that represents your test repo on GitHub. This should download the README.md file from GitHub. Look in RStudio’s file browser pane for the README.md file.

## Make local changes, save, commit
From RStudio, modify the README.md file, e.g., by adding the line “This is a line from RStudio”. Save your changes.

But how can we update these changes on Github?
- Click the “Git” tab in upper right pane.

![Git button](img/git_button.png)

- Check “Staged” box for README.md.
- If you’re not already in the Git pop-up, click “Commit”.
- Type a message in “Commit message”, such as “Commit from RStudio”.
- Click “Commit”.

## Push your local changes online to GitHub
Click the green “Push” button to send your local changes to GitHub.

And if everything has been set up correclty, you should see the new new changes in your repository!