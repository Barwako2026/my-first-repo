\# User Manual Procedure: Setting Up a GitHub Repository and Making a First Commit



\## Prerequisites

\- A computer with internet access

\- A GitHub account

\- Git installed locally (check with `git --version`)

\- PowerShell, Terminal, or another command-line application

\- Basic familiarity with typing commands and navigating folders



\## Steps



1\. \*\*Create a new repository on GitHub.\*\* Click the "+" icon in the top-right corner of GitHub, select "New repository," give it a name (e.g. `my-first-repo`), leave "Add a README file" unchecked, then click "Create repository."

&#x20;  \*Expected result:\* GitHub shows the "Quick setup" page for an empty repository.



2\. \*\*Copy the repository's HTTPS URL.\*\* On the "Quick setup" page, make sure the "HTTPS" tab is selected, then copy the URL shown (e.g. `https://github.com/username/my-first-repo.git`).

&#x20;  \*Expected result:\* The URL is copied to your clipboard.



3\. \*\*Open PowerShell and create/navigate to a project folder.\*\*



mkdir my-first-repo

cd my-first-repo



&#x20;  \*Expected result:\* The prompt shows `PS C:\\Users\\YourName\\my-first-repo>`.



4\. \*\*Create a README file.\*\*



echo "# my-first-repo" >> README.md



&#x20;  \*Expected result:\* `README.md` appears in the folder.



5\. \*\*Initialize Git in the folder.\*\*



git init



&#x20;  \*Expected result:\* Terminal shows `Initialized empty Git repository in .../my-first-repo/.git/`.



6\. \*\*Stage the README file.\*\*



git add README.md



&#x20;  \*Expected result:\* Running `git status` shows README.md staged in green.



7\. \*\*Commit the change.\*\*



git commit -m "first commit"



&#x20;  \*Expected result:\* Terminal shows `\[master (root-commit) <hash>] first commit`.



8\. \*\*Rename the branch to main.\*\*



git branch -M main



&#x20;  \*Expected result:\* No error output; the branch is now named `main`.



9\. \*\*Link the GitHub remote.\*\*



git remote add origin https://github.com/username/my-first-repo.git



&#x20;  \*Expected result:\* No output on success.



10\. \*\*Push the commit to GitHub.\*\*

git push -u origin main

&#x20;   \*Expected result:\* Terminal shows upload progress ending in `\* \[new branch] main -> main` and `Branch 'main' set up to track 'origin/main'`.



11\. \*\*Verify on GitHub.\*\* Refresh the repository page in your browser.

&#x20;   \*Expected result:\* `README.md` is now listed in the repository instead of the "Quick setup" screen.



\## Screenshot

Screenshot 1: Terminal window showing the full command sequence from `mkdir` through `git push -u origin main`, ending in the success message `\* \[new branch] main -> main` and `Branch 'main' set up to track 'origin/main'`, confirming the push completed.



\## Troubleshooting

If `cd Desktop` (or any folder name) fails with an error like "Cannot find path... because it does not exist," the folder isn't present at that default location on your machine. Run `mkdir foldername` to create the folder first, then `cd` into it, or navigate to wherever you actually want the project stored.

