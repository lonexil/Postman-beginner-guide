# A  Beginner Guide For Postman
## Introduction
If you have ever tried working with APIs, you probably lnow how coonfusing itncan get at first. All requests, response and headers flying around. Thats where POSTMAN comes in.
Postman is a simple but powerful tool that helps developers test organize and underrstand APIs without stress. Instead of writing long curl command code just to see how an APIs works, you can use postman's clean interface to send request, view responses and even save everything in one place

## 2. Getting Started With Postman
Think of postman like your control room it's where you can send requests, and receive responses.
### 1. Setting Postman Up
To get started:
- Go to https://www.postman.com/downloads/ 
- Download the version for your operating system (Windows, MacOS, or linux).
- Once installed, open it you will then be asked to sign in or create an account.
(signing in helps you save and sync your work across all devices )
If you get a pop up about your window firewall, just allow postman on both private and public networks (like home and work).
 This ensures that it can send request properly
### 2. Understanding the interface
When you open the postman , the layout migh eem a little bit intimidating, but here is what matters most
- Request Builder:
This is the big box at the top, Here you eneter your API URL (the endpoint) and choose the method (GET, POST, PUT, DELETE eTC) from the drop down.

- Params, Auth, Headers, Body Tabs:
Thes tabs below the request bar let you customize your request for example, adding parameters, authentication keys, or JSON data

- Send Button:
The magic, once everything is set, hit SEND to make your request.

- Response Section
This is where the API's reply appears it could be JSON data, an error message, or status codes like 200 OK, 404 Not Found. etc.

### 3. Creating your first workspace
A workspace is simply a project space a place to organize your API requests and collections
you can:

- create a personal workspace for your learning or projects

- Or collaborate with others (once you are more advanced)
For now you can just stick to your personal workspace, its private and perfect for experimentation

## 3. Making Your First Request
Now that you have your postman all setup , lets make your first API request. we will be using jsonplaceholder a free test API. It's perfect for practce as it does not require any authentication or setup.

- Step 1 : Open a New request tab 
Once you open postman click "+New tab" at the top . This open  a blank request window where we will enter our first API endpoint

- Step 2: Choose the request type
On the left of the reuest bar, you will see a drop down that says GET. Leave it as GET for now, this is the request type used to retrieve data.

- Step 3: Enter your url
In the request box paste this endpoint:

``` https://jsonplaceholder.typicode.com/posts/1 ``` 
That simply asked the server to return the post with ID 1.

- step 4 : Hit send
click the send button on the right side
After a few seconds you will see a JSON response appear in the bottom panel. It should look smething like this
``` 
JSON
{
    "userId": 1,
    "Id": 1,
    "title" : "sunt aut facer repellat provident occaecati excepturi optio reprehenderit",
    "body": "quita et suscipit suscipit recusandea"
} 
```

- step 5: Understanding what happened 

what you just did was amke a GET request to the server. the server received your request, processed it, and sent back a response containing dtat in JSON format, a structure most APIS used in exchanging information. 

## 4. Working With POST Requests
So far you have see how to send a simple get request, whcich is basically used to fetch data from an API using jsonplaceholder. But what if you want to send request instead? That's where POST request comes in.
Here's how to it in postman

### - Step 1
Create a new request
- Open postman and click +New Tab or New Request
- Set the method to POST from the dropdown next to the URL bar.

### - Step 2
- Enter your endpoint (URl)
- For practice, you can use this public test API
``` https://jsonplaceholder.typicode.com.posts ```
### - step 3
- Go to the "body" tab
- Select raw.
- choose JSON from the dropdown that says Text
- Now you can type or paste your data in JSON format. Example

``` 
{
    "title":"postman beginner guide",
    "body": Learning how to make POST requests",
    "userId":1
}
``` 
### Step 4 
- Click "send"
- postman will send your data to API, you should see a response like this 
```
{
    "title": Postman Beginner Guide",
    "body": "Learning how to make post requests",
    "userId": 1,
    " Id": 101
}  
```
- The id is usually geberated by the server to show that your new data was created.

### - Tip
If your POST request doesnt go through, double check:
- The method is set to POST not GET 
- You have selected raw-JSON in the Body tab.
- Your JSON data is properlly formated (postman highligh error in red).
## 6. PUT, PATCH and DELETE Requests
So far you have learned how to use GET to retrieve data and POST to create data.
But what happens when you need to update or delete something that already exist?
Thats where DELETE, PUT and PATCH comes in.
Let's break them down :

### - PUT Request - Full update
A put request is used to completely replace a resource in the server. Think of it like overwriting an enetire file. Basically new data replces old one.

Example endpoint
``` https://jsonplaceholder.typicode.com/posts/ 1 ```

Steps
1. Set method to PUT
2. Use the url above. Note the (/1) at the end means we are updating the post with ID 1.
3. Go to the body tab - select raw- choose JSON
4. paste this sample data:
```{
    "Id": 1,
    "title": "updated post title",
    "body": "This is the updated conetent for post 1",
    "userId": 1
}
```
5. Click send 
You will get a response showing the upsated data, confirming that your put request worked.

- Tip : With put the server expects all field , even if only one changed , if you omit afield it might be replaced with null or default values.

### PATCH Request - partial update 
A patch request is used when you only want to update a specific fields of a resource.
It is lighter and faster than PUT because it only changes what you send 
Example endpoint:
``` https://jsonplaceholder.typicode.com/posts/1```

Steps:
1. Set the method to PATCH
2. In the Body tab, use this :
``` {
    "title": "only the title was updated"
}
```
3. Hit send 
You will see that only the title field changes. Th rest of the points stays the same.

### DELETE Request- Removing a Resource
Finally, the DELETE request is used to remvoea resource from the server 
Example endpoint:
``` https://jsonplaceholder.typicode.com/posts/1 ```
Steps 
1. Set the method to delete 
2. paste the url above 
3. click send 
You should see an empty response ({}) or a confirmation message  depending on the API, meaning the deletion was sucessful 
Note: Most real- world APIs require authentication (like an API key or token) to perform delete operations.

## 7. Using Parameters
When working with APIs , you will need to send extra information along with your request. For example to get data for a specific user or to filter results. That sis where parameter comes im
There are two types of parameters in postman:
- Path Parameters - this are part of the URL itself.
- Query Parameters- these are added after (?) in the URL or modify the request
Lets get through both

### - Path parameters
Path parametex are used when the API endpoint itself chnages depending on what you are trying to acess 
Think of it like a navigating through folders , each path points to a specific resource.
Example endpoint:
``` https://jsonplaceholder.typicode.com/posts/1 ```

Here, the 1 at the end is the path parameter, meaning you are asking for the post with ID 1.

### steps
1. set methods to GET
2. paste the URL above int postman
3. Click send.
You will get a response showing only the post with the userID 1.
Tip: path parameters usually represent IDs. Things like users/5 or comments/10

### - Query Parameters 
Query parameters lets you filter or sort data without chnaging the base URL 
They are added after a (?)seperated by (&) if there are multiple.