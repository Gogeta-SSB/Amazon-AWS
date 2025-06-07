# Amazon-AWS
Website: https://pickler.blog || Made by Joash Pascal Anil, Student ID: 35375779.

Check out my link below if you want a walkthrough with instructions on how to create a website, following the guide created below.

https://drive.google.com/file/d/1nBuT4XCfYSfFoE7JKgkrxzYD8ADTgTtP/view?usp=sharing 


# Step 1: Setting up account details for your server.

The first step is to purchase an EC2 instance from Amazon Web Services and create an account using your student email to avoid payment issues. You can open the Amazon EC2 and access the EC2 service from there. (link: https://aws.amazon.com/ec2/)

# Step 2: Creating the server.

To create the server, you'd want first to open up EC2 and then launch an instance, where you'll need to name your server, choose the Operating System, create a key pair to log in from your device via SSH and finally, network settings.

To start, name your server, obviously, and next is to choose the operating system, the operating system you'll need to replicate the website listed, will be the Ubuntu OS, and for the type of Ubuntu OS, you should choose, "Ubuntu Server 24.04 LTS (HVM), SSD Volume Type".

![image](https://github.com/user-attachments/assets/d1d08ea2-a56a-4c1a-8deb-e13bdb2ed484)

Choose a t2.micro instance for easy demand access.

![image](https://github.com/user-attachments/assets/e2818cf0-a9c2-47a8-808c-177b33a1b04f)




After you complete everything above, you can create a key pair. This key pair grants you a PEM file, which is used to access your website anywhere as long as you have the PEM file in your directory to access the website coding.

![image](https://github.com/user-attachments/assets/778b1d35-d0a5-4b62-8d9f-a817e15fca63)


Finally, the most critical part will be the website's network settings.

From here, it's crucial that you set up the network correctly. Head over to network settings and press edit to set up the network. From there, add a new security group rule, making the type HTTP, and the source type as anywhere. 

![image](https://github.com/user-attachments/assets/7c0ec702-4163-45a3-a791-66c7db7afd9d)


Storage is typically set as 8 GB; that's all you need.

Press "Launch Instance", where you will get your key pair. DO NOT LOSE THIS FILE. Losing this file will permanently lose access to your server remotely; you can only edit your Amazon EC2 instance via the website.

Congratulations, you've successfully created a server!

# Step 3: Setting up the server.

Before you do anything at all, first create an elastic IP. From there, allocate your Elastic IP to your EC2 Instance. By allocating your elastic IP, you are accessing your website firmly; your IP address does not change continuously, which is essential for your website, as you'd want your IP address to be linked to a domain name. Still, if the IP address is inconsistent, there will be problems.

![image](https://github.com/user-attachments/assets/340f9b51-ca79-4373-bd78-3870a538c480)
(choose instance in resource type, choose your current instance in instance.)

Once you've completed associating your Elastic IP, you can start the server, head over to instances, click your instance and set your instance state to "start instance".

Your IPV4 address should be the same as your Elastic IP.

# Step 4: Accessing the  web server remotely.

To access your server remotely, you first need the server up and running, from which you'll go to Amazon EC2 instances, and press connect while your server is active.

Once in the connect section, you can use the "EC2 Instance Connect". You can use this to access your website, and there's no issue with that, but editing your server via terminal/command prompt is much more suitable.

So... to access your server via command prompt/terminal, head over to the SSH client in Connect, and before you follow the instructions on there, create a folder with your PEM file, and make your current directory in command prompt/terminal to be set in the folder which contains your PEM file, or else you won't have suffient access to use your website.

And finally, to access your server via command prompt/terminal, go over the example, and copy the sentence where it starts with "ssh", and paste it into your command prompt/terminal, and there you have it, access to your Amazon EC2 server via command prompt/terminal.

![image](https://github.com/user-attachments/assets/875ab7ec-bb3d-4a40-9d31-edefa9491c06)

# Step 5: Creating an Apache website.

Now that you're using the SSH client, and the server is up and running, enter the command "sudo apt update". This command updates the software on your Ubuntu server, which will help install your Apache server. Once the update has finished, paste this command: "sudo apt install apache2". This command installs Apache on your server.
![image](https://github.com/user-attachments/assets/52d4a313-3010-4b8a-bcf1-50a8f739a8f3)

![image](https://github.com/user-attachments/assets/6d6e468a-ebb5-4bd8-8546-9bf04517300c)



And there you have it, your very own Apache server. You can edit your website via: "sudo nano /var/www/html/index.html".

(should look like this)
![image](https://github.com/user-attachments/assets/0cd1738c-e615-4620-8fcf-7cc9b473ba0e)


To open your website, paste your IP address into your browser like this: Http://<IP>.

You'll have to use HTTP to access your website currently, since modern browsers will auto-redirect your website to HTTPS and not HTTP, and your website hasn't been configured to be secure.

# Step 6: Linking your website to a domain.

For this step, you'll need a debit card or some form of digital payment, which is easy.

Head over to https://www.namecheap.com/

Create an account and purchase a domain name of your choice, but if you ask me, choose something cheap that's billed yearly. My domain costs $5 in AUD, and you can buy this domain name called... "bloggers.it.com". It's up to you what domain name you'd like, but remember, all domain name prices vary.

Once your domain name is ready, you can head to Amazon Route 53.

From there, let's create a hosted zone, and it'll come with two records. For the name, you can just input the domain name you've purchased, set the type to a public hosted zone, and create the hosted zone.

You'll have two records already created, which will be used to link the domain, but you'll need to make two additional documents.

![image](https://github.com/user-attachments/assets/1f727320-05a3-4e33-b190-3732cd80f13a)
(Should be similar to this, all Route 53 hosted zones are unique)


In your hosted zone, you can create a record, and from here, I recommend using the wizard preference, since it makes the instructions much easier to follow.

![image](https://github.com/user-attachments/assets/4c4c7015-ab9b-4ae4-a685-1fee116d302e)


Choose the simple routing for your routing, then define the simple record. From here, all you need to do is route the traffic to your IP address, your Elastic IP address.

Now, create another record, choose simple routing, define the simple record, and from here in your record name, input "www" and your route traffic to your domain name, e.g. pickler.Blog.

And finally, to allow your website to be registered, you need to go back to namecheap.com, where you'll go to your profile, access your dashboard, head over to the domain list, press manage, and head over to nameservers.

Here, we'll need to add four lines of traffic. From your record in Amazon Route 53, find your four route traffics in your NS type record, and go back to Namecheap.com, where you'll create a custom DNS. Add all four traffic routes, and confirm that they have been saved.

![image](https://github.com/user-attachments/assets/6ea13b33-972f-4137-a1de-384d622e1425)
(should look similar to this)

Typically, you'll have to wait maybe 10-15 minutes for Namecheap to connect to register through the custom DNS, but once it's done, your server can now be accessed via http://<domain name>.
# Step 7: converting your website from http to https

This is the final step in setting up your website from HTTP to HTTPS.

You can look at this website, which I used to set up HTTPS, but I'll walk you through how to set it up on your server.
https://certbot.eff.org/instructions?ws=apache&os=snap 

Moving on...

Let's head back to our SSH client, which you should know how to use already. Let's install snapD on our server via this command: "sudo apt install snapd" and "sudo snap install hello-world". Check if you've correctly installed it via this command: "hello-world", it should come back with "Hello World!". With Snapd installed, we can now use certbot to convert our website into a secure HTTPS website.

Enter these commands to flush out any CertBot OS packages: "sudo apt-get remove certbot", "sudo dnf remove certbot", "sudo yum remove certbot". Not all of them will work, but it's better to uninstall them to ensure that CertBot works properly. 

Once that's done, let's install CertBot via: "sudo snap install --classic certbot". Check if CertBox can run via: "sudo ln -s /snap/bin/certbot /usr/bin/certbot".

Once that's done, we can finally convert our server to https via this command: "sudo certbot --apache". Now, you will need to provide a domain name, so enter your domain name, e.g. pickler.blog, and from there, the www will allow CertBox to convert your website into an HTTPS website. Turn on auto-renewal via this command: "sudo certbot renew --dry-run". Quickly check your website, enter https://<domain name>.

And there you have it, your very own website! Your website is encrypted and linked to a domain name, and it can be accessed by anyone worldwide!






















