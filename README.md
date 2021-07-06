# Lead manager
This app is going to be used to handle leads of different users.
We are going to use Bootstrap for the stylesheets.

In this README file, you will learn the steps that it took to build it:
## 1. Django Rest Framework
Install django-rest-framework and django-rest-knox (which the last one is used for the auth).
Inside of the requirements.txt you are going to see which are the dependencies. To insall them, pip install requirements.txt.

Serializers allow complex data such as querysets and model instanced to be converted to native Python datatypes that can be then easily rendered into JSON..

Serializers also provide deseralization, allowing parsed data to be ocnverted back into complex types.

## 2. Serializer 
Create a serializer to take the model of leads, the queryset and to convert it to JSON. We will do it with a class of serializer.

This way we turn our lead model into a serializer.

## 3. Creating an API 
Once created the serializer, we need to create the API. We are going to do it inside of the api.py.

We create a viewset, which allows us to create a full CRUD API (Create, Read, Update and Delete) without having to specify specific methods for the functionalities.

We do not have to even create our routes. We can use the default route, which register the endpoint and then we can make the requests to this endpoint.

## 4. Creating URLs 
Create the urls inside of the leadsmanager project, which will include the file of the leads app.

Inside of the leads app urls, we are not going to create explicitly urls, as we are going to use the router from rest_framework.

In the urlpatterns of leads url file, we are gonig ot set that will be equal to the router.urls, which gives us the urls registered for the endpoint o fapi/leads.

## 5. REST API
We can now test the API with Postman. We run first the server, and then go to Postman to: http://localhost:8000/api/leads/. 

We can do a post rqeuest to this url. For the header we are going to add a Content-Type. And the value is application/json. And then for the body we can write:
    {
        "name":"juan",
        "email":"juan@gmail.com",
        "message":"Contactame"
    }

And what we will obtain is:
    {
        "id": 1,
        "name": "juan",
        "email": "juan@gmail.com",
        "message": "Contactame",
        "created_at": "2021-07-03T20:39:43.155856Z"
    }
We sohuld obtain a status of 201, which is a succees status.
We could create another one.

If we now put in the url http://localhost:8000/api/leads/1/, and a GET request, we are going to obtain the information we just have uploaded.

We can do the different request as it is a full API CRUD.

6. ## React implementation
Now it is time to implement React.
First, we will create a django application, and build some folders: static, src and templates (we can do this with mkdir in the terminal).
Then, we are going to init the environment for React: npm init -y.

Then, we are going to open the package.json in an integrated terminal, and install the Webpack: npm i webpack webpack-cli --save-dev.

We configure inside of package json the scripts for dev and build (one for development and the other for production).

Now it is time to install babel, which is the transpiler: npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev.

Next, pull in React dependencies: npm i react react-dom --save-dev.

Then, we have to configure babel with the file of .babelrc.

Finally, we configure webpack inside of webpack.config.js.

## 7. Preparing front-end views
Go to views.py of the frontend app, and create the view with python and inside of template create the React basic structure (index.html).

Moreover, you can include the urls inside of urls.py.

Remember to register this app inside of the settings and include those urls on leadmanager.

## 8. Creating React front-end
Now, we are going to create the index.js inside of src as well as the App.js inside of components folder (which will contain our react application).

So we will create the default structure that will enable us React.

Having done this, we are going to run npm run dev (being in the frontend folder). And we will see that it is created a main.js file inside of static. Which is the compiled JS, which is the JS that is being imported in the HTML.

Take into consideration taht in package.json, if we put in the dev script --watch, we will not have to hard reload every time we have changed something, it will recompile automatically.

## 9. Adding components
We will add some basic components that we will use for this lead manager app. Specifically, we will build:
- Header (inside of layout folder)
- Dashboard (which will contain the following two)
- Leads (a list of the different lists)
- Form (form to put new leads)

Those components will have Boostrap as styling, as this is only a project for practical example (so we are not focusing on styles)

## 10. Install Redux
We are going to use Redux, as we need a single source of truth. As we are going ot have leads and authentication, so we need some form to save our state of the application.

We can install Redux DevTools for Chrome, so we can see a clear image of how the state of the Redux is.

So we go ot our terminal, and put: npm install redux react-redux redux-thunk redux-devtools-extension

Where redux-thunk will allow us to make asynchrnous requests.

## 11. Implementing Redux

One of the first thinks when implementing Redux, is to start with the store.

We are going to create a filde inside of the src folder, which will be called store.js.

There we are going to do the necessary imports:
- createStore: necessary for creating the actual store of Redux.
- applyMiddleware: as we are using thunk
- composeWithDevTools
- thunk
- rootReducer: which will look for a file called index.js inside of the folder reducers