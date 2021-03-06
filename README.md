# Magento 2

## Simple start to end demo

https://www.youtube.com/playlist?list=PLJ1EBN1Sm2mAaamk0eGoOz-7givyXqaco

1. Get Magento: https://www.mageplaza.com/devdocs/how-install-magento-2-ubuntu.html
    - SignUp to Magento: https://magento.com/tech-resources/download then https://devdocs.magento.com/guides/v2.4/install-gde/composer.html
    - Download zip at: https://www.mageplaza.com/download-magento/
    - Clone Guthub repo: https://github.com/magento/magento2/

Preliminaries:
- If visit `{domain}/project_name/setup/` and see `Please note Magento Web Setup Wizard has been removed since version 2.3.7.`, `//$menu->remove('Magento_Backend::setup_wizard');` won't work. 
    - Instead see: https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html . In other words: Use CLI to setup (ie: `bin/magento  whatever_commands`)
    - https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli.html
        ```
        bin/magento setup:install --base-url=http://localhost/magento2/ \
        --db-host=localhost --db-name=xxx --db-user=xxx --db-password=xxx \
        --admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
        --admin-user=admin --admin-password=admin123 --language=en_US \
        --currency=USD --timezone=America/Chicago
        ```
    - You will see `app/etc/env.php` created. You will find your admin URL in there under `backend.frontName`. You can then log into the admin backoffice by visiting `{domain}/magento2/{admin_uri}` with the `admin-user & admin-password` provided above.
- In `app/etc/di.xml`: Change `<item name="view_preprocessed" xsi:type="object">Magento\Framework\App\View\Asset\MaterializationStrategy\Symlink</item>` to `<item name="view_preprocessed" xsi:type="object">Magento\Framework\App\View\Asset\MaterializationStrategy\Copy</item>`

2. SignUp to Paypal: https://www.paypal.com/en/webapps/mpp/country-worldwide , https://www.paypal.com/vn/signin

3. Auto-generate sandbox Paypal accounts: https://developer.paypal.com/developer/accounts/ 

The default business is the seller. The default personal is the buyer.

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal.png)

4. Install Magento. Then go to the admin size and start setting up:

5. Catalog > Product > Create new Product

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/product.png)

6. Connect Magento to Paypal: Store > Setting > Configuration. Sales > Payment Methods. Other Paypal Payment Solutions > Payments Standard.

Copy over Paypal's sandbox seller account's: email, username, secret & API signature.

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal_setup_1.png)

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal_setup_2.png)

7. Create a new user at the frontend.

8. Go shopping. When it's time to pay by Paypal, use Paypal's sandbox buyer account's username & secret.

9. Result: https://raw.githubusercontent.com/atabegruslan/Others/master/Illustrations/magento_demo_1.mp4

10. Only after you submit the order's invoice, you would see the transfer of money from buyer's account to the seller's account.

---

## Modules

### Skeleton

- app/code/Namespace/ModuleName/
    - registration.php
    - etc/
        - module.xml

`registration.php`
```php
<?php
\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::MODULE,
    'Namespace_ModuleName',
    __DIR__
);
```

`etc/module.xml`
```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Namespace_ModuleName" setup_version="1.0.0"/>
</config>
```

### The 'meat' of the module

This is 1 example: https://bsscommerce.com/blog/create-admin-menu-in-magento-2/
- https://www.mageplaza.com/magento-2-module-development/create-admin-menu-magento-2.html
- https://www.mageplaza.com/magento-2-module-development/
- https://www.mageplaza.com/magento-2-module-development/magento-2-routing.html#admin-route

### Publish

After creating all the necessary files run:  
```
php bin/magento setup:upgrade
php bin/magento cache:clean
php bin/magento indexer:reindex
php bin/magento setup:static-content:deploy # If you found that the CSS and JS files missing
```

### Watch Tutorials

1. https://www.youtube.com/watch?v=aT1AnhDzYYM
2. https://www.youtube.com/watch?v=CwsxIQLuvBU

## Common problems:

- https://magento.stackexchange.com/questions/37647/admin-not-working-in-localhost
- https://magento.stackexchange.com/questions/251926/magento-2-3-its-not-working-properly-in-localhost
- It's much more convenient not to have Magento on Windows
