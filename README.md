# Amazon-AWS
By Joash Pascal Anil, Student ID: 35375779
Website: 



# Step 1: Setting up account details for your server.

The first step is to purchase an EC2 instance from Amazon Web Services and create an account using your student email to avoid payment issues. You can open the Amazon EC2 and access the EC2 service from there.

# Step 2: Creating the server.

To create the server, you'd want first to open up EC2 and then launch an instance, where you'll need to name your server, choose the Operating System, create a key pair to log in from your device via SSH and finally, network settings.

To start, name your server, obviously, and next is to choose the operating system, the operating system you'll need to replicate the website listed, will be the Ubuntu OS, and for the type of Ubuntu OS, you should choose, "Ubuntu Server 24.04 LTS (HVM), SSD Volume Type".

After completing everything above, could you make a key pair? This key pair grants you a PEM file, which is used to access your website anywhere as long as you have the PEM file in your directory to access the website coding.

Finally, the most critical part will be the website's network settings.

From here, it's crucial that you set up the network correctly. Head over to network settings and press edit to set up the network. From there, add a new security group rule, making the type HTTP, and the source type as anywhere. 

Storage is typically set as 8 GB; that's all you need.

Press "Launch Instance", where you will get your key pair. DO NOT LOSE THIS FILE. Losing this file will permanently lose you access to remotely edit your server; you can only edit your Amazon EC2 instance via the website.

Congratulations, you've successfully created a server!

# Step 3: Setting up the server.

Before you do anything at all, first create an elastic IP. From there, could you associate your Elastic IP with your EC2 instance? By allocating your elastic IP, you are accessing your website firmly, meaning that your IP address does not change continuously, which is essential for your website, as you'd want your IP address to be linked to a domain name. Still, if the IP address is inconsistent, there will be problems.

Once you've completed associating your Elastic IP, you can start the server, head over to instances, click your instance and set your instance state to "start instance".

Your IPV4 address should be the same as your Elastic IP.

# Step 4: Accessing the web server remotely.

To access your server remotely, you first need the server up and running, from which you'll go to Amazon EC2 instances, and press connect while your server is active.

Once in the connect section, you can use the "EC2 Instance Connect". You can use this to access your website, and there's no issue with that, but editing your server via terminal/command prompt is much more suitable.

So... to access your server via command prompt/terminal, head over to the SSH client in Connect, and before you follow the instructions on there, create a folder with your PEM file, and make your current directory in command prompt/terminal to be set in the folder which contains your PEM file, or else you won't have suffient access to use your website.

And finally, to access your server via command prompt/terminal, go over the example, and copy the sentence where it starts with "ssh", and paste it into your command prompt/terminal, and there you have it, access to your Amazon EC2 server via command prompt/terminal.

# Step 5: Creating an Apache website.

Now that you're using the SSH client, and the server is up and running, go ahead and enter the command "sudo apt update". This command updates your current software on your Ubuntu server, which will help in installing your Apache server. Once the update has finished, go ahead and paste this command: "sudo apt install apache2". This command installs Apache on your server.

And there you have it, your very own Apache server. You can edit your website via: "sudo nano /var/www/html/index.html".

Sequentially, to open your website, grab your IP address and paste it into your browser like this, Http://<IP>.

Note that you'll have to use HTTP to access your website currently, since modern browsers will auto-redirect your website to be HTTPS and not HTTP, and your website hasn't yet been configured to be a secure website.

# Step 6: Linking your website to a domain.

For this step, you'll need a debit card or some form of digital payment, crazy, isn't it?

Head over to https://www.namecheap.com/

Create an account and purchase a domain name of your choice, but if you ask me, choose something cheap that's billed yearly. My domain cost $5 in AUD, and you could buy this domain name called... "bloggers.it.com", up to you what domain name you'd like, but remember, all domain name prices vary.





















