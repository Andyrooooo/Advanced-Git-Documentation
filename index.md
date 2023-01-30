# Git Basics

### What is Git?
#### Git is a version control system that will track all your files and any changes made to them to boil it down. It does this by your commits you make, each commit Git will go through your lines of code and see which lines have changed and save those into the "timeline" which is just a snapshot of how it looked at the moment of the commit. This gives you a history of your commits you have made that you can reference back to, or just revert back to a specific commit you made. Git can be linear in this "timeline" but it doesn't have to be, Git also allows you to branch from your main root repository to allow you to work on your projects without any changes made to the main project. If your trying to work on some code for a specific feature or working collaboratively and the project is divided out to each member each person can work in another branch without affecting the main project, and then can later be merged together. Now, Git has three main states that your files can be in, there's the modified, staged, and committed states. When your file has changed, say you have made changes to your code and you save it in like VSCode it will then be in the modified state. Once you add the new changes it is then moved from the working directory into the staged state. In the staged state you can look through the changes and only commit cerain files or commit it all, it is really up to you, but when you are ready you will commit your changes and it will then be in the committed state where the files are now tracked by git. 

### Why use Git? What problem does it slove?
#### Git accomplishes exactly what I explained in the previous paragraph, it makes commits, merging, branching, and overall collaboration so much easier and faster. It also allows other to make a clone of your work to help with this collaboration. If they have a repository they can copy your files including your commit history and work in different areas but then merge those changes together. You're able to work on the same file as your team mate or friend.

### What is the difference between Git and Github?
#### Git is the actual version control system that you will use on your local machine to work on your projects. The whole process we talked about earlier will apply to Git. So, you can make changes add those changes and then commit, which is saving it your local files. GitHub is essentially the hosting service for your repositories if you decide to take that route. To do that, once you committed your changes to your files you would push this to your repository on GitHub (make sure you create the repo on GitHub first). It is also helpful for those trying to find others to collaborate on their work outside of their project group. Others may make suggestions for the code, contribute, or even use your code for their projects. GitHub is a good way to find features, frameworks, and other work that may help your project. 


## Git rebase
### What is Git rebase?
#### Git Rebase is a command used to merge commits from one branch on top of another branch that you choose. So, essentially it orphans the original commits made by the new branch when it split from the ancestor of this branch and another branch, and then places them on top of the branch you chose. So, it is all the same commit history it just makes your commit history more linear. 
![rebase2](https://user-images.githubusercontent.com/97576252/215553550-f0674ddf-ea29-427e-b1cd-428fefb50473.jpg)![rebase](https://user-images.githubusercontent.com/97576252/215553617-8b0dbc0e-640b-434d-8bc4-548a6c839392.jpg)



### What are some advantages and disadvantages of Git rebase? (At least 2 of each)
#### **Advantages**
* An advantage to this is reviewing your history will be much easier when it is more linear than a gigantic mess of many different branches.
* Another advantage is if your working in a large team, using rebase can help clean up intermediate commits by making them just one commit.
* It also eliminates the need to merge the two branches because it has essentially merged them with the commits in a linear way.

#### **Disadvantages**
* Although it may have its advantages, not many people have experience with rebase and if done incorrectly can be destructive to your commit history if there turns out to be any bugs or no documentation as to why something was done the way it was.
* It can also be more time consuming if you rebase branches with a buch of conflicts, and nobody wants to spend more time on something they are already spending a lot of time on.

### When shouldn't you use Git rebase? Why?
#### Using Git Rebase may seem nice to use when you want to make your commit history linear and nice to look at, however I would say you shouldn't use Rebase on larger projects with mutiple developers working on the project. This is because there can be more disadvantages then there are advantages. If you have developers who are prone to mistakes they may introduce bugs into the project which inevitably may take longer to resolve. At times you may never notice this bug until later down the road and can be a long road going through the history to find the issue.

## Create a new repo and demonstrate your knowledge of the following items with screenshots:
### A rebase merge
here insert the image of the rebase
#### As you will see here we have the initial commits and a point where the "new" branch diverged from the master branch and created commits of their own. We then use the rebase command from the "new" feature and it re-writes its history on top of the master branch. 

### An interactive rebase merge
here insert the images
#### In the interactive rebase you will place the commit history of the branch on top of the target branch just like a regular rebase, but the interactive rebase allows you to make changes to those commits. 
using the command `git rebase <target branch> -i` it will bring up the various commits. In here you can choose from the list of commands you want to do for each commit before it is rebased into the other branch

### When you shouldn't rebase with a remote repo.
#### In here I have pushed the local repo to a remote repo on github. Now the problem can arise when you create a remote repo that is worked on with a team. It destroys the history and make it difficult for others on your team to understand what happened. Another issue can arise when there are changes made to the same branch in the remote repo that are not made locally. When this happens and you use rebase and push to the remote it can be destructive as well.

## Git reset, checkout, and revert
### What is Git reset?
#### Git reset will essentially take your current branch and its commit history and have it point somewhere else.
(show the image here)

### What is the difference between hard, mixed and soft?
#### `Git reset --hard` will completely remove any commits made up to the commit that it will be pointed to and remove any of the changes made and are then removed from the local directory. They will show in the previous image like this as orphaned and unrelated to the commit history at that point.

#### `git reset --mixed` will reset you to the target commit and will unstage your commits, they are not removed and the files will stay the same.

#### `git reset --soft` will not touch your index, so it will keep your files and stage all changes back, and will be back prior to being commited. It will still move you down to the targeted commit but when you run git status they will be there in the staging area.

### What is Git checkout?
#### Git checkout is a way for you to move from one branch to another. When working on a project and needing to split into another branch to work on the project without affecting the actual project you'll find this very handy to go back and forth between different versions. Not only that but you can point to a specific commit and look at it at that snapshot in time. So, it can be used to copy a file from another commit into your current working tree, but won't automatically commit the file.
(place image here)

### What is Git revert?
#### Git revert will essentially create a new commit in your current branch. When it does this it is supposed to reverse the point in your commit history that you chose. So to give a little more context say we created 5 new files: 1, 2, 3, 4, and 5. Now, once we created them we use `git revert` and revert back the third commit with the hash "c8012d7". What it will do is remove the 3rd file and then create the new commit after. It also will not remove the commit history from the 3rd commit because it will still be there, so if you want to refer back to it you can, it will just revert your current working tree or the head of your current branch. It's non destructive and can also help for tracking bugs. 
(place image here)

### In what ways are these commands the same and what ways are they different?
#### The git revert and git reset are similar as the both will undo commmits, but they are different in how they achieve that command. The way that reset and revert can be different is say you had the scenario in the git revert happens where you have the 5 commits. But you acutally want to go back to the 3rd file and remove the history and those files to the third file, you would do a `Git Reset --hard`. So, they are different because the revert will only remove the file you pointed to but reset will remove everything up to the commit you are pointing to. Git Checkout on the other hand is used to copy or 

### When would you use reset, checkout, or revert? Why?
#### Git Checkout would be used in all sorts of situations. You could use it to move from branch to branch or just checking your commits and see how the code was at that time to see if there was something removed that you needed. Git Revert would be used where you wanted to remove a specific commit you made that you made earlier that is no longer needed. Reset is a hardcore one and would be used in situations where you want to remove those commits and files and are positive you want to remove them because they will be gone after that.

## Create a new repo and demonstrate your knowledge of the following items with screenshots:
### a Git reset 
(place image here)
#### In here you will see that we reset the "new" branch with a hard reset back to 97ba6da commit, which all commits that are orphaned and are no longer in the commit history.

### a Git checkout
(place image here)
#### You'll see here that we start in the master branch and move our way into the "new" branch using checkout

### a commit
(place image here)
In here you will see each commit that is made and is the snapshot of all data committed at the time.

### a Git revert
(place image here)
In here you will see the new commit and it is blue to indicate the git revert. 

## Git submodules
### What are Git submodules?
#### Git submodules are essentially a repo within your repo. They are used primarily for libraries, so if you were to find a library you wanted to use for your project you would add it to your project as a submodule and clones the repo into your repo. When you do this it will also show in your Git commit history and will show the name, and what specific commit we are pointing to. This also gives you control of the version you are using in your project, this means that if the owner of the library does any updates it will not affect your project and update automatically. This is also good if someone were to use your project it will tell them what version of that libary you are using within your own project. This doesn't mean you can't update your version to a new one, you are able to do that you would just go in and commit the new version and it will also show this new history in your commit.


### When would you use a submodule?
#### As I explained earlier, you would mostly use submodules for bringing libraries into your projects. It's a good way to bring them in while also allowing there to be a commit history that points back to that library. It is also a good way for you to distribute your repos all as one. It may also help share code between your projects or collaborate your code with other people on the team.


### What are the advantages and disadvantages of Git submodules?
#### **Advantages**
* In some situations its easier to share your code between different projects. Say you just want to share your code with someone else or another project but some of the code is not available with a package manager. This can offer a more simple solution to help you achieve what you want. 

* An advantage to submodules is the fact it can keep your project more clean when introducing third party code into your project. When you copy and paste code into your project from someone else to acheive a function, or feature or whatever it is, your blending it into your project and knowing what is your code and theirs can get confusing. I know from experience that doing this can make it confusing down the road because of others styles it can take more time to read it.

#### **Disadvantages**
* Now given how great it can be it can also be complicated to get to this step and may confuse those who try to use it for the first time.

* Another problem that can arise from using submodules is that it can get pretty complicated, and by this I mean if you try to merge your submodules into your main repo it can get very complex and can turn some away from it. 
