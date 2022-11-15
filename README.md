# Setting-Up-GraphQL-With-Apollo

<p> Note: You will need to use node version 14.x.x to run this assignment </p>

## Step 1: Downloading the starter files from GitHub.

Save them into a local folder and run:
```
npm install
```
followed by
```
npm run dev
```

### You can check the package.json to see that running npm run dev is equivalent to running next dev. Once this is working, navigate to localhost:3000. You should see something like this: 

<img width="1025" alt="Screenshot 2022-11-15 at 4 38 00 PM" src="https://user-images.githubusercontent.com/94776104/202039783-5408f0d5-da07-4206-80c6-94fedfbe4a44.png">

## Step 2: Starting the back end

### Navigate to the backend folder within the same project directory.From that directory, run npm install, followed by npm run build, followed by npm run develop. Then, navigate to localhost:1337 in your browser to confirm that Strapi is running. Select the localhost:1337/admin link to navigate to the login page and log in to your Strapi account. 

## Step 3: Creating a user

- You can now use the front end running on localhost:3000 to create a user in Strapi instead of manually creating it in the Strapi UI.

- Navigate to localhost:3000 and select the Sign up link at the top right. Input a username, email, and password to complete the form. Afterward, navigate back to your Strapi dashboard and view the new user within the user list.

- Next, navigate to Roles & Permissions. Select the Public role and add your newly created user to that role by searching for the username at the top right of the page. Next, allow full access to the new user. 

## Step 4: Adding Restaurants

- To populate the main page UI with restaurants, navigate to the Strapi restaurant collection. Then, you should input restaurants.

- Now, fill in the Name and Description fields and upload a picture for the restaurant. There are no content requirements, but you need to fill in all fields for the app to work. Please add at least two restaurants. After saving your restaurants, refresh your UI to see them populated in cards.

## Step 5: Learning where the Apollo Client design pattern is used

With the Apollo Client, you can easily determine the state of the HTTP calls between your UI and DAL. In the example below, the GQL query can return “loading,” “error,” or “data,” depending on which one is the correct response. This allows for each state to be handled with a short code.

```
import { gql, useQuery } from '@apollo/client';
 
const Username = () => {
  const { loading, error, data } = useQuery(gql`
    {
      me {
        username
      }
    }
  `);
 
  if (loading) return <text>Loading...</text>;
  if (error) return (
    <text>Error! ${error.message}</text>
  );
  if (!data || !data.user) return (
    <text>Could not find user :(</text>
  );
 
  return (
    <text>Your username: {data.me.username}</text>
  );
}
```

### Screenshot of Strapi restaurant collection and main UI populated with restaurants:

<img width="1440" alt=" Strapi restaurant collection" src="https://user-images.githubusercontent.com/94776104/202040850-6491ec10-6edb-4e3b-9775-16fc464be628.png">
<img width="1440" alt=" UI populated with restaurants" src="https://user-images.githubusercontent.com/94776104/202040884-2dd5f9f1-b1be-422f-b0d1-927caa633630.png">


