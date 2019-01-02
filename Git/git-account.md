# Git Account

## Using more than one git acount in single mac.

I had to use 2 git account on mac, one for private GitLab for work and another for my personal GitHub.

1. Generate ssh key

```
$ cd ~/ .ssh
$ ssh-keygen -t rsa -b 4096 -C "my_personal@email.com"
Generating public/private rsa key pair.  
Enter a file in which to save the key (/Users/yourusername/.ssh/id_rsa) : id_rsa_personal
```

After this you should set the passphrase(a.k.a password).\
Then you can find id_rsa_personal file and id_rsa_personal.pub file.

2. Add ssh key to your Github

Go to personal GitHub -> Settings -> SSH and GPG keys -> New SSH key.

- Title: Anything that you can recognize
- Key: Content of id_rsa_personal.pub

Then Add SSH key.

3. Register ssh agent

```
$ ssh-add ~/.ssh/id_rsa_personal    # note that this file is without .pub, which means its private key.
$ ssh-add ~/.ssh/id_rsa_work        # (if necessary, make one for work. I just used my id_rsa file.)
```

4. Create ssh key config file

```
$ vi ~/.ssh/config

# Personal Account
Host personal  
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_personal

# Work Account
Host work  
   HostName {Company GitLab}
   User git
   IdentityFile ~/.ssh/id_rsa # I just used my own id_rsa.
```

5. Use it like this

```
# For personal
$ git remote add origin git@personal:{github_personal_account}/{repo-test-personal}.git

# For work
$ git remote add origin git@work:{work_account}/{repo}.git
```

---

#### Reference

- [Connecting to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/)
- [macOS에서 깃허브 계정 여러개 쓰기](https://bonoogi.herokuapp.com/multiple-github-account-in-mac/)
- [Managing Multiple Github Accounts](https://mherman.org/blog/managing-multiple-github-accounts/)