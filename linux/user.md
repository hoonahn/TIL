# User

## Add Superuser

First we should add a normal user.

```bash
$ adduser {name_of_user}
...
Enter new UNIX password: {password}
Retype new UNIX password: {password}
passwd: password updated successfully

Changing the user information for {name_of_user}
Enter the new value, or press ENTER for the default
	Full Name []: # Fill out the blanks if you want
	Room Number []:
	Work Phone []:
	Home Phone []:
	Other []:
Is the information correct? [Y/n] Y
# User added.
```

Then we should make the user super.

```bash
$ usermod -aG sudo {name_of_user}
# test
$ su - {name_of_user}
{name_of_user}@{hostname}:~$ # the prompt will change
```

---

#### Reference

##### Ref 1

- [Ref]()