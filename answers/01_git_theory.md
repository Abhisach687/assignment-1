# Part A — Git & project foundations

## Git fundamentals

### 1. Git has three places a change can live: the working directory, the staging area, and the repository. Describe each, and explain what you would lose if the staging area did not exist.
<strong>Answer 1: </strong> \
<strong> Working directory </strong> consists the files that are currently opened and worked on. \
<strong> Staging area</strong>, which is also known as the index, holds the exact copies of files that are chosen for the next commit. \
<strong>Repository</strong> includes of the committed files and history of those previously commited files, found normally in the .git folder. \
If Git did not have a staging area, it would be unclear which changes should go in the commit. All the unfinished and unrealted changes in the \
working directory would get commited even if that was not that intention to begin with. 

### 2. `git init` and `git clone` both leave you with a Git repository. Explain what each one actually does, and give a situation where each is the right choice.
<strong>Answer 2: </strong> \
The `git init` command sets up the repository structure within a new or existing directory/folder without committing pre-existing files to the repository. The `git init` command can be used when the user wishes to begin versioning his/her projects. On the other hand, the `git clone` command creates a local copy of an existing repository. This command will clone the entire repository history and check out the default branch and set up a remote called `origin`.

### 3. What does a commit store, and why is "committing" not the same as "saving a file"? Why is Git much less useful if user.name and user.email are unset or wrong?
<strong>Answer 3: </strong> \
A commit is a snapshot of the project at the moment of time the commit was made. A commit stores a host of information including parent commit/s, commit message, name of the author, commiter's email and the exact timestamp of the commit. Whereas, saving a file only saves it locally in the working directory. In contrast, commiting creates a permanent record in the Git history that can viewed, compared and restored later. \
If an incorrect user.name and user.email settings are set or when name and email are unset then git can no longer identify the person who made the commit. This makes hard to track who changed what and team-members no longer have the ability to contact the person who made the commit in case something goes wrong. Hence, why Git will not allow commits until correct email and name are configured. 

### 4. `git status` , `git log` , and `git diff` answer three different questions. State the question each one answers, and describe a moment in your workflow where you would reach for each.
<strong>Answer 4: </strong> \
`git status` tells the user “What is the current state of thier working directory and staging area?”, so the user can use it prior to committing in order to review staged, unstaged, and untracked files. \
`git log` tells the user “What commits have resulted in this version?” i.e "What commits exist in the project history?", which is useful in determining the history of a bug or feature’s appearance. \
`git diff` shows what changes have been made to the working directory, however, have not been added to the staging area. It shows what content is different in the working directory as compared to the staged changes.

### 5. Explain what makes a commit message good. Why is "update" a genuine problem for a team six months later, and when is it worth writing a message body rather than just a summary line?
<strong>Answer 5: </strong> \
A good commit message should be brief, however, clearly communicate what exactly changed. For example, "Fix login crash on an empty email." A clear commit message helps people understand the exact purpose of the change even after a long while. The commit message body should only be added if and only if more explanation is needed such as explaining a reason for change in detail or any limitations one has to be mindful of which cannot be communicated in a short commit message.

## Remotes and the everyday workflow

### 6. Explain the relationship between your local repository and `origin`. What do `push` and `pull` each move, in which direction, and why is pulling before pushing the habit to build?
<strong>Answer 6: </strong> \
 The local repository holds the local history whereas, origin is the default name used for the remote repository address that has been configured. When you do a push, you basically tell your remote repository to update its reference for a particular branch with your required local commits and objects, but not with your uncommitted changes. A pull involves downloading the remote history into your local repository and then merging the particular remote branch with your current branch according to your chosen configuration. It is better to pull before pushing in order to merge other people's changes. This helps prevent conflicts and ensures your push includes of the lastest version of the project. 

 ### 7. git fetch and git pull are not the same command. What is the difference, and when would youdeliberately choose fetch?
 <strong>Answer 7: </strong> \ 
 A `git fetch` downloads latest changes from a remote repository, however, it does not merge them with the local branch. It allows one to check other team members' changes before deciding what to do. `git pull` on the other hand, does both fetching and merging (or rebasing) automatically. Hence, it downloads the changes and adds them to the current branch automatically. I'd deliberately use `git fetch` if my goal is to review changes first. Similarly, I'd use `git pull` if I'm ready to update my local branch.

 ## Branching, merging, pull requests

### 8. A branch in Git is often described as "just a pointer." Explain what that means, and explain concretely what goes wrong on a team when everyone commits directly to `main`.
 <strong>Answer 8: </strong> \
A branch does not copy the entire project files, it just points to the commit/s made. When a user checks out to a branch, new commits are tracked in that branch and other branches remain unaltered. Branching allows developers to test, understand and reason about their code and compare changes before pushing everything to main brach. If everyone were to push everything into the main branch, incomplete and error-prone code would make it to the `main` branch and cause problems for the whole project.

### 9. A merge conflict happens when two branches change the same lines of the same file. Explain why Git cannot resolve this automatically, what the <<<<<<< , ======= , >>>>>>> markers mean, and what you must do to finish the merge.
 <strong>Answer 9: </strong> \
When two braches have changes made to the same file, Git cannot automatically combine those changes because two branches have different changes in the same part of the file. This phenomemon causes a conflict. This conflict also occurs when one branch has the file deleted and other branch has the same file changed or altered. In such cases, Git can detect the changes however, it cannot decide which changes to keep. \

During such cases and conflicts, Git uses markers such as `<<<<<<<` and `=======`. \
`<<<<<<<` shows changes from the current branch. \
`=======` separates the two different versions. 
`>>>>>>>` shows changes coming from the conflicting other branch. \
To resolve such a conflict, developer must open the file and deicide which changes to keep (or combine both), remove conflict markers and save the file. After ensuring that the code works correctly, the developer (or whoever is incharge of handing such cases), should add the resolved files using `git add` and complete the merge using `git commit` or `git merge --continue`.

### 10. You could merge a branch locally with git merge and push. What does opening a Pull Request add that a local merge does not? What belongs in a PR description?
 <strong>Answer 10: </strong> \
To make the changes directly in the local Git Repository directly, a local merge can be done. However, in on platforms like Github, Gitlabs and BitBucket; where many developers work simultaneously on a project remotely, developers are allowed to suggest changes, review changes, discuss them, review the code differences and review automated tests bofore adding those changes in the main branch using Pull Requests. \
A repository requires approvals and successful tests before a PR can be merged. A good PR request is one which explains why the changes were made, how the changes were tested and any potential risks and limitations. They should include related issue links and screenshots if they help explain the changes. \
\
In short, a local merge only combines the code in your computer. A PR creates a shared place where the team can review the code, discuss the changes, run automated tests and track the reasons for change. 

## 11. Issues

### 11. Explain the purpose of labels and assignees on an Issue, and what Fixes #12 in a merged PR does. Why is linking work to Issues better than closing them by hand?
 <strong>Answer 11: </strong> \
When you wish to assign Issue by category such as a bug or a feature request, then labels are the goto. <strong>Labels</strong> allow for searching, filtering and manging related tasks easier. <strong>Assignees</strong> display the exact person/s responsible for working on an issue. This allows for someone being assigned to handle the task and avoids confusion. <strong>`Fixes #12` in a Pull Request</strong> allows the Issue Number 12 to be connected to the Pull Request. When this PR is merged with the main branch, Issue #12 also automatically closes successfully at the same instance. \

Why is linking Issues better than closing them manually? This is because linking allows for a clear connection between problem, discussion, code changes and the solution.Stakeholders/developers can easily understand why a change was made, it eliminates the problem of forgetting to close an issue after the completion of the work and it overall creates a better history of the project for the future reference. 

## Project structure, environments, secrets

### 12. Why should .gitignore be one of your first commits? If a file is already tracked, does adding it to .gitignore stop Git from tracking it — and if not, what do you do instead?
 <strong>Answer 12: </strong> \
`.gitignore` should be on of the first commit for the precise reason that it tells Git which files should not be added to the repository. It helps not to commit unnecessary and sensitive files such as `.env` secret keys or huge package installations, personal setting et cetera. \

If a file is already tracked, does adding it to .gitignore stop Git from tracking it — and if not, what do you do instead? If a file was already commited, .gitignore does not stop Git from tracking it, hence why, in such cases, `git rm --cached filename` command should be run followed by making necessary changes in .gitignore and finally commiting those changes. Doing this ensures that the file stays locally in your computer but is no longer tracked by git. 

### 13. Explain the difference between .env and .env.example , and why they get opposite treatment. If a real API key was committed three weeks ago, why is deleting it in a new commit not a fix, and what should actually be done?
 <strong>Answer 13: </strong> \
`.env` file stores real configuation values and secrets such as database information, password and API keys. In contrast, `.env.example` contains of only the placeholders for these values as such leaks no secrets that should stay hidden. \
If in case, a real API key got commited, simply deleting the key in a new commit is not enough as old commit history might still contain it. The correct step is to revoke the leaked key and use a new key instead. If needed, another way is to remove the secret from the git history using `git-filter-repo` however, revoking the leaked key is the ideal solution.

### 14. What problem do a virtual environment and requirements.txt solve together? Why is venv/ itself never committed, when requirements.txt always is?
 <strong>Answer 14: </strong> \
Virtual environment/s such as `venv` create a separate space for the project's package dependencies to be installed without polluting the global space. `venv` allows to only install packages required by the specific project and we can have separate virtual enviroments for separate projects so that the dependencies of each project/s do not affect each other. `requirements.txt` stores all the required packages needed by the project so that other developers can directly install all the packages based on the file and get up and running with the project quickly. \
Why is venv/ itself never committed, when requirements.txt always is? It is because `venv` consists of machine specfic pakages and files hence it makes little sense to commit that directory. It is also large in size and can be created easily from requirements.txt file. Hence, why we commit requirements.txt but not venv.

### 15. Explain what `git push --force` does to a shared branch and whose work it can destroy. How does `--force-with-lease` behave differently, and why is that safer?
 <strong>Answer 14: </strong> \
`git push --force` forces the replacement of the remote branch history with the local branch. It can delete important history and other people's work. `git push --force` is risky on shared branches. \
`git push --force-with-lease` is a safer alternative. It checks if someone else has updated the remote branch before replacing it. If there are new changes in the remote branch that the developer isn't simply aware of then Git stops the push when it comes to `--force-with-lease`. \
`--force-with-lease` is to be preferred over `--force` because it simply reduces the chances of accidentally overwriting other teammates' work. However, it still does change the history hence it should be deployed carefully. 