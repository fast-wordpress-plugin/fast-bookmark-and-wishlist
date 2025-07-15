# Configuration

The plugin provides a settings page under **Settings > Fast Bookmark** to configure:

![Config Fast bookmark plugin](/assets/img/config-sidebar.jpg)

or you can click on **plugins > settings**
![Config Fast bookmark and wishlist for Woocommerce plugin](/assets/img/plugin-setting.jpg)

- **Custom CSS**: Override default styles, saved to `assets/css/bookmark-user-custom.css`. Leave this field empty to prevent overriding the default styles. If you choose to override the default CSS, you can always download it for customization. Remember, either the default CSS or your custom CSS will be applied.
- **Bookmarks Per Page**: Set the number of bookmarks displayed per page (1-32).
- **Auto Append**: Enable/disable automatic bookmark button placement for posts.
- **Bookmark Button Position (Posts)**: Choose where the bookmark button appears (e.g., in content, after title).
- **Woocommerce Integration** (if active):
  - **Auto Append PLP/PDP**: Enable/disable bookmark buttons on Product Listing Page (PLP) and Product Detail Page (PDP).
  - **Woocommerce Button Position**: Select button placement (e.g., before/after add-to-cart form).
- **Content Template Path**: Specify a custom theme template for rendering bookmarked posts. Otherwise it use default as fallback.
- **Shortcode**: Use `[bookmarked_posts]` or `[wishlist_products]` to display bookmarked posts or products.

If your Woocommerce plugin is not active, you will not see the Woocommerce options in the settings.