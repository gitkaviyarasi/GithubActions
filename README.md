# GitHub Actions CI/CD Setup
The app was built using the MERN stack with a React front end, MongoDB database, and Node.js/Express.js server and API. It allows users to take a quiz of ten random questions and view their final score.

We need to create a CI/CD pipeline using GitHub Actions to run the component tests via Cypress when a Pull Request is made to the develop branch, and the application is deployed when code is merged from develop to the main branch.

# Steps to setup githubactions:
1. Create a repo in github and add all the required code to the gitHub repo.
   
2. Deploy the application via Render.
   1. In the render, the build command will be `npm run render-build` and for the first time give the seed command `npm run seed`, start command  will be `npm run start`.
   2. Turn off auto deploy and copy the Deploy hook.
      1. Navigate to the repository on GitHub and then select Settings for the repository.
      2. Select "Secrets and variables" from the menu on the left, and then click on "Actions" in the sub-menu
      3. Select "New Repository Secret". Name the new secret "RENDER_DEPLOY_HOOK_URL" and then paste in the URL that you copied earlier from Render
   3. Add the MongoDbURI in the environment variables.
   
3. The github should have ```main branch```(it will be used to deploy the code to Render), ```develop ```  all the code changes from the feature 
   branch will be merged to develop branch.
   feature ---> develop
   while creating a pull request, the tests should be passed to merge.
   develop ---> main
   when we create a pull request, it will be automatically deployed to render.

4. Now add the yml files under.github\workflows. 
   
5. Set up brach protection rules in repo settings, (Go to the "Settings" tab for your repo, select "Branches", then select "Add classic branch protection rule".)
   1.  You will need to set up branch protections for the main and develop branches.
        Note: The branch name patterns must be called main and develop for the protections to take effect.
   2.  For the branch protections:
        1.  On main only: Check "Require a pull request before merging" with "Require approvals" unchecked.
        2.  For both: Check "Require status checks to pass before merging."
        3.  For both: Check "Do not allow bypassing the above settings."
        4.  For the develop branch, in the "Search for status checks in the last week for this repository" input, search for and add the       Checking Tests action.
        5.  For the main branch, in the "Search for status checks in the last week for this repository" input, search for and add the Deploy To Render action.
        Note: The actions will not show up in the search unless they have run successfully at least once. The names we are searching for come from the value provided to the name key under the jobs key in the YAML files. The names are case-sensitive.

6. All the set up has been done and now push the changes from feature branch to develop branch, it should check for test and once the tests pass, it will be merged.
7. Then create pull request from develop to main, it will deploy the changes to render.

The baseURL in cypress.config.ts should be changed to the Render URL.
Verify the scripts in package.json.

## Table of Contents 
- [GitHub Actions CI/CD Setup](#github-actions-cicd-setup)
- [Steps to setup githubactions:](#steps-to-setup-githubactions)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Demo](#demo)
  - [ScreenShots](#screenshots)
  - [License](#license)
  - [Questions](#questions)

## Installation
1. Clone the repository:
    git clone git@github.com:gitkaviyarasi/QuizUsingReact.git
2. Navigate to the project directory and create a branch and open Code editor.
3. Install the package using npm i
4. setup the MongoDBURI in the .env file
5. then run the code by building using the `npm run build` and `npm run start` 
   
## Usage


## Demo
Click the below link for a demo of working application.

https://githubactions-20l7.onrender.com



## ScreenShots
The following image demonstrates the tests.



## License
MIT



## Questions
If you have any questions about this project, feel free to reach out:

GitHub: gitkaviyarasi 
Email: kaviyarasikrishnannj@gmail.com
