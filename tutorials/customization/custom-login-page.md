---
description: >-
  Looking to use your own domain name with Sonoran CAD? We've made it easy for
  you!
---

# Custom Login Page

{% hint style="warning" %}
Custom login pages require the **standard** version or higher.  
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

The custom login page allows your community members to register, sign-in, and access your CAD all on your own domain! In addition, user signups and password recovery emails have your [custom branding](custom-emails.md). Logging in also takes you directly to the community, instead of having to select the community at the menu.

![Sonoran CAD Custom Login Page Example](../../.gitbook/assets/image%20%2892%29.png)

## DNS Record Method \(Recommended\)

{% hint style="danger" %}
This method is temporarily unavailable. An announcement will be posted in our Discord with an update soon.
{% endhint %}

### 1. Add your Domain name to Cloudflare

Due to certificate limitations, **Sonoran CAD requires custom domain name records to be managed by Cloudflare**. Cloudflare is a free service allowing you to [sign up and add your domain](https://support.cloudflare.com/hc/en-us/articles/201720164-Creating-a-Cloudflare-account-and-adding-a-website) simply by changing the name servers.

### 2. Add a CNAME Record

In Cloudflare, select your domain name and open the DNS management panel.  
Add a `CNAME` type record with the `name` set to any desired subdomain and the `content` set to `login.sonorancad.com`.

This record sets `cad.sonoranroleplay.com` as the custom login page URL.

![Cloudflare - DNS Record ](../../.gitbook/assets/image%20%2896%29.png)

### 3. Ensure TLS/SSL Mode is Full

In Cloudflare, select your domain and navigate to the SSL/TLS panel.  
Ensure the mode is set to `Full`.

![Cloudflare - SSL/TLS Mode](../../.gitbook/assets/image%20%2891%29.png)

### 3. Set the Domain Name in Sonoran CAD

In the Sonoran CAD customization menu, set the custom login page URL.  
This should not contain any `https://` or other extensions.

Don't forget to press save!  
Users can now visit this custom domain to view the CAD with a custom login page, including receiving your [branded emails](custom-emails.md) for signups and password recovery messages.

![Sonoran CAD - Custom Login URL](../../.gitbook/assets/image%20%2873%29.png)

## iFrame Method

If you are unable to use Cloudflare for DNS management, you can also host an HTML page that renders the CAD in an iFrame.

### 1. Download the HTML File

[You can download a ZIP of the HTML page here.](https://sonoransoftware.com/tutorials/sonorancad/index.zip)

### 2. Edit the HTML File

Replace `YOUR_COMMUNITY_ID_HERE` in the `index.html` file with your [community ID](../getting-started/finding-your-community-id-and-authentication-code.md).

![](../../.gitbook/assets/image%20%2876%29.png)

### 3. Host the HTML File

Now that you've saved the custom URL inside of the HTML file, you can host this with your own domain on your own web server. Users can now register and access your CAD from your custom domain, and will even receive your [custom branded emails](custom-emails.md) for account actions.

## In-Game Tablet

When using the [in-game Tablet resource](../../integration-plugins/integration-plugins/available-plugins/tablet.md), the easiest way to display your custom login page is by adding a query string.

Open the `tablet/html/index.html` file and paste your custom community URL.  
  
`https://app.sonorancad.com/#/?comid=YOUR_COMMUNITY_ID_HERE`

Simply replace `YOUR_COMMUNITY_ID_HERE` in the URL with your [community ID](../getting-started/finding-your-community-id-and-authentication-code.md).  
EX: `https://app.sonorancad.com/#/comid?=dojrp`

![Tablet HTML file](../../.gitbook/assets/screen-shot-2020-07-22-at-10.23.09-pm.png)

