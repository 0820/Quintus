1. Create a vendor directory
   - app/design/frontend/MyVendor/

2. Create custom theme
   - app/design/frontend/MyVendor/my_theme 

3. Declare a parent theme
   - set parent theme in theme.xml
   
   theme.xml
   ```xml
   <theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"xsi:noNamespaceSchemaLocation="../../../../../lib/internal/Magento/Framework/Config/etc/theme.xsd">
      <title>New theme</title> <!-- your theme's name -->
      <parent>Magento/blank</parent> <!-- parent Vendor/theme or empty -->
      <media>
         <preview_image>media/preview.jpg</preview_image> <!-- the path to your theme's preview image -->
      </media>
   </theme>
   ```
4. Make new directories
