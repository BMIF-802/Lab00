# BMIF 802 Tutorial 1: Setting Up Your Coding Environment

In this tutorial, you will set up the main tools used in BMIF 802 and practise working with a shared GitHub repository.

By the end, you should be able to:

- explain the roles of VS Code, conda, Jupyter notebooks, Git, and GitHub;
- create and activate a conda environment;
- open and run a Jupyter notebook in VS Code;
- fork and clone a GitHub repository;
- create a branch;
- commit and push a change using VS Code; and
- create a pull request using GitHub.

## Before the tutorial: install the required software

Complete this section before class when possible. Installation times vary between computers.

### 1. Create a GitHub account

Go to <https://github.com/signup> and create an account, or sign in to an existing account.

Your GitHub username and your work in this repository will be public.

Do not include your student number or other private information in your GitHub username, commits, or pull request.

### 2. Install Git

Git records changes made to the files in a project.

Download Git from:

<https://git-scm.com/downloads>

#### Windows

1. Download **Git for Windows**.
2. Run the installer.
3. Keep the default options.
4. Restart VS Code if it was already open.

#### macOS

1. Open the **Terminal** application.
2. Enter:

   ```bash
   git --version
   ```

3. If macOS asks to install the Command Line Developer Tools, accept the installation.

You can also use one of the installers on the Git download page.

#### Check that Git is installed

Open a terminal and enter:

```bash
git --version
```

You should see a Git version number.

### 3. Install Visual Studio Code

VS Code is the program we will use to edit files, work with Git, and run Jupyter notebooks.

Download it from:

<https://code.visualstudio.com/download>

Run the installer and keep the default options.

### 4. Install Miniconda

Conda creates separate Python environments. An environment lets a project use its own Python version and packages without interfering with other projects.

Download Miniconda from:

<https://www.anaconda.com/download/success>

Choose the Miniconda installer that matches your operating system.

#### Windows

1. Run the downloaded installer.
2. Choose **Just Me** if asked.
3. Keep the default installation location.
4. Finish the installation.
5. Close and reopen VS Code.

#### macOS

1. Run the graphical installer.
2. Keep the default options.
3. Close and reopen VS Code.

#### Check that conda is installed

Open VS Code and select **Terminal > New Terminal**.

Enter:

```bash
conda --version
```

You should see a conda version number.

If the command is not recognized, close and reopen VS Code. On Windows, you can also open **Anaconda Prompt** from the Start menu and enter:

```bash
conda init powershell
```

Then close the prompt and reopen VS Code.

---

# In-class tutorial

The activities below are designed to take approximately 50 minutes when the required software is already installed.

## Part 1: Understand the tools — approximately 5 minutes

| Tool | Purpose |
|---|---|
| **VS Code** | Opens project folders, edits files, runs notebooks, and provides buttons for Git actions. |
| **Python** | The programming language used in this course. |
| **conda** | Creates Python environments and installs packages. |
| **Jupyter notebook** | A document containing runnable code cells, explanatory text, tables, and figures. |
| **Git** | Records the history of changes to project files. |
| **GitHub** | Stores Git repositories online and supports collaboration. |

Some important Git and GitHub terms are:

- A **repository** is a project folder tracked by Git.
- A **fork** is your own GitHub copy of someone else's repository.
- A **clone** is a repository copied from GitHub onto your computer.
- A **commit** is a saved checkpoint in the repository's history.
- A **push** uploads your local commits to GitHub.
- A **pull** downloads changes from GitHub to your computer.
- A **pull request** asks the owner of another repository to review and accept your changes.

The workflow used today is:

```text
Course repository on GitHub
          |
         fork
          v
Your copy on GitHub
          |
         clone
          v
Your copy on your computer
```

## Part 2: Install useful VS Code extensions — approximately 5 minutes

Select the **Extensions** icon on the left side of VS Code. It looks like four blocks.

Search for and install:

| Extension | Publisher | Purpose |
|---|---|---|
| **Python** | Microsoft | Runs Python and helps select Python environments. |
| **Jupyter** | Microsoft | Opens and runs Jupyter notebooks. |
| **GitHub Pull Requests** | GitHub | Adds GitHub sign-in and pull-request tools to VS Code. |

VS Code already includes basic Git support, so no additional Git extension is required.

The GitHub Pull Requests extension is useful, but the pull request in this tutorial will be created on the GitHub website.

## Part 3: Create a conda environment — approximately 8 minutes

We will create an environment named `bmif802`.

1. In VS Code, select **Terminal > New Terminal**.
2. Enter the following command:

   ```bash
   conda create --name bmif802 python=3.12 numpy pandas matplotlib ipykernel
   ```

3. Conda will display the packages it plans to install. Enter `y` when asked to continue.
4. Activate the environment:

   ```bash
   conda activate bmif802
   ```

5. Check the Python version:

   ```bash
   python --version
   ```

You should see Python 3.12.

### What the command installed

- `python` is the programming language.
- `numpy` supports numerical calculations.
- `pandas` works with table-like datasets.
- `matplotlib` creates figures.
- `ipykernel` allows the environment to run Jupyter notebook cells.

You will normally activate the environment whenever you work on BMIF 802 material:

```bash
conda activate bmif802
```

## Part 4: Open a blank Jupyter notebook — approximately 5 minutes

This short activity checks that VS Code can use the new environment.

1. Open the Command Palette:
   - Windows/Linux: `Ctrl + Shift + P`
   - macOS: `Command + Shift + P`
2. Search for **Jupyter: Create New Blank Notebook**.
3. Near the upper-right corner of the notebook, select **Select Kernel**.
4. Choose **Python Environments**.
5. Select `bmif802`.
6. In the first cell, enter:

   ```python
   print("Hello, BMIF 802!")
   ```

7. Select the triangular **Run Cell** button.

The text should appear below the cell.

A **cell** is one section of a notebook. A **kernel** is the Python process that runs its code.

Close the notebook when finished. You do not need to save it.

## Part 5: Fork the course repository — approximately 4 minutes

A fork is your own GitHub copy of this repository.

1. Return to the GitHub page containing this README.
2. Select **Fork** near the upper-right corner.
3. Confirm that the owner is your GitHub account.
4. Keep the existing repository name.
5. Select **Create fork**.

GitHub will open your fork when it is ready.

Do not download the repository as a ZIP file. A ZIP file does not include the Git workflow used in this tutorial.

## Part 6: Clone your fork using VS Code — approximately 5 minutes

Cloning creates a copy of your fork on your computer.

### Copy the address of your fork

1. On the GitHub page for **your fork**, select the green **Code** button.
2. Select **Local**, followed by **HTTPS**.
3. Select the copy button beside the repository address.

### Clone it in VS Code

1. Return to VS Code.
2. Open the Command Palette.
3. Search for and select **Git: Clone**.
4. Paste the address copied from your fork.
5. Choose a location on your computer.
6. When cloning finishes, select **Open**.
7. If VS Code asks whether you trust the authors, select **Yes, I trust the authors**.

A folder such as `Documents/BMIF802` is a suitable location. Avoid placing the repository in OneDrive or iCloud when possible.

## Part 7: Create a branch — approximately 3 minutes

A branch lets you make a change separately from the repository's main branch.

1. Find the current branch name in the lower-left corner of VS Code. It will probably say `main`.
2. Select the branch name.
3. Select **Create new branch**.
4. Name the branch:

   ```text
   introduction-YOUR-GITHUB-USERNAME
   ```

For example:

```text
introduction-alexsmith
```

Confirm that the new branch name appears in the lower-left corner.

## Part 8: Create `me.txt` — approximately 4 minutes

1. In the VS Code Explorer, select the **New File** button.
2. Name the file:

   ```text
   me.txt
   ```

3. Add the following information:

   ```text
   Name: Your preferred name
   Preferred pronouns: Your preferred pronouns
   Favorite midnight snack: Your favorite midnight snack
   ```

For example:

```text
Name: Alex
Preferred pronouns: they/them
Favorite midnight snack: Popcorn
```

You may write `prefer not to say` for any item you do not want to post publicly.

Save the file:

- Windows/Linux: `Ctrl + S`
- macOS: `Command + S`

## Part 9: Commit and push using VS Code — approximately 6 minutes

### Review the change

1. Select the **Source Control** icon on the left side of VS Code.
2. Under **Changes**, select `me.txt`.
3. Confirm that the file contains only the information you intended to share.

### Stage the file

Move your pointer over `me.txt` and select the `+` button.

Staging tells Git to include the file in the next commit.

### Commit the file

1. In the message box, enter:

   ```text
   Add my introduction
   ```

2. Select **Commit**.

A commit has now been saved on your computer.

### If Git asks for your name and email

Open **Terminal > New Terminal** and enter:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Replace the example values with your information, and then try committing again.

You can use the GitHub no-reply email listed in your GitHub email settings if you do not want your personal email stored in public commit information.

### Push the branch

Select **Publish Branch** or **Sync Changes** in VS Code.

Sign in to GitHub if prompted. Pushing uploads your commit from your computer to your fork on GitHub.

## Part 10: Create a pull request — approximately 5 minutes

1. Open your fork on GitHub.
2. GitHub may show a banner for your recently pushed branch. Select **Compare & pull request**.
3. If the banner is not shown:
   - select **Pull requests**;
   - select **New pull request**;
   - select **compare across forks** if necessary;
   - set the base repository to the course repository and the base branch to `main`;
   - set the head repository to your fork and the compare branch to your introduction branch.
4. Use the following title:

   ```text
   Tutorial 1 introduction: YOUR-GITHUB-USERNAME
   ```

5. In the description, enter:

   ```text
   One tool that was new to me:
   One question I still have:
   ```

6. Leave **Allow edits by maintainers** enabled.
7. Select **Create pull request**.

Do not merge the pull request yourself.

## Final instructor-led activity — approximately 5 minutes

Stop here and wait for the instructor.

Keep the following open:

- your pull request in a web browser; and
- the cloned repository in VS Code.

The instructor will provide the final steps.

---

## Troubleshooting

### VS Code says Git is not installed

Install Git from <https://git-scm.com/downloads>, close all VS Code windows, and reopen VS Code.

### `conda` is not recognized

Close and reopen VS Code.

On Windows, open **Anaconda Prompt** and enter:

```bash
conda init powershell
```

Then close the prompt and reopen VS Code.

### The `bmif802` environment does not appear as a notebook kernel

1. Confirm that the environment was created:

   ```bash
   conda env list
   ```

2. Activate it:

   ```bash
   conda activate bmif802
   ```

3. Close and reopen the blank notebook.
4. Select **Select Kernel** again.

### I cloned the course repository instead of my fork

Return to GitHub, open your fork, copy its HTTPS address, and clone it into a new local folder.

### I committed on `main`

Stop before making another commit and ask the instructor for help. Your work is not lost.

### Push repeatedly asks me to sign in

Select the Accounts icon in the lower-left corner of VS Code, sign out of GitHub, and sign in again. Complete the authorization steps in your browser.

---

## Completion checklist

- [ ] Git, VS Code, and Miniconda are installed.
- [ ] The Python, Jupyter, and GitHub Pull Requests extensions are installed.
- [ ] The `bmif802` conda environment was created.
- [ ] A blank notebook ran using the `bmif802` kernel.
- [ ] The course repository was forked.
- [ ] The fork was cloned.
- [ ] An introduction branch was created.
- [ ] `me.txt` was committed and pushed.
- [ ] A pull request was opened.
- [ ] The final instructor-led activity was completed.
