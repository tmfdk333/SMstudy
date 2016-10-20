Build a simple face detection web app leveraging AlchemyAPI on Bluemix

Summary:
Recently, IBM acquires the startup AlchemyAPI to bring deep learning to Watson and make it public on Bluemix. Among AlchemyAPI service, there is an interesting feature called face detection (from its name, we can guess what it is). We build up a simple and interesting web app leveraging this feature, called "Who Are You", which helps you guess who you are from an image. It runs in PHP and employs the powerful face detection API from AlchemyAPI service on Bluemix. 

We choose PHP as runtime because PHP is very lightweight and efficient, and it is widely accepted by the open source world. Besides, Bluemix can support PHP runtime very well. In our app, the app uses only 128MB memory and runs fast. 

Good news is that AlchemyAPI provides an API SDK for PHP environment, while bad news is that it does not support the face detection API. To overcome this issue, we make the following two updates:
(1) Read AlchemyAPI apikey from VCAP_SERVICES variables instead of reading it from a file.
(2) Extend the AlchemyAPI PHP SDK to support face detection API.

From this app, you can see how easy to leverage AlchemyAPI service with only a few source code lines in PHP.

Outline:
I. Introduction
	a.  App URL: http://whoru.mybluemix.net/
	b.  Code URL: https://hub.jazz.net/project/chunbintang/whoru/overview
II. Before getting started
	a.  Bluemix Account
	b.  AlchemyAPI trial key
	c.  PHP language skill
III. How to create the app on Bluemix
	a.  PHP Runtime
        1. Open the Catalog menu.
		2. From the Runtimes section, click PHP.
        3. In the App field, specify the name of your app, in this case, it is set to whoru.
        4. Click Create.Wait for your application to provision.
　　b.  AlchemyAPI Service
        1. Click the App created in the Dashboard. Open the Catalog menu.
		2. Click Add A Service.
        3. Choose AlchemyAPI under Watson.
		4. Input the AlchemyAPI trial key. If you do not have one, please register it at http://www.alchemyapi.com/api/register.html.
        5. Click Create. Click OK if it is prompted to restart the application.
IV. Build the app
        1. Clone the source code into a directory. 
		2. Modify manifest.yml for <your_app_name>, in my case, it is whoru.
		3. Use cf tools to deploy app.
          cf push
V. Run the app
        1. Go to web app, in my case, it is http://whoru.mybluemix.net/.
        2. Click Guess Who Are You from Image URL, input a image url, for example, https://lh3.googleusercontent.com/-B8jO7AKe1Fw/UOxJEuRSV3I/AAAAAAAAAGA/28e6_kjzmVc/s512-no/Profil%2B7.png, click Submit to check whether the app can recognize this person.
		3. Click Guess Who Are You by Uploading an Image, upload an image (you may find andy.jpg under the Source Code), and check whether the app can guess who he/she is.