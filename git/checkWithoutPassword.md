## 1. Generate an SSH key
Linux/Mac
Open terminal to create ssh keys:
```
cd ~                 #Your home directory
ssh-keygen -t rsa    #Press enter for all values
```

## 2. Associate the SSH key with the remote repository

If it is a GitHub repository and you have administrative privileges, 
go to settings and click 'add SSH key'. Copy the contents of your ~/.ssh/id_rsa.pub into the field labeled 'Key'.

## 3. Set your remote URL to a form that supports SSH 1
If you have done the steps above and are still getting the password prompt, make sure your repo URL is in the form
```
git+ssh://git@github.com/username/reponame.git
```
as opposed to
```
https://github.com/username/reponame.git
```
To see your repo URL, run:
```
git remote show origin
```
You can change the URL with:
```
git remote set-url origin git+ssh://git@github.com/username/reponame.git
```

reference:
https://stackoverflow.com/questions/8588768/how-do-i-avoid-the-specification-of-the-username-and-password-at-every-git-push
