---
title: 'Linking a GoDaddy Domain to Netlify'
date: 2024-08-06T23:15:00+07:00
slug: custom-domain
category: tech
summary:
description:
cover:
  image: ''
  alt: 'Linking a GoDaddy Domain to Netlify'
  caption:
  relative: true
showToc: true
draft: false
ShowReadingTime: true
tags:
  [
    'Hugo',
    'Netlify',
    'Custom Domain',
    'Domain',
    'GoDaddy',
    'GitHub Pages',
    'Static Site Generator',
    'Web Development',
    'Custom Domain',
    'CI/CD',
    'Blogging Tools',
  ]
---

---

This guide continues from [Deploying a Blog Powered by Hugo to Netlify](https://rishabdhar.in/tech-write-up/deploy-hugo/) and will walk you through setting up a custom domain purchased from GoDaddy on Netlify.

---

### Step 1: Purchase a Domain on GoDaddy

1. **Create a GoDaddy Account**

   - Go to [GoDaddy’s website](https://www.godaddy.com/).
   - Click on "Sign In" at the top right corner or "Create an Account" if you don’t have one.
   - Follow the prompts to set up your account.

2. **Search for Your Desired Domain**

   - Once logged in, use the search bar to find the domain name you want (e.g: rishabdhar.in).
   - GoDaddy will show you the availability of the domain. If it's taken, you'll get suggestions for alternative names or extensions.

3. **Select Your Domain**

   - Choose the domain you like from the search results. Click "Add to Cart".
   - GoDaddy will offer additional services like privacy protection, email, and hosting. You can add these if needed or skip them.

4. **Proceed to Checkout**

   - Click on the cart icon and then "Continue to Cart".
   - Review your order and click "Continue to Checkout".
   - Enter your payment information and complete the purchase.

5. **Verify Domain Ownership**
   - After purchase, you’ll receive a confirmation email from GoDaddy. Follow the instructions to verify your email address and domain ownership.

---

### Step 2: Configure Domain Settings on GoDaddy

1. **Access Domain Settings**

   - Log in to your GoDaddy account.
   - Go to "My Products" and locate the domain you just purchased.
   - Click on "DNS" next to your domain name.

2. **Set Up Nameservers**

   - **Configure Nameservers**: If you plan to use Netlify’s nameservers (generally not needed as Netlify usually works with DNS records rather than nameservers directly), you would change them as follows:

     - In the "DNS Management" section, find the "Nameservers" area.
     - Select "Change" and choose "Custom".
     - Enter the nameservers provided by Netlify if applicable (Netlify generally uses DNS records rather than custom nameservers for this integration, so this step might be optional or different based on your specific setup).
     - Save your changes.

   - **Configure DNS Records**: Typically, you’ll be adding or modifying DNS records instead of changing nameservers:
     - **A Records**: If you’re using Netlify’s IP addresses, you might need to add or update A records. Netlify’s documentation provides the current IP addresses.
     - **CNAME Record**: For subdomains or if you prefer to use a CNAME, create a CNAME record pointing to `your-site-name.netlify.app`.

---

### Step 3: Set Up Your Domain on Netlify

1. **Log In to Netlify**

   - Go to [Netlify’s website](https://www.netlify.com/) and log in or sign up if you don’t have an account.

2. **Add a New Site**

   - On the Netlify dashboard, click on “Add new site” and then select “Add custom domain”.

3. **Enter Your Domain Name**

   - Enter the domain name you purchased from GoDaddy into the field provided and click “Verify”.

4. **Configure DNS Settings**

   - Netlify will provide DNS records that you need to set up on GoDaddy. This typically includes:
     - **A Records**: Point to Netlify’s IP addresses.
     - **CNAME Record**: For subdomains, point to `your-site-name.netlify.app`.

5. **Verify Domain Connection**

   - After updating DNS records on GoDaddy, go back to Netlify and click “Check DNS configuration”.
   - Netlify will verify that your domain is correctly set up. This process might take a few minutes to propagate.

6. **Finalize the Setup**
   - Once Netlify verifies the configuration, your custom domain will be linked to your site.
   - You can then set it as your primary domain or configure redirects as needed.

---

### Step 4: Test Your Domain

1. **Check DNS Propagation**

   - Use tools like [WhatsMyDNS](https://www.whatsmydns.net/) to check if DNS changes have propagated globally.

2. **Visit Your Domain**

   - Enter your domain name in a browser to ensure it correctly points to your Netlify site.

3. **Secure Your Domain**
   - Netlify provides free SSL certificates for custom domains. Ensure SSL is enabled in Netlify’s dashboard to secure your site.

---

> **Tomorrow's dawn heralds the Singularity**

---
