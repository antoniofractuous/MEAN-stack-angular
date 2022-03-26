# MEAN-stack-angular

*Demonstration of how to implement a simple book register web form using a MEAN stack. The source code used on this project was retrieved from darey.io.*

    Happy learning!

## MEAN STACK

MEAN STACK is a combination of the following components:

- **MongoDB** document based NoSQL database program that stores and allows us to retreive data.

- **Express** a back-end application framework that makes requests to the database for reads and writes.

- **Angular** Front-end application framework that handles client and server requests.

- **Node.js** JavaScript runtime environment that accepts requests and displays results to the end user. 

## Launching your EC2 Instance

So, first we need to create an account on AWS. Then we need to sign into our AWS account and setup a new Elastic Compute Cloud (EC2) instance, "mean-stack" can be our new EC2 instance's name.

To do that we click on the search box and type "EC2". Then we click on where it says "Virtual Servers in the Cloud":

![EC2-lookup](./images/EC2-lookup4.png)

We can setup an EC2 free-tier instance such as the: "t2.micro family with Ubuntu Server 20.04 LTS HV". To do so we click on "Launch Instance" and select the previously mentioned free-tier instance. We can see steps of the process on the images listed below:

![launch-instance](./images/launch-instance.png)

![ubuntu](./images/ubuntu-server.png)

![free-tier-instance](./images/free-tier-instance2.png)

![configure-security-group](./images/configure-security-group2.png)

![create-private-key](./images/create-private-key2.png)

- As we are setting up our new instance, we give a name to our private key using a ".pem" file format and download it from AWS.

- We choose a new security group with default settings. Keep in mind that these settings can be changed in the future. Then we allow access from all IP addresses, this is ideal for testing purposes only.

- Once our instance is up and running, we connect to it using our terminal.

**NOTE**: *.pem stands for "Privacy Enhanced Mail" which a file format that supports encryption, digital signatures and digital certificates as well as private and public key methods.*

**NOTE**: *Ubuntu is one of many Linux distributions*

## Connecting to your EC2 Instance

If you have macOS you can just press 'cmd spacebar' and type in 'terminal' to open the terminal.

If you have Windows you will need to download an SSH client such as "Putty"or "MobaXterm". You can download any of these by typing "Putty"or "MobaXterm" on Google so can download whichever you prefer from their website. 

The following website includes information you on how to do the next steps after you have downloaded your SSH client on Windows: 

https://www.clickittech.com/aws/connect-ec2-instance-using-ssh/

**NOTE**: *You can get your ipv4 (public-ip address) from AWS:*

![ipv4](./images/ipv4.png)

We can see on the images below how to SSH into our EC2 instance using macOS:

- We start our instance by selecting our instance and the clicking on "Instance State" then we click "Start instance".

- Once our instance is up and running, we select it and click on connect.

![start-instance](./images/start-instance.png)

![connect-instance](./images/connect-instance2.png)

- We click on the 'SSH client' tab and then copy the SSH command that is listed under "Example:"

![ssh](./images/ssh-connect.png)

Once we have copied the SSH command, we change directories to our Downloads folder because that is where our private key is located. So on our terminal we run:

`cd Downloads`

We paste the SSH command into our terminal, then we input yes. If this is the first time that you are doing this, congratulations!! You have just launched your first server in the clouds!

![EC2-instance](./images/EC2-instance.png)

**NOTE**: Here is an explanation of the SSH command:

`ssh -i "private-key.pem" username@ipv4`

- `ssh`: Means 'secure shell' and it is a protocol used to securely connect to a remote server/system.

- `-i`: Is a flag that specifies an alternate identification file to use for public key authentication.

- `private-key`: Is a variable in cryptography that is used with an algorithm to encrypt and decrypt data. Private keys should only be shared with the key's generator or parties authorized to decrypt the data.

- `username`: The Linux distribution that you are using. In this case we are using "Ubuntu".

- `ipv4`: Is the public IP of your EC2 instance. It is the underlying technology that makes it possible for us to connect our devices to the web.

**NOTE**: *You can either use your EC2 instance's public ip address or DNS name.*

## Updating your EC2 Instance
 So, once we SSH into our EC2 instance we update the list of available packages:

`sudo apt update`

Then we install a newer version of the packages we have:

`sudo apt upgrade`

## Installing Node.js

We will be using Node.js to set up the Express routes and AngularJS controllers so we run:

`sudo apt install nodejs -y`

## Installing MongoDB

MongoDB stores our data in JSON-like documents.

In this case we will be adding book records to our MongoDB that contain the following: *book name, isbn number, author, and number of pages.*

To install MongoDB we use:

`sudo apt mongodb -y`

Then we start the server:

`sudo service mongodb start` 

We verify that the service is running:

 `sudo systemctl status mongodb`

![mongodb-status](./images/status-mongodb2.png)

## Installing Node Package Manager 

`sudo apt install -y npm`

We also need to install the ‘body-parser’ package to help us process JSON files passed in requests to the server:

`sudo npm install body-parser`

We create a folder named 'Books':

`mkdir Books` 

Then we change directories:

`cd Books`

In our Books directory, we initialize the npm project:

`npm init`

In our root directory 'Books' we create a file named 'server.js':

`vi server.js`

We input or paste the following code in it:

![server.js](./images/books4.png)

## Installing Express and Setting Up Routes to the Server

Express is a minimal and flexible Node.js web application framework that provides features for web and mobile applications. We will use Express to pass book information to and from our MongoDB database.

We also will use Mongoose package which provides a straight-forward, schema-based solution to model our application data. We will use Mongoose to establish a schema for the database to store data of our book register.

So we run:

`sudo npm install express mongoose`

In our 'Books' folder, we create a folder named apps and we change directories to the apps folder:

`mkdir apps && cd apps`

Then we create a file named routes.js:

`vi routes.js`

We input or paste the following code into routes.js:

![routes.js](./images/books-apps.png)


In the 'apps' folder, we create a folder named models:

`mkdir models && cd models`

In the models folder we create a file named book.js:

`mkdir book.js`

We input or paste the following code into book.js:

![book.js](./images/books-apps-models.png)

## Accessing Routes with AngularJS

AngularJS provides a web framework for creating dynamic views in our web applications. In this tutorial, we will use AngularJS to connect our web page with Express and perform actions on our book register.

So we change the directory back to 'Books':

`cd ../..`

And create a folder named 'public':

`mkdir public`

Then we add a file to it named 'script.js' 

`vi script.js`

We input or paste the following code into our script.js file:

![script.js](./images/books-public.png)

In our public folder, we also create a file named 'index.html'

`vi index.html`

We input or paste the following code into it:

![index.html](./images/books-public-html.png)


![index.html](./images/books-public-html2.png)

**NOTE**: The identation of the code does not have to be indented as it appears on the picture. The identation can be way simpler and more practical. However, my `vi` text-editor formatted it that way when I pasted it. (I also tried it with `vim` but it formatted it the same way)

Then we change the directory back to 'Books':

`cd ..`

## Starting the Node Server

So, after changing directories to 'Books' we start our server by running:

`node server.js`

The server is now up and running, we can connect it via port 3300.

Let's access it from our browser. However, before doing that, we will need to open a TCP on port 3300 in our AWS Web Console for our EC2 instance and allow access from anywhere. (not ideal for security reasons, but it is good for testing purposes)

![EC2 port 3300](./images/tcp-3300.png)

Ultimately, we access our book register web application from the internet with our browser using our EC2 instance's Public IP address or Public DNS name. 'http://localhost:3300'.

**NOTE**: *Your localhost is your EC2 instance public-ipv4-address.*

![book register website](./images/book-register-website.png)

 Congrats!! You have just implemented a simple book register web form using a MEAN stack!