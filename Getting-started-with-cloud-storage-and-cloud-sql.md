# Objectives

In this lab, you learn how to perform the following tasks:

- Create a Cloud Storage bucket and place an image into it.

- Create a Cloud SQL instance and configure it.

- Connect to the Cloud SQL instance from a web server.

- Use the image in the Cloud Storage bucket on a web page.

## Deploy a web server VM instance
1. In the Google Cloud Console, on the Navigation menu (Navigation menu icon), click Compute Engine > VM instances.

2. Click Create Instance.

3. On the Create an Instance page, for Name, type bloghost

4. For Region and Zone, select the region and zone assigned by Qwiklabs.

5. For Machine type, accept the default.

6. For Boot disk, if the Image shown is not Debian GNU/Linux 11 (bullseye), click Change and select Debian GNU/Linux 11 (bullseye).

7. Leave the defaults for Identity and API access unmodified.

8. For Firewall, click Allow HTTP traffic.

9. Click Advanced options to open that section of the dialog.

10. Click Management to open that section of the dialog.

11. Scroll down to the Automation section, and enter the following script as the value for Startup script:

        apt-get update
        apt-get install apache2 php php-mysql -y
        service apache2 restart
    
12. Leave the remaining settings as their defaults, and click Create.

13. On the VM instances page, copy the bloghost VM instance's internal and external IP addresses to a text editor for use later in this lab.


## Create a Cloud Storage bucket using the gsutil command line
All Cloud Storage bucket names must be globally unique. To ensure that your bucket name is unique, these instructions will guide you to give your bucket the same name as your Cloud Platform project ID, which is also globally unique.

Cloud Storage buckets can be associated with either a region or a multi-region location: US, EU, or ASIA. In this activity, you associate your bucket with the multi-region closest to the region and zone that Qwiklabs or your instructor assigned you to.

1. On the Google Cloud Platform menu, click Activate Cloud Shell Activate Cloud Shell icon. If a dialog box appears, click Continue.

2. For convenience, enter your chosen location into an environment variable called LOCATION. Enter one of these commands:

       export LOCATION=US

    Or

       export LOCATION=EU

    Or

       export LOCATION=ASIA

3. In Cloud Shell, the DEVSHELL_PROJECT_ID environment variable contains your project ID. Enter this command to make a bucket named after your project ID:

        gsutil mb -l $LOCATION gs://$DEVSHELL_PROJECT_ID

    If prompted, click Authorize to continue.

4. Retrieve a banner image from a publicly accessible Cloud Storage location:

        gsutil cp gs://cloud-training/gcpfci/my-excellent-blog.png my-excellent-blog.png

5. Copy the banner image to your newly created Cloud Storage bucket:

        gsutil cp my-excellent-blog.png gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png

6. Modify the Access Control List of the object you just created so that it is readable by everyone:

        gsutil acl ch -u allUsers:R gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png


## Create the Cloud SQL instance

1. In the Google Cloud Console, on the Navigation menu (Navigation menu icon), click SQL.

2. Click Create instance.

3. For Choose a database engine, select MySQL.

4. For Instance ID, type blog-db, and for Root password type a password of your choice.

5. Select Single zone and set the region and zone assigned by Qwiklabs.

6. Click Create Instance.

7. Click on the name of the instance, blog-db, to open its details page.

8. From the SQL instances details page, copy the Public IP address for your SQL instance to a text editor for use later in this lab.

9. Click on Users menu on the left-hand side, and then click Add User Account.

10. For User name, type blogdbuser

11. For Password, type a password of your choice. Make a note of it.

12. Click Add to add the user account in the database.

13. Click on Connections menu on the left-hand side, and then click Networking tab.

14. Click ADD NETWORK.

15. For Name, type web front end

16. For Network, type the external IP address of your bloghost VM instance, followed by /32

The result will look like this:

    35.192.208.2/32
    
17. Click Done to finish defining the authorized network.

18. Click Save to save the configuration change.

## Configure an application in a Compute Engine instance to use Cloud SQL
1. On the Navigation menu (Navigation menu icon), click Compute Engine > VM instances.

2. In the VM instances list, click SSH in the row for your VM instance bloghost. Or use cloud active shell to ssh into the VM.

3. In your ssh session on bloghost, change your working directory to the document root of the web server:

        cd /var/www/html

4. Use the nano text editor to edit a file called index.php:

        sudo nano index.php

5. Paste the content below into the file:

        <html>
        <head><title>Welcome to my excellent blog</title></head>
        <body>
        <h1>Welcome to my excellent blog</h1>
        <?php
         $dbserver = "CLOUDSQLIP";
        $dbuser = "blogdbuser";
        $dbpassword = "DBPASSWORD";
        // In a production blog, we would not store the MySQL
        // password in the document root. Instead, we would store it in a
        // configuration file elsewhere on the web server VM instance.
        $conn = new mysqli($dbserver, $dbuser, $dbpassword);
        if (mysqli_connect_error()) {
                echo ("Database connection failed: " . mysqli_connect_error());
        } else {
                echo ("Database connection succeeded.");
        }
        ?>
        </body></html>
        
6. Press Ctrl+O, and then press Enter to save your edited file.

7. Press Ctrl+X to exit the nano text editor.

8. Restart the web server:

        sudo service apache2 restart

9. Open a new web browser tab and paste into the address bar your bloghost VM instance's external IP address followed by /index.php. The URL will look like this:

        35.192.208.2/index.php

  When you load the page, you will see that its content includes an error message beginning with the words:

      Database connection failed: ...

10. Return to your ssh session on bloghost. Use the nano text editor to edit index.php again.

        sudo nano index.php

11. In the nano text editor, replace CLOUDSQLIP with the Cloud SQL instance Public IP address that you noted above. Leave the quotation marks around the value in place.

12. In the nano text editor, replace DBPASSWORD with the Cloud SQL database password that you defined above. Leave the quotation marks around the value in place.

13. Press Ctrl+O, and then press Enter to save your edited file.

14. Press Ctrl+X to exit the nano text editor.

15. Restart the web server:

        sudo service apache2 restart

16. Return to the web browser tab in which you opened your bloghost VM instance's external IP address. When you load the page, the following message appears:

        Database connection succeeded.


## Configure an application in a Compute Engine instance to use a Cloud Storage object
1. In the Google Cloud Console, click Cloud Storage > Buckets.

2. Click on the bucket that is named after your GCP project.

3. In this bucket, there is an object called my-excellent-blog.png. Copy the URL behind the link icon that appears in that object's Public access column, or behind the words "Public link" if shown.

4. Return to your ssh session on your bloghost VM instance.

5. Enter this command to set your working directory to the document root of the web server:

        cd /var/www/html

6. Use the nano text editor to edit index.php:

        sudo nano index.php

7. Use the arrow keys to move the cursor to the line that contains the h1 element. Press Enter to open up a new, blank screen line, and then paste the URL you copied earlier into the line.

8. Paste this HTML markup immediately before the URL:

        <img src='
9. Place a closing single quotation mark and a closing angle bracket at the end of the URL:

        '>

  The resulting line will look like this:

       <img src='https://storage.googleapis.com/qwiklabs-gcp-0005e186fa559a09/my-excellent-blog.png'>

  The effect of these steps is to place the line containing <img src='...'> immediately before the line containing <h1>...</h1>
  
10. Press Ctrl+O, and then press Enter to save your edited file.

11. Press Ctrl+X to exit the nano text editor.

12. Restart the web server:

        sudo service apache2 restart
        
13. Return to the web browser tab in which you opened your bloghost VM instance's external IP address. When you load the page, its content now includes a banner image.




