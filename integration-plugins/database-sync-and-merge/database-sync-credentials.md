---
description: Getting your database Credentials to use with Database Sync.
---

# Database Sync Credentials

{% hint style="info" %}
Database Sync is not enabled with the free version of Sonoran CAD.  
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../../tutorials/getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

Database Sync is a read-only system. All characters, licenses, and vehicle registrations pulled from your database can not be modified in the CAD.  
  
Database Merge allows you to save off additional, manually specified data in the CAD.

## 1. Getting your Credentials

{% tabs %}
{% tab title="phpMyAdmin" %}
## phpMyAdmin - Database Credentials

#### **1. Navigate to your phpMyAdmin Web Panel**

#### **2. Navigate to User Accounts**

At the top of your screen click on **`User Accounts`**.

![](../../.gitbook/assets/image%20%28136%29.png)

**3. Create a new user account**

![phpMyAdmin - New User Account](../../.gitbook/assets/image%20%28135%29.png)

#### **4. Fill out the account information**

The `Host Name` field should be set as `Any Host` and the value as `%`. This will allow external IPs \(Sonoran CAD\) to connect to your database.

![phpMyAdmin - New User Information](../../.gitbook/assets/image%20%28145%29.png)

#### **5. Once created, edit the user account privileges**

![phpMyAdmin - Edit Account Privileges](../../.gitbook/assets/image%20%28143%29.png)

#### **6. Select your specific database**

![phpMyAdmin - Set Database](../../.gitbook/assets/image%20%28146%29.png)

#### **7. Select only the required permissions**

`SELECT` and `SHOW VIEW` will ensure this account can only read from your database.

![phpMyAdmin - Read Only Permissions](../../.gitbook/assets/image%20%28147%29.png)

#### 8. Save the user and set credentials in Sonoran CAD

You will now want to go to [http://whatsmyip.org](http://whatsmyip.org) and get your Public IP Address to use as your Host.

Database Translation Information**:**

| phpMyAdmin | SonoranCAD |
| :--- | :--- |
| Host | Host/Address |
| Database | Database |
| User name | Username |
| Password | Password |

{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](./#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}

{% tab title="HeidiSQL" %}
## HeidiSQL - Database Credentials

#### 1. Login to your database using HeidiSQL. 

#### 2. Open the User Manager

At the top of your screen click `Tools` and then `User Manager.`  
Then, click `Add` at the top left.

![HeidiSQL - Open User Manager](../../.gitbook/assets/image%20%28131%29.png)

#### 3. Enter the Account Information

Enter a user name, password, and enter `%` in the From host field. This will allow external IPs \(Sonoran CAD\) to connect to your database.

Under `Allow Access To` select `Add Object`

![HeidiSQL - User Account Credentials](../../.gitbook/assets/image%20%28142%29.png)

#### 4. Select the Database

Select the name of your database, then hit `Ok`.

![HeidiSQL - Select Database](../../.gitbook/assets/image%20%28140%29.png)

#### 5. Select the Permissions

Check off the `EXECUTE`, `SELECT`, and `SHOW VIEW` read permissions. Then press `Save`.

![HeidiSQL - Select User Permissions](../../.gitbook/assets/image%20%28144%29.png)

#### 6. Save the user and set credentials in Sonoran CAD

You will now want to go to [http://whatsmyip.org](http://whatsmyip.org) and get your Public IP Address to use as your Host.

Database Translation Information

| HeidiSQL | SonoranCAD |
| :--- | :--- |
| Host | Host/Address |
| User name | Username |
| Password | Password |
| Database | Database |

{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](./#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}

{% tab title="Zap Hosting" %}
## Zap Hosting - Database Credentials

#### 1. Login

Login to your Zap Hosting Account and Navigate to your FiveM Server.

#### 2. View the Tools Section

Scroll down until you see **TOOLS** on the left hand side of your screen and select **`Databases`.**

![ZAP Hosting Tools - Database](../../.gitbook/assets/image%20%28139%29%20%282%29.png)

#### 3. View Database Credentials

In the Center of your screen you will see you're database Credentials. 

![Zap Hosting - Database Credentials](../../.gitbook/assets/image%20%28134%29.png)

#### 4. Set DB Credentials in Sonoran CAD

Database Translation Information

| Zap Hosting | SonoranCAD |
| :--- | :--- |
| Server/IP | Host/Address |
| Database | Database |
| User | Username |
| Password | Password |

{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](./#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}
{% endtabs %}

## 2. Port Forwarding

If your database port has not already been opened, you will need to forward/open this port.  
Typically, the default MySQL port is `3306`.

To check if your MySQL port has been properly opened, [visit a port checking utility](https://www.yougetsignal.com/tools/open-ports/) and enter your MySQL server's IP address and port.

**If you are unsure how to open a port, you will need to contact your hosting provider.**

\*\*\*\*



\*\*\*\*







