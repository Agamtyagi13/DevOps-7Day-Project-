Task 2 – GitHub Repository Setup
Objective

The objective of Task 2 is to create a GitHub repository for the DevOps project, configure the required Git branches, maintain meaningful commit history, and push the project files to GitHub.

Requirements

The repository should contain:

README.md
main branch
develop branch
feature/devops branch
Meaningful commit messages
Project files pushed to GitHub
1. GitHub Repository

A GitHub repository was created for the DevOps project.

The local project was initialized as a Git repository and connected to the GitHub repository.

The repository provides a central location for storing and managing the project source code and configuration files.

2. README

A README.md file was added to the repository.

It provides basic information about the project and can be updated as additional DevOps components are added.

3. Branching Strategy

The required branches were created:

main
develop
feature/devops
main

The main branch represents the stable version of the project.

develop

The develop branch is used for development and integration work.

feature/devops

The feature/devops branch is used for implementing DevOps-related work.

4. Commit History

Project changes were committed using meaningful commit messages.

The commit history was checked to verify that changes were properly recorded.

Examples of meaningful commits:

Initial project setup
Add README
Add DevOps configuration
Update project files
5. Push Project to GitHub

The local repository was connected to GitHub and the required branches and project files were pushed to the remote repository.

The GitHub repository was then verified to ensure that the files and branches were available.


## COMMAND USED
git init

git status

touch README.md

git add .

git commit -m "Initial project setup"

git branch -M main

git checkout -b develop

git checkout -b feature/devops

git branch

git remote add origin <GITHUB_REPOSITORY_URL>

git remote -v

git checkout main
git push -u origin main

git checkout develop
git push -u origin develop

git checkout feature/devops
git push -u origin feature/devops

git branch -a

git log --oneline --all --graph

git status