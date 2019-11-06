![titulo](/docs/titulo.JPG)

# NodeJS-Heroku

Upload a simple NodeJS web API to Heroku without using Docker.

## Technologies

- [NodeJS Express](https://expressjs.com/pt-br/)
- [Heroku](https://www.heroku.com/)

## Topics

- [NodeJS](#nodejs)
- [Heroku](#heroku)

### NodeJS

Create a directory for your NodeJS web API.  
By running this command in a terminal, create a _package.json_ file:

```console
npm init
```

Edit the file by adding the following dependencies:

```js
{
	...
	"dependencies": {
		"cors": "^2.8.5",
		"express": "^4.16.4"
	}
	...
}
```

Create the _node_modules_ folder with this command:

```console
npm install
```

Create an _index.js_ file containing this code:

```js
const express = require('express');
const app = express();
var cors = require('cors');

app.use(
	cors({
		credentials: true,
		origin: true
	})
);
app.options('*', cors());

app.get('/', (req, res) => res.send('Working!!!'));

app.listen(process.env.PORT || 3000, function() {
	console.log('server running on port 3000', '');
});
```

Run the web API with the following command:

```console
node index
```

Open the browser with the URL below:

```
http://localhost:3000/
```

This will be the result:

![node01](/docs/node01.JPG)

Your web API is WORKING!  
Time to upload it to Heroku.

### Heroku

Heroku is a cloud platform that allows applications be hosted at will. It's mostly used for web APIs. Go to Heroku website and sign up or sign in.

In your machine, install the latest version of Heroku CLI [here](https://devcenter.heroku.com/articles/heroku-cli).

In the web API root folder, create a _Procfile_, which is a Heroku file that specifies the commands that are executed by the app on startup. Write the following line within the file:

```
web: node index.js
```

Create a _.git_ folder with this command:

```console
git init
```

Create a _.gitignore_ manually containing this line:

```
/node_modules
```

Your project will look like this:

![node02](/docs/node02.JPG)

Authenticate with Heroku by running this command and follow the instructions that will be displayed in the terminal:

```console
heroku login
```

Run the following command to create a project in Heroku. It will receive a random name but you can change it.

```console
heroku create
```

Now, run the commands below to commit your web API to Heroku's new project:

```console
git add *;
git commit -m "First commit";
git push heroku master;
```

The console will show the upload progress like this:

![heroku01](/docs/heroku01.JPG)

Check if any error has occurred by running:

```console
heroku logs
```

Finally, open the project by running this command:

```console
heroku open
```

This will be the result:

![heroku02](/docs/heroku02.JPG)

## Conclusion

We have successfully uploaded our NodeJS web API to Heroku without using Docker.  
Also, it was not needed to interact directly with Heroku website to create the app.

## References

[How To Deploy Nodejs App To Heroku](https://appdividend.com/2018/04/14/how-to-deploy-nodejs-app-to-heroku/)
