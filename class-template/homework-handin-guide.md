# Handing in homework
If the module repository does not specify a different process, the standard way of handing in homework is as follows.

## Initial setup (one time only)
There is a single repository with all of the homework you will be doing for HackYourFuture that can be found [here](https://www.github.com/HackYourFuture/homework). Follow these steps to get set up:

- Fork the repository. In the top right of the homework repository page, click on the fork button to fork it to your github. 
- Set up a remote upstream by issueing the following command: `git remote add upstream https://www.github.com/HackYourFuture/homework`

Once done your own forked repository is what you will be working on, make sure to never push anything to the `main` branch so that you can keep updating your fork to the latest changes. 

(OPTIONAL): To remind yourself there is a function in github to protect certain branches, many times the `main` branch will be protected from direct pushes as the `main` branch is what the user is working on. Mistakes pushed to such a branch can be disastrous. To protect your main branch follow the following steps:
- Go to your forked repository. Something like https://www.github.com/GITHUBNAME/Homework
- Click on `Settings`
- In the side menu click on `Branches`
- Next to the `Branch protection rules` title click on the `Add rule` button
- Fill in `main` as the `Branch name pattern`
- Check the box `Require pull request reviews before merging`. This means that the only way to get something into that branch is via a pull request.
- Check the box `Include administrators`. This means that you also get blocked as you are the administrator.
- Click `Save` and it is set up!

## Week of homework (every week)
If your week in the curriculum calls for homework to be handed in, the following steps should be taken. This process will make it the easiest for our mentors to give you feedback on your code and allows us to keep track on how everyone is doing.

1. Make sure you are up to date with the latest version of the homework by issueing the following commands:
  - `git fetch upstream` to check the latest version
  - `git checkout main` to make sure you are on your main branch
  - `git rebase -Xtheirs upstream/main` to grab the latest version from the HYF Homework repository
  - `git push` to update the main branch of your forked repo on GitHUb (Remember to remove your branch protection and reenable that if you did that in the setup)
  - `npm install` to make sure any needed packages are installed
2. Create a new branch `MODULENAME-WEEKNAME`. So for example, the first week of JavaScript should be called `JavaScript-Week1`
3. Do your homework! Remember that there is a test runner that does some automated testing of your homework, you can find out about that in the `README`.
4. Once completed add and commit everything to the branch
5. Push the branch to your repository
6. Create a pull request by click the `create pull request` button in your github repository page (`https://github.com/GITHUBNAME/Homework/pulls`). The pull request should be from your branch to the main branch. Do *not* create a pull request to the HYF Homework repository.
7. Add an issue to your class repository with the name `YOURNAME - MODULENAME (WEEKNAME)`. In it, share a link to the PR request you just created. Also assign it the correct milestone (the name of the module), the correct week label and make sure you assign yourself to the issue as well. 
8. Lastly, add the 'Needs review' label so our mentors know they can start reviewing it.

## Review process
All of your homework will be reviewed by one of our mentors in a very similar way code reviews happen in any company you are going to work at. The homework issues you create every week will go through the following process:

1. Initially the `Needs review` label is set.
2. When the mentor starts reviewing, the label `Review in progress` is added.
3. Once they are done the mentor decides if the homework is good enough or some work is still needed. If the homework is good enough, the issue will receive the `Approved` label. If not, the label `Reviewed with feedback` will be set.
4. The student looks at the feedback and corrects their homework. Once finished, the label `Needs review` is set again. We then go back to step 2.

So if an issue is assigned to a student with the `Reviewed with feedback` label, that means the student needs to work on it. If an issue has the label `Needs review` it means it is for the mentor to look at. In the end all issues should get the `Approved` label! The class mentor will keep an eye on the issues and close the issues once everything checks out.
