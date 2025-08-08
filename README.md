# MagedIn_TrojanRequestBlocker Extension for Magento 2

Keep your Magento 2 store protected from suspicious and harmful requests with MagedIn_TrojanRequestBlocker. This robust extension acts as a shield, detecting and blocking malicious requests before they can disrupt your e-commerce operations. Whether it’s bots, fraudulent actions, or unusual traffic spikes, MagedIn_TrojanRequestBlocker is designed to guard your store from potentially harmful activity, ensuring a secure and smooth shopping experience for legitimate users.

[![Magento 2 Coding Standard](https://github.com/magedin/magento2-module-trojan-request-blocker/actions/workflows/coding-standard.yml/badge.svg)](https://github.com/magedin/magento2-module-trojan-request-blocker/actions/workflows/coding-standard.yml)

## Compatibility

- Magento 2.3
- Magento 2.4

## Features

- **Trojan Request Blocking**: Detects and blocks malicious requests containing harmful code patterns
- **Fake User Registration Restriction**: Prevents fake user registrations based on:
  - Blocked email domains (e.g., temp-mail.org, 10minutemail.com)
  - Blocked specific email addresses (e.g., test@example.com, fake@domain.com)
  - Blocked first name patterns (e.g., test, fake, admin)
  - Blocked last name patterns (e.g., test, fake, admin)
- **Admin Configuration**: Easy-to-use admin panel for managing blocked patterns and domains
- **Checkout Protection**: Validates both guest and registered customer checkout processes

## Context

Have you ever seen any order like the following one in your Magento 2 website?

![alt text](https://github.com/magedin/magento2-module-trojan-request-blocker/blob/master/.github/assets/images/trojan_orders_in_magento2.jpg?raw=true)

In the fast-paced world of eCommerce, security is paramount.
Recently some Magento 2 websites encountered a serious security threat.
Their Magento stores were targeted by trojan orders attempting to exploit vulnerabilities within Magento’s system.
The attackers tried to inject malicious code through customer fields, such as the First Name and Last Name fields, with the aim of executing code when rendering the page.

## Installation

```bash
> composer require magedin/module-trojan-request-blocker
> php bin/magento module:enable MagedIn_TrojanRequestBlocker
> php bin/magento setup:upgrade
> php bin/magento setup:di:compile
```

## How to Use This Extension

To get a full explanation of what's the problem here, please refer to this blog post:

[Protecting Your Magento Store from Trojan Orders: Introducing the Trojan Request Blocker](https://wp.me/p8DGlE-2k5)

There you'll have a video explaining how it works and how you can use it.

## Fake User Registration Restriction Configuration

The extension includes a powerful fake user registration restriction feature that helps prevent fake accounts from being created. To configure this feature:

1. Go to **Admin Panel > Stores > Configuration > System > Fake User Registration Restriction**
2. Enable the "Enable Fake User Restriction" option
3. Configure the following settings:
   - **Blocked Email Domains**: Add email domains to block (one per line)
     - Example: `temp-mail.org`, `10minutemail.com`, `guerrillamail.com`
   - **Blocked Email Addresses**: Add specific email addresses to block (one per line)
     - Example: `test@example.com`, `fake@domain.com`, `admin@test.com`
   - **Blocked First Name Patterns**: Add patterns to block in first names (one per line)
     - Example: `test`, `fake`, `admin`, `user`
   - **Blocked Last Name Patterns**: Add patterns to block in last names (one per line)
     - Example: `test`, `fake`, `admin`, `user`
   - **Error Message**: Customize the error message shown when registration is blocked

### How It Works

The extension validates customer registration data during:
- **Customer Account Creation**: When users create new accounts
- **Guest Checkout**: When guests place orders without creating accounts
- **Registered Customer Checkout**: When registered customers update their information

If any of the configured patterns are detected in the email domain, specific email address, first name, or last name, the registration/checkout process will be blocked with the configured error message.

## Further Reading

- [Adobe Commerce merchants to be hit with TrojanOrders this season](https://sansec.io/research/trojanorder-magento)
- [Magento stores targeted in massive surge of TrojanOrders attacks](https://www.bleepingcomputer.com/news/security/magento-stores-targeted-in-massive-surge-of-trojanorders-attacks/)
- [Surge in TrojanOrders Attacks on Magento 2 E-commerce Sites](https://cyberfraudcentre.com/surge-in-trojanorders-attacks-on-magento-2-e-commerce-sites)
- [Magento 2: Fake customer order came through with weird code instead of customer name](https://magento.stackexchange.com/questions/358839/magento-2-fake-customer-order-came-through-with-weird-code-instead-of-customer)
- [Despite "Allow Guest Checkout" set to "No" it's possible to place a guest order with the guest-carts REST API #36691](https://github.com/magento/magento2/issues/36691)

<br>

<div style="text-align: center;">
    <a href="https://github.com/magedin/magento2-module-trojan-request-blocker">
        <img src="https://raw.githubusercontent.com/magedin/assets/c0cd4f15cee6580c6c96848400cf089e91417529/images/logo/magedin_horizontal.svg?raw=true" width="200" alt="MagedIn Technology" title="MagedIn Technology"/>
    </a>
</div>
