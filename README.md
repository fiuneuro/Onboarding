# Onboarding
Onboarding information for new members of the FIU cognitive neuroscience program

## Accounts to sign up for
- [ORCID](https://orcid.org)
- [Google Scholar](https://scholar.google.com)
- [GitHub](https://github.com)
- [Trello](https://trello.com)

## Organizational accounts to request access to
- GitHub: [FIU-Neuro](https://github.com/FIU-Neuro) and your lab's organization
    - NOTE: Set your membership visibility to "Public"
- Slack: [FIU Neuro](http://fiuneuro.slack.com) and your lab's workspace
- Google Calendar: **FIU Neuroscience** and your lab's calendar
- Trello: [FIU Neuro](https://trello.com/fiuneuro/home) and your lab's organization

## For incoming graduate students
1. Grad students have two email addresses- a student email (which has numbers, like `tsalo006@fiu.edu`) and an employee email (which generally doesn't, like `tsalo@fiu.edu`). The student email is accessible on Gmail, while the employee email is accessed through Outlook. Make sure to forward your employee email to your student email, or vice versa. Important emails may be sent to either or both, so it is very helpful to just forward one to the other.
2. Follow instructions [here](http://ircc.fiu.edu/accounts/) to obtain access to the FIU High Performance Cluster (HPC). Most labs perform most of their data analysis on the HPC.
3. Follow instructions [here](https://castic.fiu.edu/main/app/core/helpguides/Papercut-Mac.pdf) to obtain access to printer queue. This will allow you to send your print jobs to a queue and release the jobs on the Toshiba printers on campus using your Panther ID card.

## Setting up necessary software on your laptop
Attempt to follow the installation instructions for the below software. However, note that, if you have a lab laptop, you may run into issues with your privileges on the computer. If you do not have admin privileges on your FIU-owned computer, you will need to go through cybersecurity training from CASTIC first and then download an app titled "Privileges" through CASTIC.

Install the following software:
1. A [VNC client](http://ircc.fiu.edu/visualization/): You will need a VNC client DCV NICE in order to access visualization nodes on the HPC.
    - If your HPC account has not been created yet, you can still download the software, but you won't be able to use it.
    - If, for whatever reason, DCV NICE (recommended by the IRCC) does not work for you, try installing RealVNC's [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/).
2. A [VPN Client](https://network.fiu.edu/vpn/): You will need a VPN client like Cisco AnyConnect in order to access the HPC from home.
3. An SCP Client: You will need an SCP client like [Cyberduck](https://cyberduck.io) to transfer files to and from the HPC.
    - If your HPC account has not been created yet, you can still download the software, but you won't be able to use it to access the HPC.
4. [git](https://help.github.com/en/articles/set-up-git): git is necessary for version control and is a key component of GitHub.
    - It will probably be easier to just download [GitHub Desktop](https://desktop.github.com), which provides a simplified GUI for using git, and will automatically set git up without having to configure anything.
5. PaperCut: See above for more information on how to install this software.
6. Slack: See above.
7. [Google Drive File Stream](https://support.google.com/drive/answer/7329379)

## Setting up git on the HPC

1. Get a [GitHub](https://github.com/) account
2. SSH onto the HPC
    - Do the following to SSH onto login node 2 of the HPC:
        - `ssh [username]@hpclogin02.fiu.edu`
3. Set up Git on HPC
    1. [Set your user name](https://help.github.com/en/articles/setting-your-username-in-git) as your name:
        - `git config --global user.name "Mona Lisa"`
    2. [Set your user email](https://help.github.com/en/articles/setting-your-commit-email-address) as the email address you used for your GitHub account:
        - `git config --global user.email "mlisa001@fiu.edu"`
4. Add your SSH key to GitHub
    1. Use the code below to print your public key:
        - `cat ~/.ssh/id_rsa.pub`
    2. Copy the key to your Clipboard, then paste it to your GitHub account settings (on the website) --> SSH and GPG Keys --> add SSH key
        - Name it "HPC"
    - NOTE: Steps 4-6 reflect an abbreviated version of the full set of instructions for connecting to GitHub using SSH, although they should work for everyone with HPC access. If you have problems with this step or the next two, try following the full instructions detailed [here](https://help.github.com/en/articles/connecting-to-github-with-ssh).
    - One common reason this step may fail is because you don't have an existing RSA key. Follow the instructions to generate one from the link above.
5. Test your SSH connection
    1. Test if SSH over the HTTPS port is possible. Run this SSH command:
        - `ssh -T -p 443 git@ssh.github.com`
    2. You should see:
        - > Hi [username]! You've successfully authenticated, but GitHub does not provide shell access.
6. Modify your SSH configuration file
    1. `nano ~/.ssh/config`
        - **NOTE**: If you do not have a config file (or if it is empty), then copy [the example one from this repository](https://github.com/FIU-Neuro/Onboarding/blob/master/templates/.ssh/config) into your .ssh folder.
    2. Add the following lines:  
        - > UserKnownHostsFile ~/.ssh/known_hosts
        - > Host github.com  
        - > Hostname ssh.github.com  
        - > Port 443
    3. You may see the following line somewhere in the file:
        - > UserKnownHostsFile /dev/null
        - If you see it, remove that line. We are replacing it with the first line that you pasted into the file.
    4. To save the file and exit nano, do the following:
        1. Ctrl-X
        2. y
        3. Enter
