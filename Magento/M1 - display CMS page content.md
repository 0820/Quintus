__Magento get CMS page content anywhere without header and footer using below script.__

```php
$page = Mage::getModel('cms/page');
$page->setStoreId(Mage::app()->getStore()->getId());
$page->load('CMS-IDENTIFIER-HERE','identifier'); //EDIT IN THIS LINE
$helper = Mage::helper('cms');
$processor = $helper->getPageTemplateProcessor();
echo $html = $processor->filter($page->getContent());
```
