# Front-End Developer

AWS Learning Path

## Introduction {collapsible="true" default-state="expanded"}

### What is a Front-End Developer?

As a front-end or mobile developer, you build feature-rich web and mobile applications.
You use popular front-end web or mobile frameworks including React, React Native, Vue, Angular, Iconic or iOS/Android to
build the presentation layer of your app (e.g., the layout, the positioning of text and images, colors, fonts, buttons,
etc.). You also work with backend APIs and services to add interactivity to your web or mobile application.

Using Amplify, you can use your existing front-end skillset to add cloud functionality into your application such as
auth, data, analytics, push notifications, and more.

### Objectives

- **Host Web or Mobile Application**
    - Build and host a web or mobile application on the AWS Global content delivery network (CDN).
- **Add Authentication**
    - Add authentication to your application to enable sign-in and sign-out.
- **Add Database and Storage**
    - Add a GraphQL API, database, and storage solution to your application.

## Build a Full-Stack React Application {collapsible="true" default-state="expanded"}

Create a simple web application using AWS Amplify

### Introduction: Build a Full-Stack React Application

#### Overview

In this tutorial, you will create a simple full-stack web application using AWS Amplify, a set of tools and services
including a web hosting service.
In the first module, you will build and host a React application on AWS.
Through the remaining four modules, you will initialize a local app using the CLI, add authentication, add a GraphQL API
and database, and update your app to store images.

#### What you will accomplish

This tutorial will walk you through the steps to create a simple web application discussed above. You will learn:

- **Hosting**: Build and host a React application on the AWS global content delivery network (CDN)
- **Authentication**: Add auth to your app to activate sign-in and sign-out
- **Database and storage**: Add a GraphQL API, database, and storage solution

### Module 1: Deploy and Host a React App {collapsible="true" default-state="expanded"}

In this module, you will create a React application and deploy it to the cloud using the AWS Amplify web hosting service

#### Overview

AWS Amplify provides a Git-based CI/CD workflow for building, deploying, and hosting single-page web applications or
static sites with serverless backends. Upon connecting to a Git repository, Amplify determines the build settings for
both the frontend framework and any serverless backend resources configured with the Amplify CLI, and automatically
deploys updates with every code commit.

In this module, we will begin by creating a new React application and push it to a GitHub repository. Then, we will
connect the repository to [AWS Amplify](https://aws.amazon.com/amplify/?e=gs2020&p=build-a-react-app-one) web hosting
and deploy it to a globally available content delivery network (CDN) hosted on an amplifyapp.com domain. Next, we will
demonstrate continuous deployment capabilities by making changes to the React application and push a new version to the
main branch, which will automatically kick off a new deployment.

#### What you will accomplish

In this module, you will:

- Create a React application
- Initialize a GitHub repository
- Deploy your app with AWS Amplify
- Implement code changes and redeploy your app

#### Key concepts

**React application** – React is a JavaScript web application library that enables developers to quickly build
performant single-page applications.

**Git** – A version control system that allows developers to store files and maintain and update relationships between
files and directories, versions, and changes to the files.

#### Implementation

##### Create a new React application

The easiest way to create a React application is by using the command create-react-app. Install this package using the
following command in your command prompt or terminal:

```bash
npx create-react-app amplifyapp
cd amplifyapp
npm start
```

##### Initialize GitHub repository

In this step, you will create a GitHub repository and commit your code to the repository. You will need a GitHub account
to complete this step—if you do not have an
account, [sign up here](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).

a. Create a new [GitHub repo](https://github.com/new) for your app.

![Front_End_GitHub_Repository_Module_1](Front_End_GitHub_Repository_Module_1.png)

b. Open a new terminal and navigate back to your app's root folder, for example, _amplifyapp_.

c. Using create-react-app will automatically initialize the git repo and make an initial commit. If you are trying to
deploy an existing React application where git has not been initialized, make sure to input the following commands
before continuing:

```bash
git init
git add .
git commit -m "initial commit"
```

d. If you have never used GitHub on your computer,
follow [these steps](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)before continuing to allow
connection to your account.

Push the application to the new GitHub repo by executing the following commands in your command line interface:

```bash
git remote add origin git@github.com:username/reponame.git
git branch -M main
git push -u origin main
```

##### Log into the AWS Management Console

Open the [AWS Management Console](https://us-west-1.console.aws.amazon.com/console/home?region=us-west-1) in a new
browser window, so you can keep this step-by-step guide open. When the screen loads, enter your user name and password
to get started. Then enter Amplify in the search bar and select **AWS Amplify** to open the service console.

![AWS Amplify](AWS_Amplify.jpg)

##### Deploy your app with AWS Amplify

In this step, you will connect the GitHub repository you just created to the AWS Amplify service. This will enable you
to build, deploy, and host your app on AWS.

a. In the AWS Amplify service console, select **Get Started** under **Amplify Hosting**.

![Getting Started](amplify_getting_started.jpg)

b. Select GitHub as the repository service and select **Continue**.

![Hosting](amplify_hosting.jpg)

c. Authenticate with GitHub and return to the Amplify console. Choose the repository and main branch you created
earlier, then select **Next**.

![add branch](add_branch.jpg)

d. Accept the default build settings and select **Next**.

![configure](configure.jpg)

e. Review the final details and choose **Save and deploy**.

![save and deploy](save_and_deploy.jpg)

f. AWS Amplify will now build your source code and deploy your app at https://...amplifyapp.com.

![amplify react](amplify_react.jpg)

g. Once the build completes, select the thumbnail to see your web app up and running live.

![react app](react_app.jpg)

##### Automatically deploy code changes

In this step, you will make some changes to the code using your text editor and push the changes to the main branch of
your app.

a. Edit **src/App.js** with the code below and save.

```Javascript
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <img src={logo} className='App-logo' alt='logo' />
        <h1>Hello from V2</h1>
      </header>
    </div>
  );
}

export default App;
```

b. Push the changes to GitHub in the command prompt (Windows) or terminal (macOS) to automatically kick off a new build:

```bash
git add .
git commit -m “changes for v2”
git push origin main
```

c. Once the build is complete, select the thumbnail in the AWS Amplify console to view your updated app.

![react app v2](react_app_v2.jpg)

#### Conclusion

You have deployed a React application in the AWS Cloud by integrating with GitHub and using AWS Amplify. With AWS
Amplify, you can continuously deploy your application in the cloud and host it on a globally available CDN.

Next, we will create a local version of the app to continue development and add new features.

### Module 2: Initialize a Local App {collapsible="true" default-state="expanded"}

#### Overview

Now that we have initialized a new Amplify project in our account, we want to bring it down into our local environment,
so we can continue development and add new features.

In this module, you will install the Amplify CLI and initialize the Amplify project using the CLI.

#### What you will accomplish

In this module, you will:

- Install and configure the Amplify CLI
- Initialize the Amplify app

#### Key concepts

**Amplify CLI** – The Amplify CLI allows you to create, manage, and remove AWS services directly from your terminal.

#### Implementation

##### Install the Amplify CLI

The Amplify command line interface (CLI) is a unified toolchain to create AWS Cloud services for your app, following a
simple, guided workflow. Let’s go ahead and install the Amplify CLI using the command prompt (Windows) or the terminal (
macOS). Note: This command can be run in any directory in your command prompt/terminal because the “-g” indicates the
binary will be installed globally on your system.

```bash
npm install -g @aws-amplify/cli
```

##### Configure the Amplify CLI

AWS Identity and Access Management (IAM) enables you to manage users and user permissions in AWS. The CLI uses IAM to
create and manage services programmatically on your behalf through the CLI.

To configure the CLI, run the configure command. To see a video walkthrough of the CLI configuration process, see
Installing & Configuring the AWS Amplify CLI below.

```bash
amplify configure
```

##### Initialize the Amplify app

Next, we will deploy a backend and initialize the backend environment locally.

a. In the Amplify console, select **Backend environments** and choose **Get started**. Wait for the backend to be
deployed.

![graph ql](amplify-react-graphql.jpg)

b. On the **Backend environments** tab, choose **Launch Studio**.

![graph ql 2](amplify-react-graphql2.jpg)

c. Return to the **Backend environments** tab and expand the L**ocal setup instructions** section. Copy the command to
your clipboard and open the terminal on your computer.

![graph ql 3](amplify-react-graphql3.jpg)

d. Paste the command into your terminal and follow the setup instructions.

```bash
? Choose your default editor: Visual Studio Code
? Choose the type of app that you're building javascript
? What javascript framework are you using react
? Source Directory Path:  src
? Distribution Directory Path: build
? Build Command:  npm run-script build
? Start Command: npm run-script start
? Do you plan on modifying this backend? Y
```

#### Conclusion

You have initialized the Amplify project and are now ready to start adding features. In the next module, we will add an
entire user authentication flow with just a few lines of code.

To view your Amplify project in the dashboard at any time, you can now run the following command:

```bash
amplify console
? Which site do you want to open? AWS console
```

### Module 3: Add Authentication {collapsible="true" default-state="expanded"}

#### Overview

The next feature you will be adding is authentication. In this module, you will learn how to authenticate a user with
the Amplify CLI and libraries, leveraging Amazon Cognito, a managed user identity service.

You will also learn how to use the Amplify UI component library to scaffold out an entire user authentication flow,
allowing users to sign up, sign in, and reset their password with just a few lines of code.

#### What you will accomplish

In this module, you will:

- Install Amplify libraries
- Create and deploy an authentication service
- Configure your React app to include authentication

#### Key concepts

**Amplify libraries** – The Amplify libraries allow you to interact with AWS services from a web or mobile application.

**Authentication** – In software, authentication is the process of verifying and managing the identity of a user using
an authentication service or API.

#### Implementation

##### Install the Amplify Libraries

We will need two Amplify libraries for our project. The main **aws-amplify library** contains all the client-side
APIs for interacting with the various AWS services we will be working with, and the **@aws-amplify/ui-react library**
contains framework-specific UI components. Install these libraries in the root of the project.

```bash
npm install aws-amplify @aws-amplify/ui-react
```

##### Create the authentication service

To create the authentication service, use the Amplify CLI:

```bash
amplify add auth

? Do you want to use the default authentication and security configuration? Default configuration
? How do you want users to be able to sign in? Username
? Do you want to configure advanced settings? No, I am done.
```

##### Deploy the authentication service

Now that the authentication service has been configured locally, we can deploy it by running the Amplify push command:

```bash
amplify push --y
```

##### Configure the React project with Amplify resources

The CLI has created and will continue to update a file called **aws-exports.js** located in the src directory of our
project. We will use this file to let the React project know about the different AWS resources that are available in our
Amplify project.

To configure our app with these resources, open **src/index.js** and add the following code below the last import:

```bash
import { Amplify } from 'aws-amplify';
import config from './aws-exports';
Amplify.configure(config);
```

##### Add the authentication flow in App.js

Next, open **src/App.js** and update with the following code:

```Javascript
import logo from './logo.svg';
import '@aws-amplify/ui-react/styles.css';
import {
  withAuthenticator,
  Button,
  Heading,
  Image,
  View,
  Card,
} from '@aws-amplify/ui-react';

function App({ signOut }) {
  return (
    <View className='App'>
      <Card>
        <Image src={logo} className='App-logo' alt='logo' />
        <Heading level={1}>We now have Auth!</Heading>
      </Card>
      <Button onClick={signOut}>Sign Out</Button>
    </View>
  );
}

export default withAuthenticator(App);
```

In this code, we've used the **withAuthenticator** component. This component will scaffold out an entire user
authentication flow allowing users to sign up, sign in, reset their password, and confirm sign-in for multifactor
authentication (MFA). We have also added a **Sign Out** button to log users out.

##### Run the app locally

Wait for the resources to finish deploying and then run the app to see the new Authentication flow protecting the app:

```bash
npm start
```

![sign-in](sign-in.jpg)

Here, you can try signing up, which will send a verification code to your email. Use the verification code to log in to
the app. When signed in, you should see a `Sign Out` button, which signs you out and restarts the authentication flow.

![emailed you](emailed-you.jpg)

##### Setup Ci/CD of the frontend and backend

Next, we need to configure the Amplify build process to add the backend as part of the continuous deployment workflow.
From your terminal window run:

```bash
amplify console
? Which site do you want to open? AWS console
```

This will open the Amplify console. From the navigation pane, choose **App settings > Build settings** and modify it to
add the **backend section (lines 2–7 in the code below)** to your amplify.yml. After making the edits, choose **Save**.

```yaml
version: 1
backend:
  phases:
    build:
      commands:
        - '# Execute Amplify CLI with the helper script'
        - amplifyPush --simple
frontend:
  phases:
    preBuild:
      commands:
        - yarn install
    build:
      commands:
        - yarn run build
  artifacts:
    baseDirectory: build
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```

Scroll down to **Build image settings** and choose **Edit**. Select the **Add package version** override dropdown and
select **Amplify CLI**. It should default to the latest version, as shown in the image.

![edit build image settings](edit-build-image-settings.jpg)

Next, update your frontend branch to point to the backend environment you just created. Under the branch name, choose *
*Edit**, and then point your **main** branch to the **staging** backend you just created. Choose **Save**.

![cd/ci](cd_ci.jpg)

![edit target backend](edit-target-backend.jpg)

If you see the message _Please set up a service role..._, follow the instructions provided before continuing to set up
and attach a service role to your app.

##### Deploy the changes to the live environment

Now return to your local terminal window and deploy the changes to GitHub to begin a new build in the Amplify console:

```bash
git add .
git commit -m "added auth"
git push origin main
```

#### Conclusion

You have now added user authentication to your app with just a few lines of code. In the next module, we will add an API
to your app.

### Module 4: Add a GraphQL API and Database {collapsible="true" default-state="expanded"}

#### Overview

Now that we have created and configured the app with authentication, let's add an API.

In this module, you will add an API to your app using the Amplify CLI and libraries. The API you will be creating is a
GraphQL API that uses AWS AppSync (a managed GraphQL service) which is backed by Amazon DynamoDB (a NoSQL database). (
For an introduction to GraphQL, see the [GraphQL website](https://graphql.org/learn/).)

The app we will be building will be a Notes app that will allow users to create, delete, and list notes. This example
will give you a good idea of how to build many popular types of CRUD+L (create, read, update, delete, and list)
applications.

#### What you will accomplish

In this module, you will:

- Create and deploy a GraphQL API
- Write frontend code to interact with the API

#### Key concepts

**API** – Provides a programming interface that allows communication and interactions between multiple software
intermediaries.

**GraphQL** – A query language and server-side API implementation based on a typed representation of your application.
This API representation is declared using a schema based on the [GraphQL](https://graphql.org/learn/) type system.

#### Implementation

##### Create a GraphQL API and database

a. Add a GraphQL API to your app by running the following command from the root of your app directory:

```bash
amplify add api

? Select from one of the below mentioned services: GraphQL
? Here is the GraphQL API that we will create. Select a setting to edit or continue: Continue
? Choose a schema template: Single object with fields (e.g., "Todo" with ID, name, description)
? Do you want to edit the schema now? (Y/n) yes
```

b. Open the GraphQL schema in your text editor: **/amplify/backend/api/<api_name>/schema.graphql**.

Update the file with the following schema:

```graphql
type Note @model @auth(rules: [{ allow: public }]) {
  id: ID!
  name: String!
  description: String
}
```

c. Save the file.

##### Deploy the API

Now that the API has been configured locally, it is time to deploy it. To do so, run the Amplify push command:

```bash
amplify push --y
```

This will do three things:

1. Create the AWS AppSync API
2. Create a DynamoDB table
3. Create the local GraphQL operations in a folder located at src/graphql that you can use to query the API

To view the GraphQL API in your account at any time, run the following command and then select GraphQL API in the left
navigation pane:

```bash
amplify console api

> Choose GraphQL
```

To view the Amplify app in your account at any time, run the following command:

```bash
amplify console
? Which site do you want to open? AWS console
```

##### Write front-end code to interact with the API

Now that the backend has been deployed, let's write some code to allow users to create, list, and delete notes.

Update src/App.js with the following code:

```Javascript
import React, { useState, useEffect } from 'react';
import './App.css';
import '@aws-amplify/ui-react/styles.css';
import { API } from 'aws-amplify';
import {
  Button,
  Flex,
  Heading,
  Text,
  TextField,
  View,
  withAuthenticator,
} from '@aws-amplify/ui-react';
import { listNotes } from './graphql/queries';
import {
  createNote as createNoteMutation,
  deleteNote as deleteNoteMutation,
} from './graphql/mutations';

const App = ({ signOut }) => {
  const [notes, setNotes] = useState([]);

  useEffect(() => {
    fetchNotes();
  }, []);

  async function fetchNotes() {
    const apiData = await API.graphql({ query: listNotes });
    const notesFromAPI = apiData.data.listNotes.items;
    setNotes(notesFromAPI);
  }

  async function createNote(event) {
    event.preventDefault();
    const form = new FormData(event.target);
    const data = {
      name: form.get('name'),
      description: form.get('description'),
    };
    await API.graphql({
      query: createNoteMutation,
      variables: { input: data },
    });
    fetchNotes();
    event.target.reset();
  }

  async function deleteNote({ id }) {
    const newNotes = notes.filter((note) => note.id !== id);
    setNotes(newNotes);
    await API.graphql({
      query: deleteNoteMutation,
      variables: { input: { id } },
    });
  }

  return (
    <View className='App'>
      <Heading level={1}>My Notes App</Heading>
      <View as='form' margin='3rem 0' onSubmit={createNote}>
        <Flex direction='row' justifyContent='center'>
          <TextField
            name='name'
            placeholder='Note Name'
            label='Note Name'
            labelHidden
            variation='quiet'
            required
          />
          <TextField
            name='description'
            placeholder='Note Description'
            label='Note Description'
            labelHidden
            variation='quiet'
            required
          />
          <Button type='submit' variation='primary'>
            Create Note
          </Button>
        </Flex>
      </View>
      <Heading level={2}>Current Notes</Heading>
      <View margin='3rem 0'>
        {notes.map((note) => (
          <Flex
            key={note.id || note.name}
            direction='row'
            justifyContent='center'
            alignItems='center'
          >
            <Text as='strong' fontWeight={700}>
              {note.name}
            </Text>
            <Text as='span'>{note.description}</Text>
            <Button variation='link' onClick={() => deleteNote(note)}>
              Delete note
            </Button>
          </Flex>
        ))}
      </View>
      <Button onClick={signOut}>Sign Out</Button>
    </View>
  );
};

export default withAuthenticator(App);
```

Our app has three main functions:

1. fetchNotes—This function uses the API class to send a query to the GraphQL API and retrieve a list of notes.
2. createNote—This function also uses the API class to send a mutation to the GraphQL API. The main difference is that
   in this function we are passing in the variables needed for a GraphQL mutation so that we can create a new note with
   the form data.
3. deleteNote - Like createNote, this function is sending a GraphQL mutation along with some variables, but instead of
   creating a note, we are deleting a note.

##### Run the app

To test out the app, run the start command:

```bash
npm start
```

#### Conclusion

You have now created a Notes app. Using AWS Amplify, you added a GraphQL API and configured create, read, and delete
functionality in your app. In the next module, we will add a storage service to your app.

### Module 5: Add Storage {collapsible="true" default-state="expanded"}

#### Overview

Now that we have the notes app working, let's add the ability to associate an image with each note. In this module, you
will use the Amplify CLI and libraries to create a storage service using Amazon S3. You will then update the GraphQL
schema you created in the previous module to associate an image with each note. Finally, you will update the React app
to enable image uploading, fetching, and rendering.

#### What you will accomplish

In this module, you will:

- Create a storage service
- Update a GraphQL schema
- Update your React app

#### Key concepts

**Storage service** - Storing and querying for files, such as images and videos, is a common requirement for most
applications. One option to do this is to Base64 encode the file and send as a string to save in the database. This
comes with disadvantages, such as the encoded file being larger than the original binary, the operation being
computationally expensive, and the added complexity around encoding and decoding properly. Another option is to have a
storage service specifically built and optimized for file storage. Storage services like Amazon S3 exist to make this as
easy, performant, and inexpensive as possible.

#### Implementation

##### Create storage service

To add image storage functionality, we'll use the Amplify storage category. You can keep the default selections for most
of the options below, but be sure to select the **create/update**, **read**, and **delete** options individually by
pressing the spacebar on each before pressing **Enter** to continue with the prompt.

```bash
amplify add storage

? Select from one of the below mentioned services: Content (Images, audio, video, etc.)
? Provide a friendly name for your resource that will be used to label this category in the project: imagestorage
? Provide bucket name: <your-unique-bucket-name>
? Who should have access: Auth users only
? What kind of access do you want for Authenticated users? create/update, read, delete
? Do you want to add a Lambda Trigger for your S3 Bucket? (y/N) no
```

##### Update the GraphQL schema

Next, open **amplify/backend/api/notesapp/schema.graphql** and update it with the following schema:

```graphql
type Note @model @auth(rules: [{ allow: public }]) {
  id: ID!
  name: String!
  description: String
  image: String
}
```

Make sure to save the file.

##### Deploy storage service and API updates

Now that the storage service has been configured locally, and we have updated the GraphQL schema, we can deploy the
updates by running the Amplify push command:

```bash
amplify push --y
```

##### Update the React app

Now that the backend has been updated, let's update the React app to add the functionality to upload and view images for
a note. Open **src/App.js** and make the following changes.

a. First, add the Storage class and Image component to your Amplify imports:

```Javascript
import { API, Storage } from 'aws-amplify';
import {
  Button,
  Flex,
  Heading,
  Image,
  Text,
  TextField,
  View,
  withAuthenticator,
} from '@aws-amplify/ui-react';
```

b. Update the fetchNotes function to fetch an image if there is an image associated with a note:

```Javascript
async function fetchNotes() {
  const apiData = await API.graphql({ query: listNotes });
  const notesFromAPI = apiData.data.listNotes.items;
  await Promise.all(
    notesFromAPI.map(async (note) => {
      if (note.image) {
        const url = await Storage.get(note.name);
        note.image = url;
      }
      return note;
    }),
  );
  setNotes(notesFromAPI);
}
```

c. Update the createNote function to add the image to the local image array if an image is associated with the note:

```Javascript
async function createNote(event) {
  event.preventDefault();
  const form = new FormData(event.target);
  const image = form.get('image');
  const data = {
    name: form.get('name'),
    description: form.get('description'),
    image: image.name,
  };
  if (!!data.image) await Storage.put(data.name, image);
  await API.graphql({
    query: createNoteMutation,
    variables: { input: data },
  });
  fetchNotes();
  event.target.reset();
}
```

d. Update the deleteNote function to delete files from storage when notes are deleted:

```Javascript
async function deleteNote({ id, name }) {
  const newNotes = notes.filter((note) => note.id !== id);
  setNotes(newNotes);
  await Storage.remove(name);
  await API.graphql({
    query: deleteNoteMutation,
    variables: { input: { id } },
  });
}
```

e. Add an additional input to the form in the return block:

```Javascript
<View name='image' as='input' type='file' style={{ alignSelf: 'end' }} />
```

f. When mapping over the notes array, render an image if it exists:

```Javascript
{
  notes.map((note) => (
    <Flex
      key={note.id || note.name}
      direction='row'
      justifyContent='center'
      alignItems='center'
    >
      <Text as='strong' fontWeight={700}>
        {note.name}
      </Text>
      <Text as='span'>{note.description}</Text>
      {note.image && (
        <Image
          src={note.image}
          alt={`visual aid for ${notes.name}`}
          style={{ width: 400 }}
        />
      )}
      <Button variation='link' onClick={() => deleteNote(note)}>
        Delete note
      </Button>
    </Flex>
  ));
}
```

g. Commit your changes and push to GitHub. Then wait for the build to complete to see your full app live!

```bash
git add .
git commit -m "Added graphql and storage"
git push origin main
```

##### Run the app

To test out the app, run the start command:

```bash
npm start
```

You should now be able to optionally upload an image for each note.

##### Deleting the resources

**Removing individual services**

To remove individual services, you can use the Amplify remove command:

```bash
amplify remove auth

? Choose the resource you would want to remove: <your-service-name>
```

Then run the Amplify push command:

```bash
amplify push
```

**Deleting the entire project**

To delete the project and the associated resources, you can run the Amplify delete command:

```bash
amplify delete
```

#### Conclusion

You have deployed a web application using AWS Amplify! You have added authentication to your app allowing users to sign
up, sign in, and manage their account. The app also has a scalable GraphQL API configured with an Amazon DynamoDB
database, allowing users to create and delete notes. You have also added file storage using Amazon S3 so that users can
upload images and view them in their app.

<seealso>
[Link](https://aws.amazon.com/getting-started/learning-path-front-end-developer/)
</seealso>
