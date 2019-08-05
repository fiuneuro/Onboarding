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
1. Make sure to forward your employee email (e.g., `tsalo@fiu.edu`) to your student email (e.g., `tsalo006@fiu.edu`), or vice versa. Important emails may be sent to either or both, so it is very helpful to just forward one to the other.
2. Follow instructions [here](http://ircc.fiu.edu/accounts/) to obtain access to the FIU High Performance Cluster (HPC). Most labs perform most of their data analysis on the HPC.
3. Follow instructions [here](https://castic.fiu.edu/main/app/core/helpguides/Papercut-Mac.pdf) to obtain access to printer queue. This will allow you to send your print jobs to a queue and release the jobs on the Toshiba printers on campus using your Panther ID card.

## Setting up necessary software on your laptop
Attempt to follow the installation instructions for the below software. However, note that, if you have a lab laptop, you may run into issues with your privileges on the computer. If you do not have admin privileges on your FIU-owned computer, you will need to go through cybersecurity training from CASTIC first and then download an app titled "Privileges" through CASTIC.

## Necessary software for your laptop
1. A [VNC client](http://ircc.fiu.edu/visualization/): You will need a VNC client like VNCViewer or DCV Nice in order to access visualization nodes on the HPC.
    - If your HPC account has not been created yet, you can still download the software, but you won't be able to use it.
2. A [VPN Client](https://network.fiu.edu/vpn/): You will need a VPN client like Cisco AnyConnect in order to access the HPC from home.
3. An SCP Client: You will need an SCP client like [Cyberduck](https://cyberduck.io) to transfer files to and from the HPC.
    - If your HPC account has not been created yet, you can still download the software, but you won't be able to use it to access the HPC.
4. [git](https://help.github.com/en/articles/set-up-git): git is necessary for version control and is a key component of GitHub.
    - It will probably be easier to just download [GitHub Desktop](https://desktop.github.com), which provides a simplified GUI for using git, and will automatically set git up without having to configure anything.
5. PaperCut: See above for more information on how to install this software.
6. Slack: See above.
7. [Google Drive File Stream](https://support.google.com/drive/answer/7329379)

## Setting up git on the HPC

### 1. Get a [GitHub](https://github.com/) account

### 2. Set up Git on HPC
[Set your user name](https://help.github.com/en/articles/setting-your-username-in-git) as your name:
> git config --global user.name "Mona Lisa"

[Set your user email](https://help.github.com/en/articles/setting-your-commit-email-address) as the email address you used for your GitHub account:
> git config --global user.email "mlisa001@fiu.edu"

### 3. Set up your ssh key
- Remember to make your password easy to remember (you will be typing it a lot)

- Use the code below to print your public key.
```bash
cat ~/.ssh/id_rsa.pub
```
- Copy the key to your Clipboard, then paste it to your GitHub account settings (on the website) --> SSH Keys --> add SSH key

### 4. Modify your ~/.ssh/config file using nano
 1. Test if SSH over the HTTPS port is possible. Run this SSH command:

```bash
ssh -T -p 443 git@ssh.github.com
```

You should see:

> Hi username! You've successfully authenticated, but GitHub does not provide shell access.

- Enable SSH connections over HTTPS

```bash
nano ~/.ssh/config
```

Add the following lines:  
> Host github.com  
> Hostname ssh.github.com  
> Port 443

You may also see the following line somewhere in the file:
> UserKnownHostsFile /dev/null
If you see that line, change `/dev/null` to `~/.ssh/known_hosts`.
If you don't see that line, add the following line to the file:
> UserKnownHostsFile ~/.ssh/known_hosts
