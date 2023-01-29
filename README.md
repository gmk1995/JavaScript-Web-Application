# My App

This is a sample JavaScript web application.

## Getting Started

1. Install dependencies: `npm install`
2. Start the app: `npm start`
3. Open [http://localhost:3000](http://localhost:3000) in your browser

### About the Project

This is a very basic example, but it should give you an idea of how the different files fit together. You can use this as a starting point and build upon it to create a more complex application.

Please note that in the above example, the package.json file is present which is used for npm package management, to add and remove the dependencies, to run scripts and other purposes. But you need to run npm install command to install the dependencies and npm start command to run the application.

#### SonarQube Code Quality Check and Store the Build Artifacts in Nexus

Sure, you can use SonarQube to perform code quality checks on your JavaScript application and store the build artifacts in a Nexus repository. Here's an overview of the process:

First, you'll need to set up SonarQube on your machine or on a server. You can follow the instructions provided on the SonarQube website to do this.

Next, you'll need to integrate SonarQube with your build tool. For example, if you're using npm as your build tool, you can use the sonarqube-scanner package to run a SonarQube scan as part of your build process.

In your package.json file, you will add the following script,

**** "scripts": {
    "sonar": "sonar-scanner"
  },****

Next, you can run the SonarQube scan by executing the following command

****npm run sonar****

After the scan is complete, you can view the results on the SonarQube dashboard.

To store the build artifacts in a Nexus repository, you'll need to configure the Nexus repository in your build tool. For example, if you're using npm, you can use the npm-publish package to publish your artifacts to Nexus.

In your package.json file, you will add the following script,

**** "scripts": {
    "publish": "npm-publish"
  },
****
To publish your artifacts to Nexus, you can run the following command

****npm run publish****

After the artifacts are published, you should be able to view them in the Nexus repository.
Please note that the above example is just an overview of the process, and the exact steps may vary depending on your specific setup. Also, you need to make sure that the Nexus is configured and running before you run the above command.

##### Jenkins Pipeline

The project uses a Jenkins pipeline to automate the build and deployment process. The pipeline consists of the following stages:

1. GitCheckOut: The pipeline checks out the code from the `main` branch of the repository located at `https://github.com/gmk1995/JavaScript-Web-Application.git` using the credentials specified in the `credentialsId` parameter.

2. InstallNpmDependiences: The pipeline runs the `npm install` command to install the project's npm dependencies.

3. SonarQubeReport: The pipeline runs the `npm run sonar` command to generate a report on the code's quality using SonarQube.

4. UploadArtifactsToNexus: The pipeline runs the `npm run publish` command to upload any build artifacts to Nexus.

5. StartingTheApp: The pipeline runs the `npm start` command to start the application.

## Running the Application

To run the application locally, you will need to have NodeJS installed. You can then clone the repository and run the following commands in the project's root directory:

```javascript
npm install
npm start
```

javascript

This will install the project's dependencies and start the application.

## Note

Make sure that you have configured the sonarQube and Nexus authentication details in the project's build script, such as a `package.json'.
