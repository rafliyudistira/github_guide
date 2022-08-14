# **Team Collaboration With GitHub**
## **Tool 1: Adding Team Members**

There are generally two ways of setting up Github for team collaboration:

1. **Organizations** - Organization owner can create many teams with differing permission levels for various repositories
2. **Collaborators** - Repository owner can add collaborators with Read + Write access for a single repository

### **Organizations**
If you are supervising several teams and would like to set different permission levels for each team with various members and add each member to different repositories, then Organization would be the best option. Any Github user account can already create free Organizations for open source code repositories. To create an Organization, simply browse to your organization's settings page:

To access the teams page for your Organization, you can simply go to http://github.com/organizations/[organization-name]/teams to view them or even visit https://github.com/organizations/[organization-name]/teams/new to create new teams with members of 3 different permission levels such as:

1. **Pull Only**: Fetch and Merge with another repository or a local copy. Read only access.
2. **Push and Pull**: (1) along with updating of remote repo. Read + Write access.
3. **Push, Pull & Administrative**: (1), (2) along with rights to billing info, creating teams as well as canceling Organization accounts. Read + Write + Admin access

### **Collaborators**

Collaborators are used to give both Read + Write access to a single repository owned by a personal account. To add Collaborators, (other Github personal accounts) just go to https://github.com/[username]/[repo-name]/settings/collaboration:

Once that is done, each Collaborator will then see a change in the access status on the repository page. After we have Write access to the repository, we can do a git clone, work on the changes, make a git pull to fetch and merge any changes in the remote repository and ultimately git push, to update the remote repository with our own changes:

# **Tool 2: Pull Requests**

[Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) are an awesome way to contribute to a repository independently by forking it. At the end of the day, if we wish, we can send a pull request to the repository owner to merge our code changes. The pull request in itself can then fire off discussions for code quality, features or even general strategy.

Let's now go through the basic steps for a [Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## **Initiating a Pull Request**

There are two [models of pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) in Github:

1. **Fork & Pull Model** - Used in a public repository for which we don't have push access
2. **Share Repository Model** - Used in a private repository for which we have push access. Fork is not required is this case.

Here we see the workflow between two users (repo-owner and forked-repo-owner) for the Fork and Pull model:

1. Identify the Github Repository that you want to contribute to, and click the "Fork" button to create a clone of the repository in your own Github account:
2. This will create an exact copy of the repository in your own account
3. [Choose the SSH URL](https://docs.github.com/en/get-started/getting-started-with-git/why-is-git-always-asking-for-my-password) so that it will ask for your SSH key passphrase instead of the username and password each time you git push or git pull. Next, we will clone this repository to our local machine:

```
$ git clone [ssh-url] [folder-name]
$ cd [folder-name]
```
4. Generally, we will create a new git branch for each new feature. This is a good practice because in the future if we further update the branch after some discussions, the [pull request will be automatically updated](https://stackoverflow.com/questions/9790448/how-to-update-a-pull-request-from-forked-repo). Let's create a new branch to make a very simple change to amend the readme.md file:

```
$ git checkout -b [new-feature]
```
5. After making the relevant additions to build the new features, we will just commit the new changes and checkout to the git master branch:
```
$ git add .
$ git commit -m "information added in readme"
$ git checkout master
```
6. At this point, we will push the branch to the remote repository. For this we will first check the branch name with the new feature as well as the git remote repository aliases. Then we will push the changes using git push [git-remote-alias] [branch-name]:
````
$ git branch
* master
readme
$ git remote -v
origin  git@github.com:[forked-repo-owner-username]/[repo-name].git (fetch)
origin  git@github.com:[forked-repo-owner-username]/[repo-name].git (push)
$ git push origin readme
````
7. In our forked repository Github page, we will change to the branch with the new feature and then hit the "Pull Request" button.
8. After submitting the pull request, it will directly take us to the original repository's pull request page. We will see our pull request, both as a new issue as well as a new pull request.
9. After the discussion, it might be possible that the forked repository's owner might want to add changes to the new feature. In this case, we will checkout to the same branch in our local machine, commit it, and push it back to Github. When we visit the pull request page of the original repository, it will be automatically updated!

## **Merging a Pull Request**
If you are the original repository owner, there are two ways of merging an incoming pull request:

1. **Merging directly on Github**: If we are merging directly in Github, then ensure that there are no conflicts and it is ready to be merged into the master branch. The original repository's owner can simply click the "Merge Pull Request" green button to do so:
2. **Merging in our local machines**: At other times, there may be merge conflicts, and upon clicking the "info" button, Github will have clear instructions on how we can merge the branch in our local machine by pulling in the changes from contributor's branch:

There are different branching models used for versioning in software development teams. Here are two popular git workflow models: (1)[Github workflow](http://scottchacon.com/2011/08/31/github-flow.html) that has a simple branching model and uses pull requests and (2) [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/) which has a more extensive branching. The model that is eventually chosen will definitely vary depending on the team, the project and the situation.

# **Tool 3: Bug Tracking**

### *[Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) are an awesome way to contribute to a repository independently by forking it.*

In Github, the center for all bug tracking are the Issues. Even though they are primarily for bug tracking, it is also helpful to use Issues in the following ways:

* **Bugs**: Things that are obviously broken and need fixes
* **Features**: Awesome cool new ideas to implement
* **To do list**: A checklist of items to complete
Let's explore some of the features of Issues:

Let's explore some of the features of Issues:
1. **Labels**: They are colored categories for each issue. They are helpful for filtering issues accordingly.
2. **Milestones**: They are dated categories that can be associated with each issue and are useful for identifying what issues need to be worked on for the next release. Also since Milestones are connected to issues, it automatically updates the progress bar upon closing each associated issue.
3. **Search**: Auto-complete search for both issues and milestones
4. **Assignment**: Each issue can be assigned to a person in-charge to fix the issue. It is another useful feature to see what we should be working on.
5. **Auto-close**: Commit messages with Fixes/Fixed or Close/Closes/Closed #[issue-number] will automatically close the issue.
6. **Mentions**: Anyone can also leave a note by just indicating #[issue-number] in their messages. Because the issue numbers are hyperlinked, this makes it really easy to mention related issues during discussion.

# **Tool 4: Analytics**
## *It is clear that we can tightly couple our task list and updates to our code commits.*

There are two tools that give insight into a repository - Graphs and Network. Github Graphs provides an insight into the collaborators and commits behind each code repository, while Github Network provides a visualization on each contributors and their commits across all forked repositories. These analytics and graphs become very powerful, especially when working in teams.

## **Graphs**
Graphs provide detailed analytics such as:

* **Contributors**: Who were the contributors? And how many lines of code did they add or delete?
* **Commit Activity**: Which weeks did the commits take place in the past year?
* **Code Frequency**: How many lines of code were committed throughout the entire life cycle of the project?
* **Punchcard**: During which times of the day do the commits usually take place?

## **Network**
Github Network is a powerful tool that lets you see each every contributor's commits and how they are related to one another. When we look at the visualizer in its entirety, we see every commit on every branch of every repository that belongs to a network. Insightful!

# **Tool 5: Project Management**
While Github Issues have project management capabilities with Issues and Milestones, some teams might prefer another tool because of other features or existing workflow. In this section, we will see how we can link Github with two other popular project management tools - [Trello](https://trello.com/) and [Pivotal Tracker](https://www.pivotaltracker.com/). With Github service hooks, we can automate updating task with commits, issues and many other activities. This automation helps in not only saving time, but also increases accuracy in updates for any software development team.

## **Github and Trello**
Trello provides a simple, visual way of managing tasks. Using [Agile Software Development](https://en.wikipedia.org/wiki/Agile_software_development) methodologies, Trello cards can emulate a simple virtual [Kanban Board](https://en.wikipedia.org/wiki/Kanban_board). As an example, we will automatically create a Trello card whenever a Pull Request is made using Github Service Hooks. Let's go through the steps!

1. Open an account in Trello if you don't already have one and create a new Trello Board.
2. Go to the Github repository > Settings > Service Hooks > Trello
3. Get the TOKEN under Install Notes #1 with the hyperlink provided for authentication.
4. Under Install Notes #2, use the URL given to generate a json-formatted structure that gives us the list id for each Trello card. BOARDID is part of the URL when we visit the board at https://trello.com/board/[BOARD-NAME]/[BOARDID]. TOKEN can be create with the hyperlink given under Install Notes #1.
5. Back in the Github service hooks, put in the list id and the token. Check Active, Test Hook and we are all set to get automatic updates every time there's a Pull Request.
6. The next time that there's a Pull Request, the Pull Request Trello card will automatically have a new item!

## **Github and Pivotal Tracker**
[Pivotal Tracker](https://www.pivotaltracker.com/) is another lightweight agile project management tool where story-based planning allows the team to easily collaborate by instantly reacting to various changes and progress of the project. Based on the team's current progress, it can also create charts to analyze the team velocity, iteration burn-up, release burn-down, etc. In this short example, we will automatically deliver a story by linking it to a Github commit!

1. Create a new project in the Pivotal Tracker with a new Story that needs to be delivered.
2. Go to Profile > API Token (right at the bottom). Copy the API token given.
3. Come back to Github repository > Settings > Service Hooks > Pivotal Tracker. Paste the token, check Active and click Update Settings. We are all set to automatically deliver Pivotal Tracker Stories with Github Commits!
4. Finally we will commit our changes and add the tracker id to the commit message with the format git commit -m "message [delivers #tracker_id]"
````
$ git add .
$ git commit -m "Github and Pivotal Tracker hooks implemented [delivers #43903595]"
$ git push
````
5. Now, when we come back to the Pivotal Tracker, we will see that the story has been automatically delivered with links to the exact Github commit that shows the file changes!

With these Trello and Pivotal Tracker examples, it is clear that we can tightly couple our task list and updates to our code commits. This is a tremendous time-saver when working in a team, and it enhances accuracy when linking tasks to the exact commits. The good news is, if you already use other project management tools such as [Asana](https://asana.com/), [Basecamp](https://basecamp.com/) and others, you can also create Service Hooks in a similar way. If there are no existing Service Hooks for your current project management tool, [you can even create one!](https://github.com/github/github-services)

## **Tool 6: Continuous Integration**
[Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) is an important part of all software development projects that work with teams. CI ensures that, when a developer checks in their code, an automated build (including tests) detects integration errors as fast as possible. This definitely reduces integration errors and makes rapid iteration much more efficient. In this example, we will see how [Travis CI](https://www.travis-ci.com/) can be used with Github for CI to detect errors as well as recommend merge when it passes all tests.

## **Setting Up Travis CI**
We will use a simple "hello-world" project for [node.js](https://nodejs.org/en/) with [grunt.js](https://gruntjs.com/) as the build tool to setup a Travis CI project. Here are the files in the project:

1. The hello.js file is the node project. Here we will purposely leave out a semicolon so that it will not pass the grunt build tool for linting:

````var http = require('http');
http.createServer(function (req, res) {
res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World in Node!\n') // without semicolon, this will not pass linting
}).listen(1337, '127.0.0.1');
console.log('Server running at http://127.0.0.1:1337/');
````
2. package.json denotes the dependencies:
````
{
  "name": "hello-team",
  "description": "A demo for github and travis ci for team collaboration",
  "author": "name <email@email.com>",
  "version": "0.0.1",
  "devDependencies": {
    "grunt": "~0.3.17"
  },
  "scripts": {
    "test": "grunt travis --verbose"
  }
}
````
3. The gruntjs build tool only has one task (linting) just for simplicity:
````
module.exports = function(grunt) {
    grunt.initConfig({
     lint: {
      files: ['hello.js']
    }
  });
  grunt.registerTask('default', 'lint');
  grunt.registerTask('travis', 'lint');
};
````
4. .travis.yml is a Travis configuration file that will make Travis run our tests:
````
language: node_js
node_js:
  - 0.8
````
5. Next, log on to Travis with your Github Account and turn on the repository hook under the repository tab.
6. If the step before does not trigger the build, then we will have to manually setup the service hook. To set it up manually, copy the Token under the profile tab.
7. Go back to the Github repository to setup the Github Travis service hooks with the token.
8. For the first time, we need to do a manual git push to trigger the first Travis build and if everything is okay, just visit http://travis-ci.org/[username]/[repo-name] to see the build status as passing!

## **Travis CI with Pull Requests**
Previously, without any CI in the process of a pull request, the steps went something like this (1) sent pull request (2) merge (3) test to see if it pass/fail. With Travis CI hooked up to the pull requests, we will be able to invert steps 2 and 3, further increasing fast decision making on whether or not it's good to merge with Travis giving us the status with each pull request. Let's see how to make that happen.

1. Send a Pull Request with a passing build and Travis will do its magic to let you know that it is good to merge even before merging
2. If the Pull Request fails the build, Travis will also alert you.
3. If we click on the red alert button, it will also link to the travis page to show us the details of the build.

Travis CI with Github is immensely useful for teams because of automated builds and immediate notification. It certainly makes the error correction cycle a lot shorter. If you are using Jenkins, another popular CI tool, yes you can setup Github service hooks very similarly as well.

# **Tool 7: Code Review**
With each commit, Github allows a clean interface for general comments or even specific comments on a line of code. The ability to raise comments or questions on every single line of code is very useful in doing line by line code reviews. To view the inline comments, toggle on-off the checkbox right at the top of each commit.

Let's explore some URL patterns that can be used to help us in code review by quickly giving us the differences between commits:

1. **Compare branches / tags / SHA1** : use the URL pattern https://github.com/[username]/[repo-name]/compare/[starting-SHA1]...[ending-SHA1]. You can do the same with branch or tags.
2. **Compare without whitespace** : add ?w=1 to the compare urls
3. **Diff** : add .diff to the compare URLs to get the git diff information in plain text. This could be useful for scripting purposes.
4. **Patch** : add .patch to the compare URLs to get the git diff information [formatted for email patch submissions](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-format-patch.html).
5. **Line Linking** : When we click the line number on any file, Github will add a #line at the end of the URL and make the entire line background color as yellow. This is neat for pointing out the exact line. It also accepts line ranges by adding #start-end. Here are examples of [line linking](https://github.com/NETTUTS/team-collaboration-github/blob/master/.travis.yml#L4) and [line range linking](https://github.com/NETTUTS/team-collaboration-github/blob/master/.travis.yml#L2-3).

# **Tool 8: Documenting**
In this section, we will explore two documentation methods:

1. **Formal Documentation**: Github Wiki to create documentation for the source code
2. **Informal Documentation**: [Github Hubot](https://github.com/hubotio/hubot) to document discussions among team members and automate information retrieval by interacting with a fun chat bot!
3. **Mentions, Shortcuts & Emoji**
## **Github Wiki**
A Github Wiki can be created with each repository, and this can be extremely handy to put both source code and the documentation under the same repository. To create the Wiki, just access the Wiki tab on the main header and you are set to create pages with information. The Wiki itself has its own versioning, and the data can be cloned into our local machine for updates or even offline access.

One thing that I find very useful is integrating the Github Wiki into the main source code project so that I don't have to maintain two separate git projects. To do this, I add the Wiki git repo as a [submodule](https://git-scm.com/book/en/v2/GitHub-Summary) from the master branch. If you are using Travis CI or any other CI, do ensure that the build tool [ignores the wiki submodule](https://github.com/travis-ci/travis-build/pull/46). For Travis CI file .travis.yml, add the following:
````
git:
  submodules: false
````
Then add a git submodule wiki to the main code repository:

````
$ git submodule add git@github.com:[username]/[repo-name].wiki.git
Cloning into 'hello-team.wiki'...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (6/6), done.
$ git add .
$ git commit -m "added wiki as submodule"
$ git push origin master
````
Now the Wiki will neatly appear as a submodule within the main source code project.

## **Github Hubot**
*Hubot, in short, can tremendously add a lot of fun in documenting and notifying team discussions on important commits.*

[Hubot](https://github.com/hubotio/hubot) is simply a chat bot that can retrieve information or provide notification when connected to Github commits, issues or activities. In a team that seeks to significantly reduce meetings or even totally eliminate them, Hubot with a chat interface among the team members helps to document every single discussion. It certainly promotes flexible work timings, as nobody has to be present at the same time for discussions to take place. Warning: Hubot is terribly addictive!

With this, let's start with setting up Hubot hosted on Heroku and as a bot with the Campfire chat interface! For both [Heroku](https://www.heroku.com/) and [Campfire](https://basecamp.com/retired/campfire), there are free versions to get started.

1. We will use [Github's Campfire version of Hubot](https://github.com/hubotio/hubot). If you wish, you can check out [adapters for other chats](https://github.com/hubotio/hubot) such as Skype, IRC, Gtalk, etc.
2. Open a new Campfire account just for the Hubot and this account will create a new chat room that everyone else will be invited to later on.
3. Deploy Hubot to Heroku with the [instructions given](https://github.com/hubotio/hubot) in the Hubot Wiki. Don't be alarmed if the heroku app url gives a Cannot GET / as [there is nothing to get](https://github.com/hubotio/hubot/issues/286) by default.
4. From the Hubot Campfire account, invite yourself. Now, log into your own Campfire account and execute Hubot help. It will give you all the available command for hubot.
5. Give some a try, such as hubot ship it or hubot map me CERN.
6. Next, we will add in a Hubot script. There are [plenty available](https://github.com/github/hubot-scripts/tree/master/src/scripts) with [command illustrations](https://hubot-script-catalog.herokuapp.com/).
7. As an example, we will add the [github-commits](https://github.com/github/hubot-scripts/blob/master/src/scripts/github-commits.coffee) script so that everytime there's a commit, Hubot will notify us in the chat room. Put the file github-commits.coffee inside the scripts folder.
8. Update package.json file with the relevant dependencies as instructed on top of each hubot script file under comments.
9. Deploy the changes to Heroku once again with git push heroku master.
10. Navigate to the repository in the Github whose commit notification will be displayed in the chat. Add in the web hook under repo settings. In the case of the said "github-commit" script, the webhook will be [HUBOT_URL]:[PORT]/hubot/gh-commits?room=[ROOM_ID]
11. The next time the repository has a commit, the Hubot will chat in and say so!

Checkout other [Github related Hubot scripts](https://github.com/github/hubot-scripts), or if you want to write one there's [a cool tutorial on that](https://code.tutsplus.com/tutorials/writing-hubot-plugins-with-coffeescript--net-28334) as well! Hubot, in short, can tremendously add a lot of fun in documenting and notifying team discussions on important commits, issues and activities taking place with our Github repositories. Give it a try!

As a final note on working with team on Github, here are some productivity tips:

1. **Mentions** - In any text area, we can mention another github user with @user and the user will get notified of the comment
2. **Shortcuts Keys** - Press [shift] + ? to access Github shortcut keys on any page.
3. **Emoji** - Using the [Emoji cheat sheet](https://www.webfx.com/tools/emoji-cheat-sheet/), Github textareas also supports insertion of icons. Go ahead and have some fun with your team mates!

# **Non-Software Collaboration on Github**
Most of us will think of using Github only for software projects. After all, Github was started for social "coding". But, there are some cool Github repositories that are being used for non-coding projects, and they were equally awesome for collaboration and discussion. Because these projects are also open source and anyone can contribute, it's fast to fix errors, easy to report bugs and effective to collaborate with like-minded people.
