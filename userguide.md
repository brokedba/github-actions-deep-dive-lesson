# User Guide

## Install

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### Set Up a Workflow to Run on the Runner

1.  In your GitHub repository, select **Code** in the top menu bar.
2.  Below **Quick setup**, select **creating a new file**.
3.  In the first **Name your file** text box, enter `.github/`.
4.  In the second **Name your file** text box, enter `workflows/`.
5.  In the third **Name your file** text box, enter `action.yaml`.
6.  Configure your first workflow in the file editor:

```yaml
name: Must run on custom runner

on: push

jobs:
  init:
    runs-on: self-hosted
    steps:
      - run: echo 'hello cloud gurus'
      - run: echo $HOSTNAME
      
```
# Set Up the Lab VM to Work as a Runner Connected to Your GitHub Repo

## Create a GitHub Repository and Add a Runner

1.  After logging in to your GitHub account, select the **Repositories** tab, then click **New**.
2.  In the **Repository name** field, enter an easily identifiable name for the repository (like `needs-custom-runner`).
3.  Select **Private** to ensure only authorized users can create pull requests for your custom runner.
4.  Click **Create repository**.
5.  After the repository is created, select **Settings** in the top menu bar.
6.  In the sidebar menu, select **Actions**, then select **Runners**.
7.  Click **New self-hosted Runner**. GitHub provides you a list of commands to download, configure, and run the runner on a VM.
8.  If you're using the VM provided for the lab, select the **Linux** option for the **Operating System**.

## Configure the Runner in Your VM in EC2

1.  Navigate to your VM.
2.  Copy and paste all the **Download** commands and the first **Configure** command from GitHub into your VM, one at a time. After all the commands are entered into your VM, the VM connects to GitHub and authenticates the runner.
3.  When prompted in the VM terminal, press **Enter** to accept all of the defaults.
4.  Copy and paste the last **Configure** command from GitHub into your VM to run the runner:

```bash
./run.sh
```

# GitHub Runners Comparison Table

| **Aspect**                    | **GitHub-Hosted Runners**                                       | **Self-Hosted Runners**                                |
|-------------------------------|---------------------------------------------------------------|-------------------------------------------------------|
| **Setup and Maintenance**      | No setup required; fully managed by GitHub                    | Requires manual setup and maintenance                 |
| **Cost**                       | Free with limits on usage; charges for extra minutes          | No cost for runner; infrastructure costs apply        |
| **Scalability**                | Automatically scales based on demand                           | Manually managed based on your infrastructure         |
| **Environment Control**        | Predefined environments with limited control                   | Full control over the environment                     |
| **Operating Systems**          | Windows, Linux, and macOS                                      | Any OS that can run the runner application            |
| **Security**                   | Secure but runs in a shared environment                        | Potentially more secure, isolated in your infra.       |
| **Performance**                | Fixed performance capabilities                                 | Can be tailored to your needs                         |
| **Access to Internal Resources**| Limited unless using self-hosted services                      | Direct access to internal networks and resources      |
| **Customization**              | Limited to available GitHub environments                       | Complete customization of the setup                   |
| **Usage Limits**               | Subject to GitHub's usage limits and quotas                    | Determined by your own resources                      |

