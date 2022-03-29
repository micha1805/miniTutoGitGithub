# git and github

## solo work

As a general information, if you work alone you can obviously still have a github repo for your project ! Just don't forget to push your code regularly (and pull if you merge on github and not locally).

### initialize your project

initialize your git in your project's folder :

```bash
git init
```

Create your first commit.

First stage everything :


```bash
git add .
```


then commit it (make a snapshot of that current state of your code):

```bash
git commit -m "First commit"
```

By default this is on the `master` or `main` branch (this is the default branch, its name can vary)


### commit your changes


#### Big changes

If you work on big features create new branches for each one of them :

```bash
git branch myNewBigFeature
```

then switch to that branch :

```bash
git switch myNewBigFeature
```


Now you can commit each individual modification :

Selects the files you want in your commit (everything in this example)
```bash
git add .
```

Then take your snapshot, the commit :

```bash
git commit -m "I changed this and that and blablabla..."
```

Repeat this until your feature is working as you want.

When your feature is working fine you can now merge into the main branch.

If your project is on github you can merge on github yourself, as explained in the next chapter, or you can merge locally.

To merge locally : when you've commited eveything you wanted and your feature is ok, switch to the main branch :


```bash
git switch main
```

then merge into it the branch you were working on :

```bash
git merge myNewBigFeature
```

If there is no conflict you're done, you have a new commit in the `main` branch with your last changes, if you have conflicts you need to solve them.

If you have conflicts, stay in the `main` branch and go to the files with the conflicts, you'll get stuff like this :


```
<<<<<<< HEAD

something in the main

=======

something else in my new branch that is different

>>>>>>> myNewBigFeature
```

Delete all this text to only keep what you want, for instance :

```
something else in my new branch that is different
```

Now stage all these files (or this file if there is only one) and commit it in your `main` branch :

```bash
git add .
git commit -m 'conflicts solved !'
```


You're done !


#### Small changes

If you want to do small changes like typos etc. you can stay in your main branch.

You can still do bigger changes in your main branch if you really want to, but as a general rule it's bad practice.


So you stay in your `main` branch and you do some modifications, then when it's done select the modified files you want in your snapshot (here it's everything, which is what you will very often do):

```bash
git add .
```


Then take the snapshot of your code, which is the commit :

```bash
git commit -m "I did this and this and that"
```

Then you're done !


## team work


### creating the repo

One team member creates a repo on github.

Then every member clones it :

```bash
git clone URLGITHUBREPO
```
### modify code

When a member needs to modify something: create a branch :

```bash
git branch myNewFeature
```
Then switch to it :

```bash
git switch myNewFeature
```

Do your modifications then add it to the git index (staging area).

(If you don't want to add everything add only the files you want)

Add everything from current folder :

```bash
git add .
```

Then make a snapshot of the new state of your code, using git commit :

```bash
git commit -m "This is the message of my commit, write here some indications about what you did"
```



### merge on github

When you're done with your modifications on your branch, push it to github :


```bash
git push origin myNewFeature
```

For information `origin` is the name of the github url of your repo, you can check it out like so, you'll get the value of your different remotes, normally just one, the `origin` remote.

```bash
git remote -v
```
example output :

```
origin	git@github.com:mygithuburl/myprojectname.git (fetch)
origin	git@github.com:mygithuburl/myprojectname.git (push)
```

You have 2 lines because there is also a line for the pull/fetch, but obviously for us they are the same.


When everything is pushed to github you need to go on the github website, you normally will get a big green button suggesting to do a pull request, click on it.


Then fill some information in the form, what you changed, some infos about your modifications etc. then click on create a pull request.

When the pull request is made you have 2 options : either merge yourself, either ask someone else.

In a perfect world the one merging your branch is not you, because another eye is better to check all the possible conflicts.

If you're not in a perfect world or if the changes are minor, merge yourself.

To merge the developer responsible of merging has to click the 'merge pull request' buttons.

If there are no conflicts : Hurray ! You have merged to the main branch !


If there are conflicts :

```bash
git pull origin main
```
Then in the code you have locally go to the files with conflict and resolve them.


Once the conflicts are resolved :

Stage your changes :
```bash
git add .
```
Commit them :

```bash
git commit -m 'conflicts solved'
```

then push them :

```bash
git push origin main
```





Once everything is pushed : every member can pull the new version :

```bash
git pull origin main
```


You're done !
