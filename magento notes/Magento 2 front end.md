- install new project
    ```php
    
    1- Create new folder (Etlala)
    2- Open folder in vs code
    3- curl -s <https://raw.githubusercontent.com/markshust/docker-magento/master/lib/template> | bash
    4- Create src folder
    5- At src folder ==> git clone <https://labcrocogit.crocoit.com/backend/magento/etlala.git>
    6- Put database file in src folder (dbetlala.sql)
    7- bin/start --no-dev
    8- bin/mysql < src/dbetlala.sql
    9- bin/copytocontainer --all
    10- bin/composer install
    11- bin/magento app:config:import
    12- bin/setup-domain (local.etlala)
    13- bin/restart
    14- open <https://local.etlala>
    ```
    
- magento commands
    
    ```php
    bin/magento c:c
    ```
    
    ```php
    bin/magento c:f
    ```
    
    ```php
    bin/magento setup:static-content:deploy -f
    ```
    
    ```php
    bin/magento setup:di:compile
    ```
    
    ```php
    bin/magento setup:upgrade
    ```
    
    ```php
    bin/magento deploy:mode:set developer
    ```
    
    ```php
    bin/magento deploy:mode:set developer
    ```
    
    ```php
    cd src
    rm -rf var/cache/* var/view_preprocessed/* generated/* pub/static/* 
    ```
    
    ```php
    bin/magento s:up && bin/magento setup:di:compile && bin/magento s:s:d -f
    
    ```
    
    ```php
	bin/magento setup:upgrade && bin/magento setup:di:compile && bin/magento setup:static-content:deploy -f && bin/magento cache:flush
    ```
    
- Create account on magento dashboard admin:
    
```php
bin/magento admin:user:create --admin-user="abdo.ragab" --admin-password="abdo@123" [--admin-email="abdo@gmail.com](mailto:--admin-email=%22mo123@gmail.com)" --admin-firstname="abdo" --admin-lastname="ragab"
```
    
- git commands
    
    ```markdown
    git pull origin staging 
    ```
    
    ```markdown
    git checkout [branch_name]
    ```
    
    ```markdown
    git branch
    git status
    git add (files paths that I have changed)
    git commit -m ""
    ```
    
    ```markdown
    git push origin TASK-2025-00498-Create-Account-Edits
    ```
    
    ```markdown
    
    Delete commit:
    git log --oneline
    git reset --hard <commit-hash>
    ```
    
- use `jquery` in magneto
    
    ```jsx
    require([
        'jquery',
        'Magento_Customer/js/customer-data'
    ], function ($, customerData) {
        $(document).ready(function () {
            // your code goes here
        });
    });
    ```
    
- show variable `php`
    
    ```php
        <?php echo $partner['payment_source']; ?>
    ```
    
- log `php` variable in `js`
    
    ```jsx
        var helperData = <?php echo json_encode($partner['payment_source']); ?>;
        console.log(helperData);
    ```
    
- change the title of the page
    
    ```
        <referenceBlock name="page.main.title">
            <action method="setPageTitle">
                <argument translate="true" name="title" xsi:type="string">My Rentals</argument>
            </action>
        </referenceBlock>
    ```
    
- Add image in `file.phtml`
    
    ```php
    <img src="<?php echo $block->getViewFileUrl('images/logout.jpg'); ?>" alt="Logout">
    ```
    
- text translatable
    
    ```php
    in phtml files ===> <a href="#"><?= __('Click to download'); ?></a>
    in html files ===> <p data-bind="i18n: 'Hello, World!'"></p>
    ```
    
- get store view code
    
    ```php
    <?php
    /** @var \\Magento\\Store\\Model\\StoreManagerInterface $storeManager */
    $objectManager = \\Magento\\Framework\\App\\ObjectManager::getInstance();
    $storeManager = $objectManager->get(\\Magento\\Store\\Model\\StoreManagerInterface::class);
    $storeCode = $storeManager->getStore()->getCode();
    ?>
    
    href="/<?php echo $storeCode; ?>/"
    ```
    
- how to write links in `phtml`
    
    ```php
    <li><a href="<?php echo $block->getUrl('customer/account'); ?>"><?php echo __('Dashboard'); ?></a></li>   
                
    href="<?= $escaper->escapeUrl($block->getUrl('customer/account/edit')) ?>"
    
    href="<?= $block->getUrl('customer/account/edit') ?>"         
    ```
    
- how to get block inside block `phtml`
    
```xml
    <?= $block->getLayout()->createBlock(\\Magento\\Framework\\View\\Element\\Template::class)->setTemplate('Magento_Sales::order/newarrival.phtml')->toHtml() ?>
```

- to add class object
```php
$marketplaceBlock = $block->getLayout()->createBlock(

\Webkul\Marketplace\Block\Product\Productlist::class

);
```
- how to get layout `xml` inside layout.
    
    ```xml
        <update handle="customer_account"/>
    		// (used to include the layout and blocks of another layout handle into the current one.)
    ```
    
- create modal using `Magento_Ui/js/modal/modal`
    
    ```php
    <!-- Modal HTML -->
    <div id="my-modal" style="display:none;">
        <div class="modal-inner-content">
            <p>This is a custom modal!</p>
        </div>
    </div>
    
    <button id="open-modal" type="button" class="action-primary">
        Open Modal
    </button>
    ```
    
    ```php
    <script type="text/javascript">
        require([
            'jquery',
            'Magento_Ui/js/modal/modal'
        ], function($, modal) {
            var options = {
                type: 'popup', // or 'slide'
                title: 'My Modal Title',
                buttons: [{
                    text: $.mage.__('Close'),
                    class: 'action-secondary',
                    click: function () {
                        this.closeModal();
                    }
                }]
            };
    
            var popup = modal(options, $('#my-modal'));
    
            // Open the modal (for example, on button click)
            $('#open-modal').on('click', function() {
                $('#my-modal').modal('openModal');
            });
        });
    </script>
    
    ```

#  Translation 

## 1. PHTML (PHP Template)
```php
<?= __('Your text here') ?>
```
---
## 2.  JavaScript
```javascript
alert($t('Something went wrong'));
```
---
## 3. HTML with Knockout.js
```html
<button data-bind="i18n: 'Save changes'"></button>
```
---
## 4. XML Layout
```xml
<label translate="true">Your translated text here</label>
```

---
