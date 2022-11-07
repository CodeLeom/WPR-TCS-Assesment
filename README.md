# WPR-TCS-Assesment
Assesment for L2 support role

>Question A
The customer disabled WP Rocket’s automatic cache clearing system. They want you to provide them with a way to clear the following cache files at a specific time they select, e.g. when the site has the least traffic:

- HTML
- Combined/minified CSS/JavaScript files
- Files created by the Remove files from static resources feature

Using WP Rocket’s existing functions:

1. Explain how they should implement the requirement to clear the cache at a specific time.
2. Provide any piece of code necessary to perform the cache clearing task.

> ### Response

Hello Mate, kindly empathize with the customer and send the following response:

To perform this operation, it can be done in two ways, through real Cron Job on the customer's server or through the WP Cron. 
For this issue I will advice you create a Cron Job on your server following the following procedure:

Firstly, disable WP Cron to avoid execution anytime someone loads your websites. To disable WP Cron, go to your server root files, locate `wp-config` inside wp content folder. 
Edit your `wp-config.php` file and add the following code before the "/* That's all, stop editing! Happy blogging. */" line.
`define('DISABLE_WP_CRON', true);`

>NB: each server has differenct way of adding Cron job, you can ask your hosting provider to direct you but if you are using cPanel, Follow the steps in this [video](https://recordit.co/A4Jj1Kg7x9). Set the Cron Job on the time that you know the website has less traffic. 

The code you are requested to put in the command field is 
```bash
wget -q -O - http://yourdomain.com/wp-cron.php?doing_wp_cron >/dev/null 2>&1
```
Replace `yourdomain.com` with your website domain name. e.g mywebsite.com

If the above steps didn't work refer to this [article](https://docs.wp-rocket.me/article/1279-cron-and-wp-rocket#setting-up-cron-job) for guide.
You can also refer to the steps in [this](https://docs.wp-rocket.me/article/494-how-to-clear-cache-via-cron-job#clear-cache).

I hope this helps, if there is anything you will like me to do for you, kindly let me know.

Thanks,
Ayodele.




>Question B
Your teammate sent your instructions and code to the customer.  They implemented them but the cache isn’t cleared.

Provide the steps that you’d follow to troubleshoot this, based on the solution you provided in A. 

> ### Response
Firstly, I will check if the Cron Job was set properly, and if wp-cron is disabled in the wp-config file and it is replaced with a server cron

If all that was done perfectly, I will request the client to contact their hosting provider on why Cron is not working as expected.
