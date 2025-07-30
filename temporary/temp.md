```php

<?php
/**
 * Webkul Software.
 *
 * @category  Webkul
 * @package   Webkul_Marketplace
 * @author    Webkul
 * @copyright Copyright (c) Webkul Software Private Limited (https://webkul.com)
 * @license   https://store.webkul.com/license.html
 */
/** @var $block \Webkul\Marketplace\Block\Product\Productlist */

$helper = $this->helper(\Webkul\Marketplace\Helper\Data::class);
$paramData = $this->getRequest()->getParams();
$filter = '';
$filterStatus = '';
$filterDateFrom = '';
$filterDateTo = '';
if (isset($paramData['s'])) {
    $filter = $paramData['s'] != '' ? $paramData['s'] : '';
}
if (isset($paramData['status'])) {
    $filterStatus = $paramData['status'] != '' ? $paramData['status'] : '';
}
if (isset($paramData['from_date'])) {
    $filterDateFrom = $paramData['from_date'] != '' ? $paramData['from_date'] : '';
}
if (isset($paramData['to_date'])) {
    $filterDateTo = $paramData['to_date'] != '' ? $paramData['to_date'] : '';
}
$products_coll = $block->getAllProducts();
if ($helper->getIsProductApproval() || $helper->getIsProductEditApproval()) {
    $enabledStatusText = __('Approved');
    $disabledStatusText = __('Pending');
} else {
    $enabledStatusText = __('Enabled');
    $disabledStatusText = __('Disabled');
}
$websiteNames = $block->getWebsiteNames();
$customer = $helper->getCustomer();
$ismangedByEtlala = 0;
$requestManagedEtlala = 0;
if($customer->getId())
{
    $ismangedByEtlala = $customer->getIsManagedByEtlala(); //if value 1 means request accepted, 2 means request declined
    $requestManagedEtlala = $customer->getRequestEtlalaManaged(); // if value 1 mean request is send
}

if ((int) $ismangedByEtlala === 1) {
    $activeClass = 'accepted';
} elseif ((int) $ismangedByEtlala === 2) {
    $activeClass = 'declined';
} elseif ((int) $requestManagedEtlala === 1 && (int) $ismangedByEtlala === 0) {
    $activeClass = 'requested';
} else {
    $activeClass = null;
}

if ($activeClass === 'accepted') {
    $iconUrl = $block->getViewFileUrl('Webkul_Marketplace::images/Approved.png');
} elseif ($activeClass === 'requested') {
    $iconUrl = $block->getViewFileUrl('Webkul_Marketplace::images/Pending.png');
} else {
    $iconUrl = '';
}

?>
<?php
/** [@var](profile/var) \CrocoIT\Rental\Helper\Data $rentalHelper */
$rentalHelper = $this->helper('CrocoIT\Rental\Helper\Data');
?>

<form
    action="<?= /* @noEscape */
        $block->getUrl('marketplace/product/add/set/4/type/configurable/', ['_secure' => $block->getRequest()->isSecure()]) ?>"
    enctype="multipart/form-data" method="post" id="form-customer-product-new" data-mage-init='{"validation":{}}'
    class="form-customer-product-new" id="form-customer-product-new">
    <div class="wk-mp-design">
        <fieldset class="fieldset info wk-mp-fieldset">
            <legend class="legend two-btn">

                <button type="button" class="button wk-mp-btn wk-mp-btn-manage <?= $activeClass ?>"
                    id="managed_by_etlala_btn" <?= $activeClass === 'requested' ? 'disabled' : '' ?>>
                    <?php if (!empty($iconUrl)): ?>
                    <img src="<?= $escaper->escapeUrl($iconUrl) ?>" alt="Status Icon" />
                    <?php endif; ?>
                    <span>
                        <span>
                            <?php if ($activeClass === 'requested'): ?>
                            <?= /* @noEscape */ __('pending approval') ?>
                            <?php else: ?>
                            <?= /* @noEscape */ __('Managed by Etlala') ?>
                            <?php endif; ?>
                        </span>
                    </span>
                </button>

                <button class="button wk-mp-btn wk-mp-btn-first" id="list-new-item-btn" title="Continue">
                    <span><span><?= /* @noEscape */ __('List A New Item') ?></span></span>
                </button>
            </legend>
            <?php $isPaused=false ?>
            <div class="pause-btn-container <?php echo $isPaused ? 'paused' : ''; ?>">
                <button class="button pause-btn" id="pause-btn">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
                        <path
                            d="M13.3333 15.8327C12.875 15.8327 12.4828 15.6696 12.1567 15.3435C11.8306 15.0174 11.6672 14.6249 11.6667 14.166V5.83268C11.6667 5.37435 11.83 4.98213 12.1567 4.65602C12.4833 4.32991 12.8756 4.16657 13.3333 4.16602C13.7911 4.16546 14.1836 4.32879 14.5108 4.65602C14.8381 4.98324 15.0011 5.37546 15 5.83268V14.166C15 14.6244 14.8369 15.0169 14.5108 15.3435C14.1847 15.6702 13.7922 15.8332 13.3333 15.8327ZM6.66667 15.8327C6.20833 15.8327 5.81611 15.6696 5.49 15.3435C5.16389 15.0174 5.00056 14.6249 5 14.166V5.83268C5 5.37435 5.16333 4.98213 5.49 4.65602C5.81667 4.32991 6.20889 4.16657 6.66667 4.16602C7.12444 4.16546 7.51694 4.32879 7.84417 4.65602C8.17139 4.98324 8.33444 5.37546 8.33333 5.83268V14.166C8.33333 14.6244 8.17028 15.0169 7.84417 15.3435C7.51806 15.6702 7.12556 15.8332 6.66667 15.8327Z"
                            fill="white" />
                    </svg>

                    <span>
                        <span><?= /* @noEscape */ $isPaused ? __('Resume My Wardrobe') : __('Pause My Wardrobe') ?></span>
                    </span>
                </button>

                <input type="date" class="start-date" name="start_date" aria-label="Start Date" style="display:none;">
                <input type="date" class="end-date" name="end_date" aria-label="End Date" style="display:none;">

                <div id="calendar-modal" class="flatpickr-calendar-popup">
                    <div class="modal-body-content">
                        <div id="flatpickr-calendar" style="display: none;"></div>

                        <button type="submit" class="action primary pause-confirmation" disabled>
                            <?= $block->escapeHtml(__('pause Confirmation')) ?>
                        </button>
                    </div>
                </div>

            </div>

            <?php if (!$products_coll || count($products_coll) == 0): ?>
            <div class=" list-easier">
                <p><?= __('Listing your item couldn\'t be easier... <br /> Why not try it out?') ?></p>
                <button class="button wk-mp-btn-second" title="Continue" type="submit">
                    <span><span><?= /* @noEscape */ __('List A New Item') ?></span></span>
                </button>
            </div>
            <?php else: ?>
            <?= /* @noEscape */ $block->getChildHtml('myproductlist') ?>
            <?php endif; ?>

            <?= /* @noEscape */ $block->getBlockHtml('formkey') ?>
            <?= /* @noEscape */ $block->getBlockHtml('seller.formkey') ?>
        </fieldset>
    </div>
</form>


<div class="wk-mp-design wee">
    <fieldset class="fieldset info wk-mp-fieldset">
        <!-- <legend class="legend">
            <span><?= $escaper->escapeHtml(__('Product List')) ?></span>
        </legend> -->
        <div class="grid">
            <div class="hor-scroll">
                <!-- <form
                    action="<?= $escaper->escapeUrl($block->getUrl('marketplace/product/productlist', ['_secure' => $this->getRequest()->isSecure()]))?>"
                    method="get" id="form-productlist-filter" name="formProductlistFilter"
                    data-mage-init='{"validation":{}}' autocomplete="off">
                    <table cellspacing="0" class="border wk-mp-list-table">
                        <thead>
                            <tr id="wk-mp-tr-heading">
                                <th><span><?= $escaper->escapeHtml(__('Product Name')) ?></span></th>
                                <th><span><?= $escaper->escapeHtml(__('Date')) ?></span></th>
                                <th><span><?= $escaper->escapeHtml(__('Product Status')) ?></span></th>
                                <th><span>&nbsp;</span></th>
                            </tr>
                        </thead>
                        <tbody class="wk-mp-body" id="colender-check">
                            <tr>
                                <td>
                                    <input type="text" class="input-text" name="s"
                                        placeholder='<?= $escaper->escapeHtml(__('Search by product name')) ?>'
                                        value="<?= $escaper->escapeHtml($filter)?>" />
                                </td>
                                <td>
                                    <span class="wk-mp-td-span">
                                        <?= $escaper->escapeHtml(__('From: ')) ?>
                                        <input name="from_date" id="special-from-date" class="input-text"
                                            value="<?= $escaper->escapeHtml($filterDateFrom)?>" />
                                    </span>
                                    <span class="wk-mp-td-span">
                                        <?= $escaper->escapeHtml(__('To: ')) ?>
                                        <input name="to_date" id="special-to-date" class="input-text"
                                            value="<?= $escaper->escapeHtml($filterDateTo)?>" />
                                    </span>
                                </td>
                                <td>
                                    <select name="status" class="input-text">
                                        <option value=""><?= $escaper->escapeHtml(__('All')) ?></option>
                                        <option value="1"
                                            <?php if ($filterStatus == 1) { echo 'selected="selected"'; }?>>
                                            <?= /* @noEscape */ $enabledStatusText ?>
                                        </option>
                                        <option value="2"
                                            <?php if ($filterStatus == 2) { echo 'selected="selected"'; }?>>
                                            <?= /* @noEscape */ $disabledStatusText ?>
                                        </option>
                                    </select>
                                </td>
                                <td>
                                    <button class="button" title="Save" type="submit">
                                        <span><span><span><?= $escaper->escapeHtml(__('Submit')) ?></span></span></span>
                                    </button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </form> -->
                <div data-bind="scope: 'product-list-component'">
                    <?php if ($products_coll && count($products_coll)): ?>
                    <form
                        action="<?= $escaper->escapeUrl($block->getUrl('marketplace/product/massDelete', ['_secure' => $this->getRequest()->isSecure()])) ?>"
                        method="post" id="form-productlist-massdelete" name="formProductlistMassdelete"
                        data-mage-init='{"validation":{}}'>
                        <?= $block->getBlockHtml('formkey')?>
                        <!-- <button class="button" title="<?= $escaper->escapeHtml(__('Delete Products')) ?>" type="submit"
                            style="float: left;padding: 5px 5px 5px 0;" id="mass-delete-butn">
                            <span><span><?= $escaper->escapeHtml(__('Delete Products')) ?></span></span>
                        </button> -->
                        <!-- ko template: getTemplate() -->
                        <!-- /ko -->
                        <div class="border wk-mp-list-table wk-mp-list-container-table">
                            <?php
    $i = 0;
    foreach ($block->getAllProducts() as $products) {
        $product = $block->getProductData($products->getMageproductId());
        $salesdetail = $block->getSalesdetail($products->getMageproductId());
        $i++;
        $image_url = $block->imageHelperObj()->init($product, 'product_page_image_large')
                    ->setImageFile($product->getImage())
                    ->getUrl();
        $isApprovedBefore = $products['is_approved'];
        $statusText = ($product->getStatus() == 2) ? $disabledStatusText : $enabledStatusText;
        $websites = [];
        foreach ($product->getWebsiteIds() as $websiteId) {
            if (!isset($websiteNames[$websiteId])) continue;
            $websites[] = $websiteNames[$websiteId];
        }
        $website = implode(', ', $websites);
        ?>
                            <div
                                class="product-item card <?= ($i == count($block->getAllProducts())) ? 'wk-last_tr' : '' ?>" data-managed='managed by etlala'>
                                <!-- Approval State -->
                                <div class="state <?= $isApprovedBefore ? 'Approved' : 'Pending'; ?>">
                                    <img src="<?= $escaper->escapeUrl(
                    $isApprovedBefore
                        ? $block->getViewFileUrl('Webkul_Marketplace::images/Approved.png')
                        : $block->getViewFileUrl('Webkul_Marketplace::images/Pending.png')
                ) ?>" alt="<?= $isApprovedBefore ? 'Approved' : 'Pending'; ?>" />
                                    <?= $escaper->escapeHtml($isApprovedBefore ? 'Approved' : 'Pending'); ?>
                                </div>

                                <div class="wk-row-view">

                                    <!-- Checkbox -->
                                    <!-- <div class="checkbox">
                                    <input type="checkbox" class="mpcheckbox"
                                        name="product_mass_delete[]"
                                        value="<?= $escaper->escapeHtml($products->getMageproductId()); ?>" />
                                    </div> -->

                                    <!-- Product Image and Name -->
                                    <div class="wk-first_td">
                                        <input type="hidden" class="hidden-id"
                                            value="<?= $escaper->escapeHtml($products->getMageproductId()); ?>" />
                                        <div class="label name"
                                            title="<?= $escaper->escapeHtml($product->getName()); ?>">
                                            <span class="product-image-wrapper" data--h-bstatus="0OBSERVED">
                                                <img src="<?= $escaper->escapeUrl($image_url) ?>"
                                                    class="image image product-image-photo"
                                                    alt="<?= $escaper->escapeHtml($product->getName()); ?>" />
                                            </span>

                                            <!-- Brand/Designer Name  -->
                                            <?php if ($block->getProductBrand($product)): ?>
                                            <div class="product-brand">
                                                <span class="brand-name">
                                                    <?php echo $block->getProductBrand($product); ?>
                                                </span>
                                            </div>
                                            <?php endif; ?>

                                            <strong class="product name product-item-name">
                                                <?php if ($product->getStatus()==1 && $product->getVisibility()!=1) { ?>
                                                <a href="<?= $escaper->escapeUrl($product->getProductUrl()) ?>"
                                                    target="_blank">
                                                    <?php } ?>
                                                    <?= $escaper->escapeHtml($product->getName()); ?>
                                                    <?php if ($product->getStatus()==1 && $product->getVisibility()!=1) { ?>
                                                </a>
                                                <?php } ?>
                                            </strong>

                                            <!-- product sizes  -->
                                            <?php
                                                $productSizes = $block->getProductSizes($product); // Ensure $productSizes is an array
                                                $productSizesArray = explode(', ', $productSizes); // Split by comma and space
                                                
                                            ?>

                                            <div class="product-sizes-wrapper">
                                                <?php
        $visibleSizes = array_slice($productSizesArray, 0, 2); // Show first 2
        $hiddenSizes = array_slice($productSizesArray, 2);     // Remaining sizes
        $hiddenCount = count($hiddenSizes);
    ?>

                                                <?php foreach ($visibleSizes as $sizeName): ?>
                                                <span class="size-tag"><?= $sizeName ?></span>
                                                <?php endforeach; ?>

                                                <?php if ($hiddenCount > 0): ?>
                                                <span class="size-tag"
                                                    title="<?= htmlspecialchars(implode(', ', $hiddenSizes)) ?>">
                                                    +<?= $hiddenCount ?> Sizes
                                                </span>
                                                <?php endif; ?>
                                            </div>

                                            <!-- Rent From Price -->
                                            <?php
        			                            $minPrice = $rentalHelper->getSmallestRetailPriceByProductId($product->getId());?>
                                            <?php if ($minPrice): ?>
                                            <div class="catalog-product-rent">
                                                <span class="rent-label">Rent from </span>
                                                <span class="price"><?= $block->escapeHtml($minPrice); ?> SAR</span>
                                            </div>
                                            <?php endif; ?>

                                            <div class="product-price-box">
                                                <!-- Buy Now Price -->
                                                <?php
                                                // Get the service type attribute value
                                                $serviceType = $product->getData('service_type');

                                                // Check if service type is 'buy' and product has price
                                                if ($serviceType === 'sell' || $serviceType === 'rent_sale'):?>
                                                <div class="buy-now">
                                                    <span>Buy now </span>
                                                    <span class="price">
                                                        <?php echo number_format($block->getProductPrice($product), 2); ?>
                                                        SAR
                                                    </span>
                                                </div>
                                                <?php endif; ?>

                                                <!-- Retail Price  -->

                                                <?php if ($product->getData('seller_retail_price')): ?>
                                                <div class="old-price">
                                                    <span class="price-container">
                                                        <span class="price-wrapper">
                                                            <span class="price" style="text-decoration: line-through;">
                                                                <?php echo number_format($product->getData('seller_retail_price'), 2); ?>
                                                            </span>
                                                        </span>
                                                    </span>
                                                </div>
                                                <?php endif; ?>
                                            </div>

                                        </div>
                                    </div>

                                    <!-- Type -->
                                    <!-- <div class="product-type">
                                    <strong><?= $escaper->escapeHtml(__('Type')) ?>:</strong>
                                    <?= $escaper->escapeHtml($product->getTypeId()) ?>
                                    </div> -->

                                    <!-- Status -->
                                    <!-- <div class="product-status">
                                    <strong><?= $escaper->escapeHtml(__('Status')) ?>:</strong>
                                    <?= $escaper->escapeHtml($statusText) ?>
                                    </div> -->

                                    <!-- Quantities -->
                                    <!-- <div class="quantities">
                                    <div><strong><?= $escaper->escapeHtml(__('Qty. Confirmed')) ?>:</strong>
                                        <?= ($product->getStatus()==2 && !$isApprovedBefore) ? __('Pending') : $salesdetail['quantitysoldconfirmed']; ?>
                                    </div>
                                    <div><strong><?= $escaper->escapeHtml(__('Qty. Pending')) ?>:</strong>
                                        <?= ($product->getStatus()==2 && !$isApprovedBefore) ? __('Pending') : $salesdetail['quantitysoldpending']; ?>
                                    </div>
                                    <div><strong><?= $escaper->escapeHtml(__('Qty. Sold')) ?>:</strong>
                                        <?php if ($product->getStatus()==2 && !$isApprovedBefore) {
                                            echo __('Pending');
                                        } else { ?>
                                            <a href="<?= $escaper->escapeUrl($block->getUrl('marketplace/order/salesdetail/', ['id'=>$product->getId(), '_secure' => $this->getRequest()->isSecure()])); ?>">
                                                <?= $salesdetail['quantitysold']; ?>
                                            </a>
                                        <?php } ?>
                                    </div>
                                    </div> -->

                                    <!-- Earned Amount -->
                                    <!-- <div class="earned-amount">
                                    <strong><?= $escaper->escapeHtml(__('Earned Amount')) ?>:</strong>
                                    <?= ($product->getStatus()==2 && !$isApprovedBefore)
                                        ? __('Pending')
                                        : $block->getFormatedPrice($salesdetail['amountearned'], $helper->getCurrencySymbol()); ?>
                                    </div> -->

                                    <!-- Websites -->
                                    <!-- <div class="websites">
                                    <strong><?= $escaper->escapeHtml(__('Websites')) ?>:</strong>
                                    <?= $escaper->escapeHtml($website); ?>
                                    </div> -->

                                    <!-- <div class="edit-product">
                                        <span class="label wk-action">
                                            <img src="<?= /* @noEscape */
                                                            $block->getViewFileUrl(
                                                                'Webkul_Marketplace::images/edititem.png'
                                                            ); ?>" data-url="<?= /* @noEscape */
                                                                $block->getUrl(
                                                                    'marketplace/product/edit',
                                                                    ['id'=>$product->getId(),
                                                                    '_secure' => $block->getRequest()->isSecure()]
                                                                ) ?>" alt="<?= /* @noEscape */ __('Edit')?>"
                                                title="<?= /* @noEscape */ __('Edit')?>" class="mp-edit" />
                                        </span>
                                    </div> -->
                                    <div class="delete-btn">
                                        <button class="button" title="<?= /* @noEscape */ __('Delete Products') ?>"
                                            type="submit" id="mass-delete-butn">
                                        </button>
                                    </div>
                                </div>
                            </div>
                            <?php } ?>
                        </div>

                    </form>
                </div>
                <?php endif ?>
            </div>
        </div>
        <!-- <?php if ($block->getPagerHtml()): ?>
        <div class="order-products-toolbar toolbar bottom"><?= $block->getPagerHtml(); ?></div>
        <?php endif ?> -->
    </fieldset>
    <!-- <div class="buttons-set">
        <p class="back-link">
            <a href="javascript:;" onclick="javascript: window.history.back();" class="left">&laquo;
                <?= $escaper->escapeHtml(__('Back')) ?></a>
        </p>
    </div> -->
</div>


<script type="text/x-magento-init">
    {
        "*": {
            "Webkul_Marketplace/js/product/product-date-range": {}
        }
    }
</script>
<script type="text/x-magento-init">
    {
            "*": {
                "Magento_Ui/js/core/app": {
                    "components": {
                        "product-list-component": {
                            "component": "sellerProductList",
                            "template" : "Webkul_Marketplace/product-list"
                        }
                    }
                }
            }
        }
</script>

<script type="text/javascript">
require(['jquery', 'flatpickr', "Magento_Ui/js/modal/modal"], function($, flatpickr, modal) {
    $(document).ready(function() {
        let flatpickrInstance = null;

        // Set the minimum date (today)
        const now = new Date();
        const fromDate = now.toISOString().split('T')[0];

        // Set the maximum date (6 months from now)
        const futureDate = new Date();
        futureDate.setMonth(futureDate.getMonth() + 6);
        const toDate = futureDate.toISOString().split('T')[0];

        let currentStartDate = null;
        let endDate = null;
        let selectedDuration = 7;   //! selectedDuration

        // Flag to prevent infinite loop caused by setDate triggering onChange
        let isDateChanging = false;

        // Function to calculate end date based on start date and selected duration
        function calculateEndDate(startDate, duration) {
            const end = new Date(startDate);
            end.setDate(end.getDate() + duration); // Add the selected duration to the start date
            return end;
        }

        function initializeFlatpickr(fromDate, toDate) {
            if (flatpickrInstance) {
                flatpickrInstance.destroy();
            }

            flatpickrInstance = flatpickr('#flatpickr-calendar', {
                inline: true,
                mode: 'single',
                minDate: fromDate,
                maxDate: toDate,
                dateFormat: "Y-m-d",
                onChange: function(dates) {
                    // Avoid recursion caused by programmatic setDate
                    if (isDateChanging) {
                        isDateChanging = false;
                        return;
                    }

                    if (dates.length > 0) {
                        // Set the selected start date
                        currentStartDate = new Date(dates[0]);
                        // Calculate the end date based on the selected duration
                        endDate = calculateEndDate(currentStartDate, selectedDuration - 1);

                        // Highlight the range on the calendar by setting both start and end dates
                        isDateChanging =
                            true; // Set flag to avoid triggering onChange again
                        flatpickrInstance.setDate([currentStartDate, endDate],
                            true); // Select the range automatically


                        function formatDateToLocal(date) {
                            const year = date.getFullYear();
                            const month = ("0" + (date.getMonth() + 1)).slice(-2);
                            const day = ("0" + date.getDate()).slice(-2);
                            return `${year}-${month}-${day}`;
                        }

                        $('.start-date').val(formatDateToLocal(currentStartDate));
                        $('.end-date').val(formatDateToLocal(endDate));
                        $('.pause-confirmation').removeAttr('disabled');
                    } else {
                        console.error("No date selected.");
                    }
                },
                onDayCreate: function(dObj, dStr, fp, dayElem) {
                    // Apply range highlight based on start and end dates
                    if (currentStartDate && endDate) {
                        const dayDate = new Date(dayElem.dateObj);

                        if (dayDate >= currentStartDate && dayDate <= endDate) {
                            dayElem.classList.add(
                                'in-range'); // Apply a class for days in the range
                        }
                    }
                }
            });
        }

        var options = {
            type: 'popup',
            responsive: true,
            title: '<?= __('Pause My Wadrobe') ?>',
            buttons: [],
            modalClass: 'flatpickr-calendar-popup',
            clickableOverlay: true,
        };

        var popup = modal(options, $('#calendar-modal'));

        $('#pause-btn').on('click', function(event) {
            event.preventDefault();
            $('#calendar-modal').modal('openModal');

            $('#flatpickr-calendar').toggle();
            initializeFlatpickr(fromDate, toDate);
        });
    });
});
</script>
<script>
    require(['jquery'], function ($) {
        $(document).ready(function () {

            $('#managed_by_etlala_btn').on('click', function (e) {
                // alert(2);
                e.preventDefault();
               
                $.ajax({
                    url: '/rest/V1/productlist/update-request/status',
                    type: 'POST',
                    contentType: 'application/json', 
                    data: JSON.stringify({
                        'requestEtlalaManaged' : 1
                    }),
                    dataType: 'json',
                    success: function (response) {
                        console.log(response);
                        // if (response.success) {
                        //     // location.reload();
                        //     // alert(response.message); // Handle success
                        // } else {
                        //     console.log('Error: ' + response.message); // Handle error
                        // }
                    },
                    error: function () {
                        console.log('An error occurred while processing your request.');
                    }
                });

            });  
        
        });
    });
</script> 
```