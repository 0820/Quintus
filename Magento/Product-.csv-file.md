##The CSV File Structure

Let’s have a look at CSV file structure for Magento 2 product import. Below, you can find a detailed description of its columns.

+ sku – a unique product identifier used as a key product attribute in the Magento 2 core. It is required for all products and should be unique for each of them. sku can include both digits and letters without spaces separated with underscores (_) and dashes (-).
+ store_view_code – an associated store view code. The column can be empty if an associated store / website have a single sub item.
+ attribute_set_code – a product attribute set code. Create and configure an attribute set before importing products into Magento 2. It should look exactly the same as an attribute set name including capital letters (e.g. “Default”, “Man shoes” etc.)
+ product_type            – the type of an imported product. Use only lowercase letters (small, configurable etc.)
+ categories - product categories in Magento 2 differs from ones utilized in Magento 1, where comma separated category ids are used. In Magento 2, full names of assigned categories, including full path, are required. Besides, assigned categories should be separated by |. For instance, “Default Category/Gear|Default Category/Gear/Bags” means that product should be assigned to both Gear and Bags categories. The latest one is a subcategory of Gear.
+ product_websites – an associated product website code. Use lowercase letters only (e.g. “base”).
+ name - a product name.
+ description - a product description.
+ short_description - a short description of a product. Both, description and short description, could include valid HTML tags.
+ weight - a weight of a product. Requires using the following format 1.00000.
+ product_online - enables or disables products. Use 1 or 0 respectively.
+ tax_class_name - a product tax class. Allows using capital later and spaces, like in Magento 2 backend (e.g. “Taxable Goods”).
+ visibility - a visibility of a product (e.g. “Catalog, Search”, “Not Visible Individually” etc.).
+ price - a price of a product (e.g. 34.000).
+ special_price - a special price of a product (e.g. 34.000).
+ special_price_from_date - time when Magento starts using a special price instead of a default one (e.g. ’2015-09-01 15:26:29’).
+ special_price_to_date – time when MAgento stops using a special price (e.g. ’2015-09-01 15:26:29’).
+ url_key - an URL key of product. In case of an empty field, a value is generated automatically based on a product name.
+ meta_title – a meta title of a product.
+ meta_keywords - product meta keywords
+ meta_description - a product meta description
+ base_image - the main product’s image and its path. Should be uploaded to  /pub/media/import. The path of /sample_data/m/b/mb01-blue-0.jpg has the following structure: /pub/media/import/sample_data/m/b/mb01-blue-0.jpg. In addition, you can use a direct URL of an image, such as http://site.com/images/some_image.jpg.
+ base_image_label - a label of a base product image.
+ small_image - a name and a path related to a small product image. Should be also uploaded to /pub/media/import. The path of /sample_data/m/b/mb01-blue-0.jpg has the following structure: /pub/media/import/sample_data/m/b/mb01-blue-0.jpg. In addition, you can use a direct URL of an image, such as http://site.com/images/some_image.jpg.
+ small_image_label - a label of a small product image.
+ thumbnail_image – a name and a path related to a thumbnail product image. Should be uploaded to /pub/media/import as well. The path of /sample_data/m/b/mb01-blue-0.jpg has the following structure: /pub/media/import/sample_data/m/b/mb01-blue-0.jpg. In addition, you can use a direct URL of an image, such as http://site.com/images/some_image.jpg.    
+ thumbnail_image_label - a product thumbnail label
+ created_at - time when a product was created. Use the following format: yyyy-mm-dd hh-mm-ss (e.g. 2015-09-01 22:26:27). If the field is empty, date and time of data base record are used.
+ updated_at - time when a product was updated in. Use the following format: yyyy-mm-dd hh-mm-ss (e.g. 2015-09-01 22:26:27). If the field is empty, date and time of data base record are used.
+ new_from_date - sets a product as “new” from the specified date. Use the following format: yyyy-mm-dd hh-mm-ss (e.g. 2015-09-01 22:26:27).        
+ new_to_date - stops displaying a product as “new” from the specified date. Use the following format: yyyy-mm-dd hh-mm-ss (e.g. 2015-09-01 22:26:27).       
+ display_product_options_in - it is a new feature introduced in Magento 2 which specifies a place on a product page where a block with options should be displayed (e.g. “Block after Info Column”).
+ map_price – a minimum price of a product.
+ msrp_price - a product’s MSRP price.
+ map_enabled - use it to enable / disable a product’s minimum price.
+ gift_message_available - shows that a gift message is available and will be displayed for a particular product.
+ custom_design – a custom design of a product page.      
+ custom_design_from - a starting date for a custom design of a product page.
+ custom_design_to - an end date for a custom design of a product page.
+ custom_layout_update – a custom XML layout for a product page
+ page_layout - a product page layout (e.g. 1 Column). If empty the field is empty, a default product layout is used.
+ product_options_container – a product options container.
+ msrp_display_actual_price_type  - a type of a product’s MSRP price.
+ country_of_manufacture - a country of origin.     
+ additional_attributes - import of product custom options and data related to a simple product associated to a configurable product. A sample value for a simple product associated to configurable product: “color=Red,has_options=0,required_options=0,size_pants=32” (Color attribute is “Red,” simple product has options in Magento 2: has_options = 0 – no required options, size pants attribute value is 32). A sample value for a configurable product in Magento 2 – “has_options=1,required_options=1” (Product has required options, simple product SKU is associated in the _associated_sku column ).
+ qty - a quantity of a particular product in stock.      
+ out_of_stock_qty - an out of stock quantity of a particular product.
+ use_config_min_qty - use minimum quantity value from config.
+ is_qty_decimal - set 1 if a quantity can be decimal.         
+ allow_backorders - set 1 if backorders are enabled.
+ use_config_backorders - use a default system value for backorder options (enable / disable).
+ min_cart_qty - a minimum required quantity of a product in shopping cart.
+ use_config_min_sale_qty - use a default config value for determining a minimum quantity of a sale product.
+ max_cart_qty – a maximum quantity of a product in a shopping cart.     
+ use_config_max_sale_qty –  use a default config value to determine a maximum quantity of a product in a shopping cart.
+ is_in_stock – 1 – a product is in stock, 0 – a product is out of stock.
+ notify_on_stock_below –  set a minimum product quantity to start a notification about a low stock level.
+ use_config_notify_stock_qty – use a default system value for a product’s low stock notification.
+ manage_stock - to control a stock quantity of a product set 1. By setting 0 you allow  Magento 2 to consider a product has an unlimited stock level.
+ use_config_manage_stock - use a default system configuration value for stock management.
+ use_config_qty_increments - use a product quantity increment from current store configuration. Set 1 to enable; set 0 to disable.
+ qty_increments - a product quantity increment.
+ use_config_enable_qty_inc - use a default store configuration value to enable a product quantity increment.
+ enable_qty_increments - set 1 or 0 to enable or disable product quantity increment.
+ is_decimal_divided - set 1 if a product quantity increment can be decimal.
+ website_id - an associated product website ID
+ related_skus - related products SKUs separated with commas (e.g. 24-WG085_Group,24-WG086,24-WG083-blue,24-UG01)
+ crosssell_skus - cross-sale product SKUs separated with commas (e.g. 24-WG085_Group,24-WG086,24-WG083-blue,24-UG01)
+ upsell_skus - upsallers product SKUs separated with comma (e.g. 24-WG085_Group,24-WG086,24-WG083-blue,24-UG01)
+ additional_images - additional product images (product media gallery) separated with commas. Images should be uploaded to /pub/media/import. The path of /sample_data/m/b/mb01-blue-0.jpg has the following structure: /pub/media/import/sample_data/m/b/mb01-blue-0.jpg. In addition, you can use a direct URL of an image, such as http://site.com/images/some_image.jpg.                                      
+ additional_image_labels - Сomma separated labels for additional product images from the previous column.
+ _associated_sku - an associated simple product SKU for a configurable product (several values should be separated with commas).     
+ _associated_default_qty - a default quantity for associated products
+ _associated_position - associated products position, based on the _associated_sku column
