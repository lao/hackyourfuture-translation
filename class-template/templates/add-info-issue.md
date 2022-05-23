It is time to add yourself to the class repo. This is a practice exercise to learn how pull requests work and get familiar with them as you will be doing these a lot in the rest of the curriculum. Follow these steps to add yourself:

- Clone your class repository to your computer
- Create a new branch `add-YOURNAME-to-class` (don't forget to checkout this branch so you are working on it)
- In the `assets` folder, add a picture of yourself
- In the `README.md` file, add the following code to the class list, updating the capitalised parts with your details:

```
<table>
  <tr>
    <td>
      <img src='./assets/PICTUREFILENAME' height="150px" width="150px" alt='Avatar of YOURNAME' />
    </td>
    <td>
      <h3 display="inline">YOURNAME</h3>
      <ul>
        <li>
          <a href="https://github.com/HackYourFuture/class31/issues?q=assignee%3AYOURGITHUBUSERNAME">My assigned tickets</a>
        </li>
        <li>
          <a href="https://github.com/YOURGITHUBUSERNAME">My github</a>
        </li>
      </ul>
    </td>
  </tr>
</table>
```

- Add and commit your changes.
- Push the branch to this repository.
- Go to https://github.com/HackYourFuture/class31/pulls and click on the `create pull request` button
- Choose your branch in the right dropdown and give the pull request a title, then submit the pull request
- Link the issue and the pull request together. You can do that at the pull request page (you should be there after submitting the pull request) and finding the section on the right with the title `Linked issues`. If you click on that you can select the issue.
- Add your class mentor as the reviewer, by clicking on the `Reviewers` link on your pull request. They will then merge your pull request once it has been checked.

That's it! Pull requests are the most common way open source projects work together, someone proposes changes and others can then easily see what they changed. This also allows others to comment on the changes in an easy way. 

For your homework you are going to be making pull requests from now on (on your own github) so that our mentors can give you feedback the same way professional developers get feedback. This was a practice run to get the hang of it!
