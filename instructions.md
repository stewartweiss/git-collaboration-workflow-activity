## Instructions for This Exercise

__Note 1__: Prior to starting, you should have installed a visual Git application on
your machine so that you can see a visual graph of the commits in the repository
as you work. The README in this repository explains how to do this.

__Note 2__: These instructions also assume that you followed the instructions in
the README file and cloned the repository to your local machine, and made the scripts
in it executable.

1. Create a repository on the local machine using the `create_demo_repo.sh`
script. On the command line, enter:

    ```bash
      create_demo_repo.sh  <repo_name>
    ```

    This creates a repository in the current working directory with whatever name
you choose as its only argument,  with a branched history containing two branches,
one named `master` and one named  `feature1`.
__For the rest of these instructions, we will assume that the name
of the repository that you created is `demo`__.

2. If it is not open, start up your browser,
open GitHub, navigate to the class organization, and create an empty repository
named `<your-github-name>-git-exercise-04`.
On the page that is then displayed, choose the option
"`...or push an existing repository from the command line`"
and copy the command-line instructions for that option to your clipboard.

    > _These instructions only push up the `master` branch. That is all we want
to push for now. Although your local repository has a `feature1` branch, we pretend
that it is not ready to be pushed to the server._

3. Return to the terminal window open on your local machine and
make your working directory  the `demo` directory that you just created:

    ```bash
     cd demo
    ```
4. Paste the commands from the clipboard into the terminal window. In most
terminal emulators, Control-Shift-V does this. If this works, you will be
prompted to authenticate by whatever method you set up with `GitHub`, and then
your repository will be populated on GitHub with the history and files
of your `master` branch.

5. It is time to start up the Git visualization tool that you installed
on your machine. I will assume here that it is `gitg`,
the `Gnome` GUI client. Return to the command line on the local machine and
in the command-line, type

    ```bash
     $ gitg &
    ```

    This starts it up and puts it in the background so that you can continue to
use the terminal. You can ignore the various warnings that it might display as
long as the window pops up and has meaningful content. (Or you can be a good
citizen and report the issue to the community.)
As you work, take a look at how the repository's history
changes. Before you go further, take a look at what it looks like and remember
it.



5. __[ALTERNATIVE INSTRUCTION]__ Instead of doing steps 7 through 15 below, you can
run the script in this repository named `make_simulating_team_repo.sh`, which
will create all of the files created, staged, and committed in those instructions
and then push the new work to the GitHub repository, so that you can continue
from step 15. It requires two arguments: a name for a second repository that it
will create, and the URL of the GitHub repository that you created in Step 2 above.

   If you choose to do this, this script must be executable, __and you must make sure
that you switched back into the `demo` directory before you run it.__

   In short,  you enter the following command when your current directory is
`demo`:

    ```bash
     $ make_simulating_team_repo.sh  <temp-repo-name> <remote-repo-name>
    ```


5. Return to the repository on GitHub and refresh the page if you do not see the
repository files automatically.

    > _The next two instructions will create a few commits on GitHub so that
your local  `master` branch will be "behind" the `origin/master`
__remote branch__. To do this, you will create two files on GitHub, put
some text into them and commit them. This will create two new commit objects
in the `master` branch of the __upstream__ ( i.e., what you call `origin`)
associated with your local `demo`repository._

6. [__Creating a file on GitHub__ ]
On GitHub click the __Create new file__ button, and name the file `gh_file1`.
In the editor window, type anything you want for the contents of the file,
scroll to the bottom of the screen, type a short Commit message in the text
box below the __Commit changes__ text,
and click the green __Commit new file__ button.

7. Repeat the previous instruction but name this second file `gh_file2`.
    > _Now you will create a new feature branch on GitHub, not on your
local machine._

8. [__Creating a branch on GitHub__]
On GitHub, locate the button on the left-hand side of the screen that displays
the text "branch: master". Click that button once and a pop-up window will be
displayed that has an empty text box with the text "`find or create a branch`"
as well as a list of your repository's existing branches below it.
In that text box, type  `feature2`. Anothed small pop-up window will be displayed
with the text "`Create branch: feature2 from master`". Click the box.

9. Repeat the instructions in [__Creating a file on GitHub__ ] above, naming the
new file `feature2_file1`.

10. Repeat the instructions in [__Creating a file on GitHub__ ] above, naming the
new file `feature2_file2`.

    > _You now have a feature branch on GitHub that is ahead of the `master` branch on
GitHub by two commits. We want the structure of this upstream repository on
GitHub to  be a bit more complex, so you will now check out the `master` branch
on GitHub and create another  branch from it named `exploratory`._

11. Go back to the button that shows `branch:feature2`,
click on it, and select the `master` branch. If you do this correctly, the box
will show "`Branch: master`".

12. Follow the steps in [__Creating a branch on GitHub__] but name the branch
`exploratory`.

13. Create two new commits by adding two more files, using the instruction
above labeled  [__Creating a file on GitHub__ ] twice. Name your two files
`option1` and `option2`.

    > _The remote repository (on GitHub) now looks roughly like the image below
      In the figure, the master branch on GitHub is the one labeled `origin/master`.
      The branch labeled `master` is the master on our local copy and is not in GitHub.
      We actually created a total of seven commits to GitHub's master branch, though the
      figure shows just five._

    <center>

    ![History of Repository](./img/structure-of-repo-on-github.png)
    <br>
    Image based on [Git Fetch](https://www.atlassian.com/git/tutorials/syncing/git-fetch)
    under a [Attribution 2.5 Australia (CC BY 2.5 AU)](https://creativecommons.org/licenses/by/2.5/au/) license.
    </center>


    > You can see a similar graph by navigating on GitHub to the __Insights -->
Network__ tab.

    > _You will now return to your local machine to use Git to do some work,
but before you do so,  make sure that you have read the slides
[Collaboration Workflow Basics](http://www.compsci.hunter.cuny.edu/~sweiss/course_materials/csci395.86/slides/collaborating_workflows.html)_.

14. Return to the terminal window open on your local machine and
make  sure that your working directory is still  the `demo` directory that you
created before.

    > _We will now simulate what happens when you and your team members have
been working independently. Although you just created a bunch of files yourself
on GitHub, this could have also been the result of your team members pushing
their own changes up to the common repository. That is how you should think
of it for now: the files and commits you made on GitHub are really the work
of others that took place concurrently with what you are about to do._

    > _You will now create a few more files in the `feature1` branch in your
repository. This simulates your working on your own on the feature branch that
is your task in this quest._

15. Check out the `feature1` branch in your repository:

    ```bash
      $ git checkout feature1
      Switched to branch 'feature1'
    ```

16. Write the following `bash` for-loop in your shell. After you type the first
line, `bash` will prompt you for the remaining lines with your
__secondary prompt string__, the `PS2` shell variable. It is usually "`-->`".
So when you see it, just type the second line, followed by the newline,
then the third and so on, and type `done` on the last line:

    ```bash
      $ for i in 3 4 5 ; do
           echo "feature1_${i}" > feature1_${i}
           git add feature1_${i}
        done
        git commit . -m "added 3 new features to feature1"
    ```
    The result of this will be that you created three new files named `feature1_3`,
`feature1_4`, and `feature1_5`, and a single new commit.

    > _Your `feature1` branch is now ready. You did some work and now you are confident
that you want to incorporate it into the project._

    > _Take a look at `gitg`'s window to see how it changed._

    > _You want to  pull down the work that has been done from the upstream, but
you will not use the `git pull` command to do this, as was explained in the
tutorial. You will use `git fetch`._

17. We fetch just the upstream `master` branch for now, the one that is _tracked_
by your local `master` branch, and the one that is known locally as
`origin/master`. Enter the following command.

    ```bash
      $ git checkout master
      Switched to branch 'master'
      Your branch is up to date with 'origin/master'
    ```
    Although Git reports that `master` is up to date with `origin/master`, it
stated this only because it did not yet "know" that `origin/master` has advanced.

18. Now enter the commands

    ```bash
      $ git fetch origin master
        remote: Enumerating objects: 7, done.
        remote: Counting objects: 100% (7/7), done.
        remote: Compressing objects: 100% (2/2), done.
        remote: Total 6 (delta 2), reused 6 (delta 2), pack-reused 0
        Unpacking objects: 100% (6/6), done.
        From https://github.com/stewartweiss/git-exercise-04
         * branch            master     -> FETCH_HEAD
           adf8879..da30c3e  master     -> origin/master
      $ git status
        On branch master
        Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
          (use "git pull" to update your local branch)

        nothing to commit, working tree clean
     ```
    This fetches Git's data from GitHub about the master branch. In this output,
the remote is a repository in my account. Notice that Git now knows that our
local master branch is behind the master in GitHub by the two commits that were
made to master there.

19. Type `ls` and notice that the files in the master branch on GitHub that were
added after we pushed our repository up are not in our working directory. Git fetch
does not create them:

   ```bash
     $ ls
      file1  file2  file3  README.md
  ```
18. Open the `gitg` window again and notice that it has added the commits
from the `master` branch on GitHub. But if you look at your working directory
it will not have the files `gh_file1` and `gh_file2` that you created.
__Fetching brings down the data from the upstream but it does not modify your
working directory. This is why it is safe__.

19. We will do a __fast-forward__ merge to move the `master` branch up to date
with `origin/master`. Enter:

    ```bash
      $ git merge origin/master
      Updating 4df383a..80b8cda
      Fast-forward
       gh_file1 | 1 +
       gh_file2 | 1 +
       2 files changed, 2 insertions(+)
       create mode 100644 gh_file1
       create mode 100644 gh_file2
    ```
20. Now look at your working directory with `ls` and see that the files are
there! The `merge` updates the working directory

    ```bash
     $ ls
      file1  file2  file3 gh_file1  gh_file2  README.md
    ```
    > _Now it is time to integrate your work on the `feature1` branch with
the upstream changes in the `master` branch. But we will not use `merge`.
This is a perfect chance to practice rebasing._

    > _Conceptually, your feature branch and the master branch look like
the figure below, although the number of commits on the master is greater
than what this figure shows._

    <center>

     ![History of Repository](./img/forked-commit-history.png)

    </center>

    > _We will rebase the feature onto the updated master branch. What you will
discover though is that we have a __rebase conflict__, which is essentially like
a merge conflict. Git cannot automatically resolve the different versions of
`file1` in the `master` and `feature1` branches. This will be good practice in
manually fixing a rebase conflict._

21. Enter the following commands

    ```bash
        $ git checkout feature1
        Switched to branch 'feature1'
        $ git rebase master
        First, rewinding head to replay your work on top of it...
        Applying: added feature1_1
        Applying: added feature1_2
        Applying: changed file1
        Using index info to reconstruct a base tree...
        M	file1
        Falling back to patching base and 3-way merge...
        Auto-merging file1
        CONFLICT (content): Merge conflict in file1
        error: Failed to merge in the changes.
        Patch failed at 0003 changed file1
        Use 'git am --show-current-patch' to see the failed patch

        Resolve all conflicts manually, mark them as resolved with
        "git add/rm <conflicted_files>", then run "git rebase --continue".
        You can instead skip this commit: run "git rebase --skip".
        To abort and get back to the state before "git rebase", run "git rebase --abort".
    ```
22. We have to fix this. First, open up `file1 in whatever editor you feel
confident using. You will see

    ```bash
      <<<<<<< HEAD
      1: modified line_1
      =======
      1:  line_1
      >>>>>>> changed file1
    ```
    Replace these lines with a single line such as

    ```bash
      1: line 1 is fixed
    ```

    and save the file. Then run

    ```bash
      $ git add file1
      $ git rebase --continue
    ```

    and the problem should be solved.

    > _The history that you should see in `gitg` is now linear; your `feature1` branch is
just a chain,  a few commits ahead of the `master` (and `origin/master`)
branch. Although you might be tempted, you are not supposed to move `master`,
because that implies that your `feature1` is merged into the project._

    > _The history now looks like this:_

    <center>

    ![History of Repository](./img/rebase-onto-feature.png)

    </center>

     > _Suppose now that the team member who was responsible for developing
`feature2` contacts everyone and says that the version of `feature2` on the
server is final and can be merged into the `master` branch. She asks you if you
can do her the favor, since you already have the most recent `master` on your
local machine, of fetching the `feature2` branch and integrating it into your
local copy, after which it can be pushed back up to the upstream. You agree
to do this._

23. Your next step is to fetch that upstream `feature2` branch and merge it in.
We will use the `fetch/merge` approach to do this. We fetch the `feature2` branch:

    ```bash
      $ git fetch origin feature2
      remote: Enumerating objects: 7, done.
      remote: Counting objects: 100% (7/7), done.
      remote: Compressing objects: 100% (2/2), done.
      remote: Total 6 (delta 2), reused 6 (delta 2), pack-reused 0
      Unpacking objects: 100% (6/6), done.
      From https://github.com/stewartweiss/git-exercise-04
       * branch            feature2   -> FETCH_HEAD
       * [new branch]      feature2   -> origin/feature2
    ```

24. You do not have a local `feature2` branch to track this remote branch.
If you look at the visual display you will not see a `feature2` branch. Fetching
does not create it,  so the
next step is to create it. The following instruction creates a branch named
`feature2` that tracks `origin/feature2` and then makes it the currrent branch:

    ```bash
      $ git checkout -b feature2 origin/feature2
    ```

    Take a look at the `gitg` window and notice that the history is now forked
again, and that the `feature2` branch tip is two commits ahead of `master`. If
you enter the `ls` command you will also see that the new files are in your
directory. This is because the `feature2` branch is created based on the remote
branch `origin/feature2`.


    > _Because `master` is an ancestor of `feature2` and not on a different part
of the tree, we can do a __fast-forward merge__ to integrate the feature into the
master branch. This will move the `master` branch so that it points to the same
commit as the `feature2` and it will also update the working directory._

25. We switch to the `master` branch to do a fast-forward merge:

    ```bash
      $ git checkout master
      Switched to branch 'master'
      $ git merge feature2
      Updating 80b8cda..c0c3627
      Fast-forward
       feature2_file1 | 1 +
       feature2_file2 | 1 +
       2 files changed, 2 insertions(+)
       create mode 100644 feature2_file1
       create mode 100644 feature2_file2
    ```

    > _Notice that Git added the two missing files. If you look at `gitg` again (you
might have to refresh it or close and reopen it) you will see that `feature2`,
`origin/feature2`, and `master` all point to the same commit. However, `feature1`
is no longer ahead of `master`; they are not on the same linear path. In other
words, `feature1` no longer is based on the most recent version of the `master`
branch._

    > _Our last task should be to fix this. We will rebase our `feature1` branch
on `master`._

26. Enter the following commands:

    ```bash
      $ git checkout feature1
      Switched to branch 'feature1'
      $ git rebase master
      First, rewinding head to replay your work on top of it...
      Applying: added feature1_1
      Applying: added feature1_2
      Applying: Added three new files to feature1 branch
    ```
    Look at the working directory and look at the `gitg` window. The history is
once again linear and all files are present.

    > _Everything has been done. You can push these change back up to the server
if you like. If you want, you can fetch the `exploratory` branch if you just want
to inspect it. That is the last step of this activity._

27. Enter the following command:

    ```bash
      $ git fetch origin exploratory
      remote: Enumerating objects: 7, done.
      remote: Counting objects: 100% (7/7), done.
      remote: Compressing objects: 100% (2/2), done.
      remote: Total 6 (delta 2), reused 6 (delta 2), pack-reused 0
      Unpacking objects: 100% (6/6), done.
      From https://github.com/stewartweiss/git-activity-04
       * branch            exploratory -> FETCH_HEAD
       * [new branch]      exploratory -> origin/exploratory
    ```
    > _Since we are only inspecting and have no plans to integrate this work
into our repository, it is enough to just check out the new remote branch._

28. Enter the command:

    ```bash
      $ git checkout origin/exploratory
      Note: checking out 'origin/exploratory'.

      You are in 'detached HEAD' state. You can look around, make experimental
      changes and commit them, and you can discard any commits you make in this
      state without impacting any branches by performing another checkout.

      If you want to create a new branch to retain commits you create, you may
      do so (now or later) by using -b with the checkout command again. Example:

        git checkout -b <new-branch-name>

      HEAD is now at ec96968 Create option2
    ```
    By doing this we can examine the files, which _are_ in our working directory.
If we want to do any work and be able to make commits, we need to follow Git's
advice and create a new tracking branch, as follows._

29. Enter this (very last, really) command:

    ```bash
      $ git checkout  -b exploratory
      Switched to a new branch 'exploratory'
    ```
    Look at the `gitg` window and you will see the final state of the repository.
You might have to refresh or reload the window.

    > _The history now looks approximately like this, ignoring the number of
commits, and that the common ancestor of `exploratory` and `master` should be
`origin/master`, and that some branchnames not labelled correctly:_

    <center>

    ![History of Repository](./img/final_state.png)

    </center>

