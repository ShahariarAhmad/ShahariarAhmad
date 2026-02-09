# Complete Routes Table with Form Fields

## Product Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/products` | `product.index` | Products List (Admin) | - |
| `GET /dashboard/products/create` | `product.create` | Create New Product | **Product Information:** name, slug, short_description, description<br>**Media:** main_image, main_image_alt, gallery_images (multiple), gallery_alts<br>**Variant Options:** attributes (multiselect), attribute_options (multiselect per attribute)<br>**Variants:** (auto-generated) sku, price, stock, image_ref<br>**Pricing:** price, discount_mode (none/flat/percent), discount_value, cost, charge_tax (checkbox)<br>**Organize:** subcategory_id, sub_subcategory_id, brand_id<br>**Shipping & Inventory:** free_shipping (checkbox), weight, dimensions, low_stock_threshold<br>**SEO:** meta_title, meta_description |
| `POST /dashboard/products` | `product.store` | Save New Product | (Same as create) |
| `GET /dashboard/products/{product}/edit` | `product.edit` | Edit Product | (Same as create) |
| `PUT/POST /dashboard/products/{product}` | `product.update` | Update Product | (Same as create) |
| `DELETE /dashboard/products/{product}` | `product.destroy` | Delete Product | - |
| `POST /dashboard/products/bulk-delete` | `product.bulk-destroy` | Bulk Delete Products | product_ids (array) |
| `GET /dashboard/products/export` | `product.export` | Export Products | - |
| `PATCH /dashboard/products/{product}/flags` | `product.flags.update` | Update Product Flags | is_featured, is_new_arrival, is_best_seller |

## Brand Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/brand` | `brand.index` | Brands List | - |
| `GET /dashboard/brand/create` | `brand.create` | Create New Brand | name, slug, logo (image via Media Library) |
| `POST /dashboard/brand` | `brand.store` | Save New Brand | name, slug, logo_media_id |
| `GET /dashboard/brand/{brand}/edit` | `brand.edit` | Edit Brand | name, slug, logo_media_id |
| `POST /dashboard/brand/{brand}` | `brand.update` | Update Brand | name, slug, logo_media_id |
| `DELETE /dashboard/brand/{brand}` | `brand.destroy` | Delete Brand | - |

## Category Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/category` | `category.index` | Categories Management | - |
| `POST /dashboard/category` | `category.store` | Create Category | name, slug, image (via Media Library) |
| `POST /dashboard/category/{category}` | `category.update` | Update Category | name, slug, image_media_id, remove_image |
| `DELETE /dashboard/category/{category}` | `category.destroy` | Delete Category | - |
| `POST /dashboard/category/subcategory` | `category.subcategory.store` | Create Subcategory | name, slug, category_id (parent), image_media_id |
| `POST /dashboard/category/subcategory/{subcategory}` | `category.subcategory.update` | Update Subcategory | name, slug, category_id, image_media_id |
| `DELETE /dashboard/category/subcategory/{subcategory}` | `category.subcategory.destroy` | Delete Subcategory | - |
| `POST /dashboard/category/sub-subcategory` | `category.sub-subcategory.store` | Create Sub-subcategory | name, slug, subcategory_id (parent), image_media_id |
| `POST /dashboard/category/sub-subcategory/{subSubcategory}` | `category.sub-subcategory.update` | Update Sub-subcategory | name, slug, subcategory_id, image_media_id |
| `DELETE /dashboard/category/sub-subcategory/{subSubcategory}` | `category.sub-subcategory.destroy` | Delete Sub-subcategory | - |

## Attribute Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/attribute` | `attribute.index` | Attributes Management Page | - |
| `POST /dashboard/attribute` | `attribute.store` | Create Attribute | name, slug, type |
| `GET /dashboard/attribute/{attribute}` | `attribute.show` | View Attribute Details | - |
| `PUT /dashboard/attribute/{attribute}` | `attribute.update` | Update Attribute | name, slug |
| `DELETE /dashboard/attribute/{attribute}` | `attribute.destroy` | Delete Attribute | - |
| `GET /dashboard/attribute/{attribute}/options` | `attribute.attributes.options` | Get Attribute Options | - |
| `POST /dashboard/attribute/{attribute}/values` | `attribute.values.store` | Create Attribute Value | value, position |
| `PUT /dashboard/attribute/{attribute}/values/{value}` | `attribute.values.update` | Update Attribute Value | value, position |
| `DELETE /dashboard/attribute/{attribute}/values/{value}` | `attribute.values.destroy` | Delete Attribute Value | - |

## Review Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/reviews` | `review.index` | Reviews Management | - |
| `GET /dashboard/reviews/create` | `review.create` | Create Review | product_id, user_id, rating (1-5), title, body, reviewer_name, is_visible |
| `POST /dashboard/reviews` | `review.store` | Save New Review | product_id, user_id, rating, title, body, is_visible |
| `GET /dashboard/reviews/{review}/edit` | `review.edit` | Edit Review | rating, title, body, reviewer_name, is_visible |
| `PUT /dashboard/reviews/{review}` | `review.update` | Update Review | rating, title, body, is_visible |
| `DELETE /dashboard/reviews/{review}` | `review.destroy` | Delete Review | - |
| `DELETE /dashboard/reviews/bulk` | `review.bulk-destroy` | Bulk Delete Reviews | review_ids (array) |
| `PATCH /dashboard/reviews/{review}/visibility` | `review.toggle-visibility` | Toggle Review Visibility | is_visible (toggle) |

## Order Management (Admin)

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/orders` | `order.index` | Orders List | - |
| `GET /dashboard/orders/{order}` | `order.show` | View Order Details | - |
| `GET /dashboard/orders/{order}/edit` | `order.edit` | Edit Order | status (pending/processing/shipped/delivered/cancelled), payment_status, shipping_address, billing_address, customer_notes, admin_notes |
| `PUT /dashboard/orders/{order}` | `order.update` | Update Order | status, payment_status, tracking_number, notes |
| `DELETE /dashboard/orders/{order}` | `order.destroy` | Delete Order | - |
| `POST /dashboard/orders/{order}/assign` | `orders.assign` | Assign Order to Staff | staff_user_id |
| `POST /dashboard/orders/{order}/courier/{courier}` | `order.courier` | Assign to Courier Service | courier (redx/pathao/steadfast), recipient_name, recipient_phone, delivery_address |

## Incomplete Orders

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/orders/incomplete` | `order.incomplete` | Incomplete Orders List | - |
| `GET /dashboard/orders/incomplete/{incompleteOrder}` | `order.incomplete.show` | View Incomplete Order | - |
| `POST /dashboard/orders/incomplete/{incompleteOrder}/convert` | `order.incomplete.convert` | Convert to Complete Order | customer_info, payment_method, notes |
| `DELETE /dashboard/orders/incomplete/{incompleteOrder}` | `order.incomplete.destroy` | Delete Incomplete Order | - |
| `POST /dashboard/orders/incomplete/bulk-delete` | `order.incomplete.bulk-destroy` | Bulk Delete Incomplete Orders | order_ids (array) |

## Staff Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/staff` | `staff.index` | Staff List | - |
| `GET /dashboard/staff/create` | `staff.create` | Create New Staff | name, email, role (select: Super Admin/Admin/Customer Support/Manager), password, password_confirmation |
| `POST /dashboard/staff` | `staff.store` | Save New Staff | name, email, role, password, password_confirmation |
| `GET /dashboard/staff/{user}/edit` | `staff.edit` | Edit Staff Member | name, email, role, password (optional), password_confirmation |
| `PUT /dashboard/staff/{user}` | `staff.update` | Update Staff Member | name, email, role, password (optional) |

## Coupon Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/coupons` | `admin.coupons.index` | Coupons List | - |
| `GET /dashboard/coupons/create` | `admin.coupons.create` | Create Coupon | code, type (percentage/flat/free_shipping), value, status (active/inactive), start_at (datetime), end_at (datetime), min_cart_amount, max_discount, usage_limit_total, usage_limit_per_user, applies_to (all/products/categories), product_ids (multiselect), category_ids (multiselect), exclude_sale_items (checkbox), stackable (checkbox), notes |
| `POST /dashboard/coupons` | `admin.coupons.store` | Save Coupon | (Same as create) |
| `GET /dashboard/coupons/{coupon}/edit` | `admin.coupons.edit` | Edit Coupon | (Same as create) |
| `PUT /dashboard/coupons/{coupon}` | `admin.coupons.update` | Update Coupon | (Same as create) |
| `DELETE /dashboard/coupons/{coupon}` | `admin.coupons.destroy` | Delete Coupon | - |

## Customer Dashboard

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/customer` | `customer.dashboard` | Customer Dashboard Home | - |
| `GET /dashboard/customer/orders` | `customer.orders` | My Orders | - |
| `GET /dashboard/customer/orders/{order}` | `customer.orders.details` | Order Details | - |
| `GET /dashboard/customer/account` | `customer.account` | My Account | - |
| `GET /dashboard/customer/wishlist` | `customer.wishlist` | My Wishlist | - |
| `GET /dashboard/customer/support` | `customer.support` | Support Tickets | - |
| `POST /dashboard/customer/support/tickets` | `customer.support.tickets.create` | Create Support Ticket | subject, priority (low/normal/high/urgent), message, attachments |
| `GET /dashboard/customer/support/tickets/{ticket}` | `customer.support.ticket` | View Support Ticket | - |
| `POST /dashboard/customer/support/tickets/{ticket}/reply` | `customer.support.ticket.reply` | Reply to Support Ticket | message, attachments |
| `GET /dashboard/customer/profile` | `customer.profile` | My Profile | name, email, phone, address, city, postal_code, country |
| `PUT /dashboard/customer/profile` | `customer.profile.update` | Update Profile | name, email, phone, address, city, postal_code, country |
| `GET /dashboard/customer/change-password` | `customer.changePassword` | Change Password Page | current_password, password, password_confirmation |
| `PUT /dashboard/customer/change-password` | `customer.password.update` | Update Password | current_password, password, password_confirmation |

## Support Tickets (Admin)

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/support` | `support.index` | Support Tickets List | - |
| `GET /dashboard/support/tickets/{ticket}` | `support.ticket` | View Support Ticket | - |
| `POST /dashboard/support/tickets/{ticket}/assign` | ` support.ticket.assign` | Assign Ticket to Staff | assigned_to (staff user_id) |
| `POST /dashboard/support/tickets/{ticket}/reply` | `support.ticket.reply` | Reply to Ticket | message, attachments |
| `PUT /dashboard/support/tickets/{ticket}/status` | `support.ticket.status` | Update Ticket Status | status (open/in_progress/resolved/closed) |

## Configuration & Settings

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/config` | `config.index` | Configuration Overview | - |
| `GET /dashboard/config/website` | `config.website` | Website Configuration | - |
| `GET /dashboard/config/settings` | `config.settings.show` | View Store Settings | - |
| `POST /dashboard/config/settings` | `config.settings.update` | Update Store Settings | store_name, store_email, store_phone, store_address, currency, timezone, logo, favicon, meta_title, meta_description, facebook_url, twitter_url, instagram_url, youtube_url, link_privacy, link_returns, link_shipping, footer_text |
| `POST /dashboard/config/smtp` | `config.smtp.update` | Update SMTP Settings | smtp_host, smtp_port, smtp_username, smtp_password, smtp_encryption (ssl/tls), smtp_from_address, smtp_from_name |
| `POST /dashboard/config/pixel` | `config.pixel.update` | Update Facebook Pixel | facebook_pixel_id, enable_pixel (checkbox) |
| `POST /dashboard/config/google-tag` | `config.google-tag.update` | Update Google Tag Manager | google_tag_id, enable_gtag (checkbox) |
| `POST /dashboard/config/sms` | `config.sms.update` | Update SMS Settings | sms_provider (twilio/nexmo), api_key, api_secret, sender_id, enable_sms (checkbox) |
| `POST /dashboard/config/fraud` | `config.fraud.update` | Update Fraud Detection | enable_fraud_detection (checkbox), high_risk_threshold, block_vpn (checkbox), max_order_value |
| `POST /dashboard/config/payment-gateway` | `config.payment-gateway.update` | Update Payment Gateway | provider (stripe/paypal/sslcommerz), api_key, api_secret, mode (test/live), enable_gateway (checkbox) |

## Shipping Charges

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `POST /dashboard/config/shipping-charges` | `config.shipping-charges.store` | Create Shipping Charge | name, type (flat/weight_based/location_based), amount, min_weight, max_weight, location, is_active (checkbox) |
| `PUT /dashboard/config/shipping-charges/{id}` | `config.shipping-charges.update` | Update Shipping Charge | name, amount, min_weight, max_weight, location, is_active |
| `DELETE /dashboard/config/shipping-charges/{id}` | `config.shipping-charges.destroy` | Delete Shipping Charge | - |

## Banner Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /dashboard/config/settings/banners` | `config.settings.banners.index` | Hero Banners List | - |
| `POST /dashboard/config/settings/banners` | `config.settings.banners.store` | Create Banner | title, subtitle, image (via Media Library), link_url, link_text, position, is_active (checkbox) |
| `POST /dashboard/config/settings/banners/{id}` | `config.settings.banners.update` | Update Banner | title, subtitle, image_media_id, link_url, link_text, position, is_active |
| `DELETE /dashboard/config/settings/banners/{id}` | `config.settings.banners.destroy` | Delete Banner | - |
| `POST /dashboard/config/settings/banners/reorder` | `config.settings.banners.reorder` | Reorder Banners | banner_order (array of ids) |

## Expense Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /expense-categories` | `expense-categories.index` | Expense Categories List | - |
| `POST /expense-categories` | `expense-categories.store` | Create Expense Category | name, description |
| `PUT /expense-categories/{expense_category}` | `expense-categories.update` | Update Expense Category | name, description |
| `DELETE /expense-categories/{expense_category}` | `expense-categories.destroy` | Delete Expense Category | - |
| `GET /expenses` | `expenses.index` | Expenses List | - |
| `POST /expenses` | `expenses.store` | Create Expense | expense_category_id, amount, date, description, receipt (file upload) |
| `PUT /expenses/{expense}` | `expenses.update` | Update Expense | expense_category_id, amount, date, description, receipt |
| `DELETE /expenses/{expense}` | `expenses.destroy` | Delete Expense | - |
| `GET /expenses/report` | `expenses.report` | Expenses Report | date_from, date_to, category_id |

## Landing Page Management

| Route Path | Route Name | Human Readable Name | Form Fields (Create/Edit) |
|------------|-----------|---------------------|---------------------------|
| `GET /limited-offer/admin/cloth-template` | `landingPage.cloth` | Cloth Template Admin | - |
| `POST /limited-offer/admin/cloth-create` | `landingPage.clothStore` | Create Cloth Landing Page | title, subtitle, product_id, original_price, sale_price, countdown_end, hero_image, gallery_images (multiple), features (array), testimonials (array) |
| `GET /limited-offer/admin/{id}/cloth-edit` | `landingPage.clothEdit` | Edit Cloth Landing Page | (Same as create) |
| ` POST /limited-offer/admin/{id}/cloth-update` | `landingPage.clothUpdate` | Update Cloth Landing Page | (Same as create) |
| `GET /limited-offer/admin/fruit-template` | `landingPage.fruit` | Fruit Template Admin | - |
| `POST /limited-offer/admin/fruit-create` | `landingPage.fruitStore` | Create Fruit Landing Page | title, subtitle, product_id, price, hero_image, benefits (array), cta_text |
| `GET /limited-offer/admin/{id}/fruit-edit` | `landingPage.fruitEdit` | Edit Fruit Landing Page | (Same as create) |
| `POST /limited-offer/admin/{id}/fruit-update` | `landingPage.fruitUpdate` | Update Fruit Landing Page | (Same as create) |

## Public Routes (Frontend)

| Route Path | Route Name | Human Readable Name | Form Fields |
|------------|-----------|---------------------|-------------|
| `GET /` | `root` | Homepage | - |
| `GET /search` | `search` | Product Search Page | q (search query), category, min_price, max_price, sort |
| `GET /product/{slug}` | `product_detail` | Product Detail Page | - |
| `POST /product/{product:slug}/reviews` | `product.reviews.store` | Submit Product Review | rating (1-5), title, body |

## Authentication Routes

| Route Path | Route Name | Human Readable Name | Form Fields |
|------------|-----------|---------------------|-------------|
| `GET /login` | `login` | Login Page | email, password, remember (checkbox) |
| `GET /register` | `register` | Registration Page | name, email, password, password_confirmation, terms (checkbox) |
| `GET /forgot-password` | `password.request` | Forgot Password Page | email |
| `GET /reset-password/{token}` | `password.reset` | Reset Password Page | email, password, password_confirmation, token |

## Cart & Checkout Routes

| Route Path | Route Name | Human Readable Name | Form Fields |
|------------|-----------|---------------------|-------------|
| `GET /cart` | `cart.index` | Shopping Cart Page | - |
| `POST /cart/add` | `cart.add` | Add Item to Cart | product_id, variant_sku, quantity |
| `PATCH /cart/item/{item}` | `cart.item.update` | Update Cart Item Quantity | quantity |
| `DELETE /cart/item/{item}` | `cart.item.remove` | Remove Item from Cart | - |
| `POST /api/cart/coupon/apply` | - | Apply Coupon Code | coupon_code |
| `POST /api/cart/shipping` | - | Update Shipping Method | shipping_method_id |
| `GET /checkout` | `checkout.index` | Checkout Page | - |
| `POST /checkout/place` | `checkout.place` | Place Order | billing_name, billing_email, billing_phone, billing_address, billing_city, billing_postal_code, shipping_name, shipping_email, shipping_phone, shipping_address, shipping_city, shipping_postal_code, payment_method, customer_notes, same_as_billing (checkbox) |

## Media Library

| Route Path | Route Name | Human Readable Name | Form Fields |
|------------|-----------|---------------------|-------------|
| `GET /media` | `media.index` | Media Library | - |
| `POST /media` | `media.store` | Upload Media | file (image upload), alt_text, title |
| `DELETE /media/{medium}` | `media.destroy` | Delete Media | - |

## Report Routes

| Route Path | Route Name | Human Readable Name | Filters Available |
|------------|-----------|---------------------|-------------------|
| `GET /dashboard/report/overview` | `report.overview` | Reports Overview | date_from, date_to |
| `GET /dashboard/report/sales` | `report.sales` | Sales Report | date_from, date_to, group_by (day/week/month) |
| `GET /dashboard/report/order-static` | `report.orderStatic` | Order Statistics | date_from, date_to, status |
| `GET /dashboard/report/transactions` | `report.transactions` | Transactions Report | date_from, date_to, payment_status |
| `GET /dashboard/report/sales-history` | `report.salesHistory` | Sales History Report | date_from, date_to, product_id |
| `GET /dashboard/report/staff-performance` | `report.staffPerformance` | Staff Performance Report | date_from, date_to, staff_id |

## Other Routes (No Forms)

### Stock Management
- `GET /dashboard/stock` - Stock Management
- `GET /dashboard/stock/setup-uptovalue` - Setup Stock Alert Values

### Point of Sale
- `GET /dashboard/pos` - Point of Sale System
- `POST /dashboard/pos/checkout` - POS Checkout

### Courier Integration
- `GET /dashboard/pathao` - Pathao Integration
- `GET /dashboard/steadfast` - Steadfast Integration

### Locations API
- `GET /dashboard/locations/pathao/cities` - Get Pathao Cities
- `GET /dashboard/locations/pathao/zones/{city}` - Get Pathao Zones
- `GET /dashboard/locations/pathao/areas/{zone}` - Get Pathao Areas
- `GET /dashboard/locations/redx/areas` - Get RedX Areas

### Wishlist
- `POST /wishlist/toggle` - Add/Remove from Wishlist (product_id)

### Tools
- `POST /tools/maintenance/toggle` - Toggle Maintenance Mode
- `GET /tools/server-stats` - Server Statistics
- `POST /cache/clear` - Clear Application Cache

### Menu Builder
- `GET /dashboard/menu-builder` - Menu Builder
- `POST /dashboard/menu-builder` - Update Menu (menu_items: array of {label, url, order, parent_id})

### Contact & IP Management
- `GET /dashboard/contact` - Contact Messages
- `POST /dashboard/contact/contact` - Save Contact Form (name, email, subject, message)
- `GET /dashboard/ip` - IP Management

### Notifications
- `GET /dashboard/notifications` - Notifications List
- `POST /dashboard/notifications/read-all` - Mark All Notifications Read
- `GET /notification/user` - User Notifications
- `GET /notification/front` - Frontend Notifications

### Activity Log
- `GET /dashboard/activity` - Activity Log

### Fraud Check
- `GET /fraud-check` - Fraud Check (order_id, ip_address, email)

### Customer Management (Admin)
- `GET /customers` - Customers Management
- `GET /customers-list` - Customers List (JSON with filters: search, status, date_from, date_to)
- `GET /customers/{customer}/history` - Customer Order History
- `POST /customers/{customer}/toggle-status` - Enable/Disable Customer

---

**Total Routes:** 244+

**Form Field Types Used:**
- Text Input (name, email, etc.)
- Text Area (description, notes, etc.)
- Number Input (price, quantity, etc.)
- Select Dropdown (status, type, category, etc.)
- Multiselect (attributes, products, categories, etc.)
- Checkbox (is_active, remember, etc.)
- Radio Buttons (payment method, shipping, etc.)
- File Upload (images, documents, etc.)
- Date/DateTime Picker (start_at, end_at, etc.)
- Rich Text Editor (Quill for descriptions)
- Media Library Picker (images)
- Search with Autocomplete (products, categories)

**Last Updated:** February 9, 2026
