---
description: >-
  Looking to use your own domain name with Sonoran CAD? We've made it easy for
  you!
---

# Custom Domain & Login Page

{% hint style="warning" %}
Custom login pages require the **standard** version or higher.\
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../other-products/server-hosting.md)!
{% endhint %}

The custom login page allows your community members to register, sign-in, and access your CAD all on your own domain! In addition, user signups and password recovery emails have your [custom branding](custom-emails.md). Logging in also takes you directly to the community, instead of having to select the community at the menu.

![Sonoran CAD Custom Login Page Example](<../../.gitbook/assets/image (4) (3).png>)

## DNS Record Method (Recommended)

{% hint style="warning" %}
**If you are unsure how to add a DNS record, you will need to contact your domain registrar.**\
Or, you may purchase a new domain name with [Sonoran Servers](https://sonoranservers.com/cart.php?a=add\&domain=register).
{% endhint %}

### 1. Add a CNAME and TXT Record for your Domain

{% hint style="info" %}
Due to [DNS requirements](https://blog.cloudflare.com/introducing-cname-flattening-rfc-compliant-cnames-at-a-domains-root), if you wish to use the Apex / root domain instead of a subdomain (i.e. dojrp.com vs cad.dojrp.com), you must have a domain registered with Cloudflare, or otherwise[ transfer your existing domain to Cloudflare](https://developers.cloudflare.com/dns/zone-setups/full-setup/setup/).
{% endhint %}

#### CNAME Record

In your domain's DNS records, add a `CNAME` type record with the `name` set to any desired subdomain and the `content` set to `login.sonorancad.com`.

The example record below sets `cad.sonoranroleplay.com` as the custom login page URL.

#### TXT Record

In your domain's DNS records add a `TXT` type record with the `name` set to `sonorancad_verify_domain` and the text/content set to your [community ID](../getting-started/finding-your-community-id-and-authentication-code.md#finding-your-community-id).

This verifies that your Sonoran CAD community owns this domain.

#### DNS Example

The example below shows the `TXT` record verifying the community ID, and `cad.sonoranroleplay.com` set to the custom login page.

![Sonoran CAD - Cloudflare DNS Example](<../../.gitbook/assets/image (16) (2).png>)

{% hint style="info" %}
**Cloudflare Users:** Be sure to have the **DNS record proxy DISABLED** - and set to `DNS Only`.
{% endhint %}

If you are using Sonoran Servers, our company's server hosting for your domain name, please note the differences in how to enter the settings pictured below. Each DNS system is a bit different and requires different input for the Host Name. Typically the hostname is left blank or in this case a `@` is used to point the record at the root domain name of "`sonoranrp.com`"

![Sonoran CAD - Sonoran Servers DNS Example](<../../.gitbook/assets/image (114).png>)

### 2. Set the Domain Name in Sonoran CAD

Now that you have a `CNAME` and `TXT` record on your domain, in the Sonoran CAD customization menu, set the custom login page URL.\
This should not contain any `https://` or other extensions.

Don't forget to press save!\
Users can now visit this custom domain to view the CAD with a custom login page, including receiving your [branded emails](custom-emails.md) for signups and password recovery messages.

![Sonoran CAD - Custom Login URL](../../.gitbook/assets/CAD\_CustomLoginUrl.png)

{% hint style="warning" %}
When updating or changing an existing DNS record, it may take some time for the change to propagate (based on your TTL).\
\
You can try running `ipconfig /flushdns` in a Windows CMD window and restarting your browser. Otherwise, you can test with other browsers/devices/users while you wait.
{% endhint %}

## iFrame Method

If you are unable to use the [DNS method](custom-login-page.md#dns-record-method-recommended), you can also host an HTML page that renders the CAD in an iFrame.

### 1. Download the HTML File

[You can download a ZIP of the HTML page here.](https://sonoransoftware.com/tutorials/sonorancad/index.zip)

### 2. Edit the HTML File

Replace `YOUR_COMMUNITY_ID_HERE` in the `index.html` file with your [community ID](../getting-started/finding-your-community-id-and-authentication-code.md).

![](<../../.gitbook/assets/image (25).png>)

### 3. Host the HTML File

Now that you've saved the custom URL inside of the HTML file, you can host this with your own domain on your own web server. Users can now register and access your CAD from your custom domain, and will even receive your [custom branded emails](custom-emails.md) for account actions.

## In-Game Tablet

If you wish to use a custom login page when using the [in-game Tablet resource](../../integration-plugins/integration-plugins/available-plugins/tablet.md), you can set a convar in your server.cfg.\
\
The easiest way to show your [custom login page](custom-login-page.md) is to use a query string.

`"https://sonorancad.com/#/?comid=YOUR_COMMUNITY_ID_HERE"`

Simply replace `YOUR_COMMUNITY_ID_HERE` in the URL with your [community ID](../getting-started/finding-your-community-id-and-authentication-code.md).\
EX: `https://sonorancad.com/#/?comid=midwestrp`

Add the following to your server.cfg **before** starting the tablet resource:

```
setr sonorantablet_cadUrl "YOUR_URL_HERE"
```

Fill in with your actual URL above with the comid you want.
