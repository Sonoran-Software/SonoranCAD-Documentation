---
description: Getting your database Credentials to use with Database Sync.
---

# Database Sync Credentials

{% hint style="info" %}
Database Sync is not enabled with the free version of Sonoran CAD.  
For more information, see our [pricing](../../pricing/faq/) or view how to check your community [limits](../getting-started/view-your-limits.md).
{% endhint %}

{% hint style="success" %}
Looking for VPS, web, or dedicated hosting? Check out our official [server hosting](../../vps-hosting-1/vps-hosting.md)!
{% endhint %}

Database Sync is a read-only system. All characters, licenses, and vehicle registrations pulled from your database can not be modified in the CAD.  
  
Database Merge allows you to save off additional, manually specified data in the CAD.

### Getting your Credentials

{% tabs %}
{% tab title="phpMyAdmin" %}
#### phpMyAdmin - Database Credentials

1. Navigate to your phpMyAdmin Instance.

2. At the top of your screen click on **`User Accounts`**.

![](../../.gitbook/assets/image%20%28136%29.png)

3. You will now want to create a new user account, to do so click **`Add user account`** .

![](../../.gitbook/assets/image%20%28135%29.png)

4. Fill out a User name and Password to use. _`Make sure you write these down as you're going to need them.`_

5. Check off `Global Privileges.` Scroll down to the bottom of the page and click `Go.`

6. At the next page you're going to want to click `Go` again.

7. You will now want to go to [http://whatsmyip.org](http://whatsmyip.org) and get your Public IP Address to use as your Host.

### Database Translation Information

| phpMyAdmin | SonoranCAD |
| :--- | :--- |
| Host | Host/Address |
| Database | Database |
| User name | Username |
| Password | Password |

{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](database-sync-and-merge.md#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}

{% tab title="HeidiSQL" %}
#### HeidiSQL - Database Credentials

1. Login to your database using HeidiSQL. 

2. At the top of your screen click `Tools` and then `User Manager.`

![](../../.gitbook/assets/image%20%28131%29.png)

3. At the top left click `Add`.

4. Enter a User name, Password, and enter `%` in the From host field. Check off `Global Privileges` and click `Save`.

![](../../.gitbook/assets/image%20%28138%29.png)



5. You will now want to go to [http://whatsmyip.org](http://whatsmyip.org) and get your Public IP Address to use as your Host.

### Database Translation Information

| HeidiSQL | SonoranCAD |
| :--- | :--- |
| Host | Host/Address |
| User name | Username |
| Password | Password |
| Database | Database |

{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](database-sync-and-merge.md#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}

{% tab title="Zap Hosting" %}
#### Zap Hosting - Database Credentials

1. Login to your Zap Hosting Account and Navigate to your FiveM Server.

2. Scroll down until you see **TOOLS** on the left hand side of your screen and select **`Databases`.**

![](../../.gitbook/assets/image%20%28133%29.png)

3. In the Center of your screen you will see you're database Credentials. 

![](../../.gitbook/assets/image%20%28134%29.png)



### Database Translation Information

| Zap Hosting | SonoranCAD |
| :--- | :--- |
| Server/IP | Host/Address |
| Database | Database |
| User | Username |
| Password | Password |



{% hint style="warning" %}
See [Database Sync and Merge Connection Credentials](database-sync-and-merge.md#written-configuration-guide) to figure out how to add Credentials to your CAD Instance using the information above.
{% endhint %}
{% endtab %}
{% endtabs %}





\*\*\*\*







