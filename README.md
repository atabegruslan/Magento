# Magento 2

## Simple start to end demo

1. SignUp to Magento: https://developer.paypal.com/developer/accounts/ and download Magento

2. SignUp to Paypal: https://www.paypal.com/en/webapps/mpp/country-worldwide

3. Auto-generate sandbox Paypal accounts: https://www.paypal.com/vn/signin

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal.png)

4. Install Magento. Then go to the admin size and start setting up:

5. Catalog > Product > Create new Product

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/product.png)

6. Connect Magento to Paypal: Store > Setting > Configuration. Sales > Payment Methods. Other Paypal Payment Solutions > Payments Standard.

Copy over Paypal's sandbox seller account's: email, username, secret & API signature.

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal_setup_1.png)

![](https://raw.githubusercontent.com/atabegruslan/Magento/v2/Illustrations/paypal_setup_2.png)

7. Create a new user at the frontend.

8. Go shopping - Result: https://ruslan-website.com/misc/magento_demo1_result_video/

9. Only after you submit the order's invoice, you would see the transfer of money from buyer's account to the seller's account.

---

## Common problems:

- https://magento.stackexchange.com/questions/37647/admin-not-working-in-localhost
- https://magento.stackexchange.com/questions/251926/magento-2-3-its-not-working-properly-in-localhost
- It's much more convenient not to have Magento on Windows
