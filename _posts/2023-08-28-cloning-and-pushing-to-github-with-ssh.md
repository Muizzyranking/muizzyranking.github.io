---
title: Bye Bye Personal Access Token; Cloning and Pushing to GitHub with SSH
tags: [Git, Github]
style: fill
color: warning
---

Have you ever stumbled upon a discovery that felt like finding a hidden treasure? Well, that's precisely how I felt when I recently learned how to use SSH to clone and push to GitHub repositories. As someone relatively new to the world of software engineering, this newfound knowledge brought a wave of excitement.

Not too long ago, I found myself on GitHub's remote shores, wrestling with the process of pushing code using HTTPS and personal access tokens. Copying and pasting tokens every time felt like sending secret messages to a digital fortress. And then, a fellow developer mentioned SSH as a solution. It was as if a secret door to a treasure trove had been revealed. SSH—short for Secure Shell—promised convenience and security, and I was all ears.

Picture this: Instead of juggling personal access tokens like they're keys to a secret garden, you have a single, magic key that unlocks all your GitHub repositories. This key is your SSH key, a digital passport that lets your machine communicate with GitHub without the hassle of tokens. No more copying, pasting, or worrying about token expiration. Just pure, streamlined code pushing bliss.

## Steps to Cloning and Pushing to GitHub with SSH

### Prerequisites:

1. A GitHub account.
    
2. Git is installed on your machine. You can download it from [**git-scm.com**](http://git-scm.com). Alternatively, you can use gitbash on Windows.
    
3. Basic familiarity with the command line.
    

### Step 1: Generate SSH Key

Open the terminal (or gitbash if you are using gitbash) in your computer system.

Use the below command to generate a new public-private key pair. Works on Windows, Mac, and Linux. Replace `you@email.com` with your GitHub email ID.

```bash
ssh-keygen -t rsa -b 4096 -C "you@email.com"
```

When asked for the location and file name, hit enter to save to the default location.

When asked for a **p**assphrase, either type a secret passphrase and hit Enter, or to leave it empty hit Enter twice.

This will generate two files; a public key ending with .pub and a private key without any extension. (The private key is secret and should never be shared with anyone. Both keys would be in a directory named .ssh.

#### Step 1.1 Adding key to ssh-agent (for git bash users)

Open git bash and run this command

```bash
eval "$(ssh-agent -s)"
```

It should show you the process ID

Now, add the SSH key to the SSH agent. Use the command below to add the SSH key to the SSH agent.

```bash
ssh-add ~/.ssh/id_rsa
```

You will get a message saying identity added. Now proceed to the next step.

### Step 2: Add SSH key to GitHub.

The next step is to add the SSH key to Github, to do that, you need to copy the SSH key. To view the key = enter the following command.

```bash
cat ~/.ssh/id_rsa.pub
```

Alternatively, you can copy the key directly into your clipboard using `pbcopy < ~/.ssh/id_ed25519.pub` (macOS) or `clip < ~/.ssh/id_ed25519.pub` (Windows).

Now go to this URL [https://github.com/settings/keys](https://github.com/settings/keys)

Or you can navigate manually by clicking your profile icon on the top right corner and clicking settings in the dropdown.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693245508909/196cacd6-6aaa-4f41-9359-d557555932ce.png?auto=compress,format&format=webp)

Click on "SSH and GPG keys on the left panel.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693245564496/e97112a4-edd3-46a2-ae1d-80d0da05a187.png?auto=compress,format&format=webp")

Click on "New SSH"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693245606975/67711c41-ae42-4839-a72f-38d042fa0db6.png?auto=compress,format&format=webp)

Give it a title of your choice and leave the key type as "authentication key". Paste the key you copied in the "Key" section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693245714215/30269d76-cfa0-4387-9bf1-bf3089895ca7.png?auto=compress,format&format=webp)

Click on "Add SSH" key button and voila, you can now clone your repository with SSH.

So, there you have it—the tale of how I bid farewell to personal access tokens and embraced the world of SSH. With its convenience, security, and a touch of digital enchantment, SSH has truly made a difference in my coding adventures. The next time you clone and push to GitHub, think about this journey and let the magic of SSH guide your way.

In the grand tapestry of coding, SSH has woven a golden thread of efficiency, and I'm thrilled to share this discovery with you all. Happy coding, fellow explorers, and may your repositories always be filled with the treasures of innovation!
