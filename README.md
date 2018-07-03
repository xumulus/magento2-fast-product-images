Join us in our fight to kill image loaders and spinners. They do nothing to improve the user experience. 

Read more about it [here](https://xumulus.com/kill-the-loader-how-to-improve-your-magento-2-product-page-load-time/ "How to speed your Magento product page load").

Uou can see it live [here](https://demo.xumulus.com/breathe-easy-tank.html)

# magento2-fast-product-images
Magento 2 fast product images removes the loading image from product images.

The default Magento 2 behavior for product images is to load a spinner, and then load all the images in the fotorama gallery. This results in the spinner being up until the dom loads, and js can take over and replace it. It makes even the fastest Magento 2 site seem slow. 

This module is quite simple in that it replaces the spinner with the first image in the gallery. So now, the page should simply show the image, and not make you feel like you are waiting for it to load. It has a few challanges in that the JS for fotorama is in the core, as well as there are many themes customizing the gallery template. 

If you have changed to your Magento_Catalog/templates/product/view/gallery.phtml file then you surely will need to make some changes to this. 

# Installation
```
composer config repositories.magento2-fast-product-images git git@github.com:xumulus/magento2-fast-product-images.git
composer require xumulus/magento2-fast-product-images:dev-master -n
bin/magento module:enable Xumulus_FastGalleryLoad
bin/magento setup:upgrade
bin/magento setup:static-content:deploy
```
# Usage

Once installed, you will then need to enable the module Stores->Config->Xumulus->Fast Gallery Load

There are no admin settings; the module can be disabled if you would like to return to the default behavior.

# Theme Modifications

If you are using a packaged theme, and it includes a ../Magento_Catalog/templates/product/view/gallery.phtml, it may require modification.

Genarally the approach is to copy the JavaScript rendered html after a page load, then integrate that into the gallery.phtml file so that it will render the html as needed the first time.  This allows us to not have to reengineer fotorama.js and allows things like configurable products to still change the image upon colort selection for example. 

Much of these changes could be applied to your gallerty.phtm in your theme. 

# Future Plans

Were waiting a bit after this to determine next steps.  Contact use at sales@xumulus.com with questions.

Release Notes:
7/01/2018 Intial builds, expermentation. We understand some of this module could be optimized and code moved to block code etc but have not done that in the intial release.
