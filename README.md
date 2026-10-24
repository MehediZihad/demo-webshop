# Demo Web Shop — Everyday, elevated

A complete responsive **frontend demo** built with HTML, CSS, and vanilla JavaScript. Inspired by the category and customer-page structure of https://demowebshop.tricentis.com, with an original modern design, sample catalog, and original local SVG illustrations. This is an independent project, not an exact catalog/content copy or an official Tricentis product.

## Run it

Open `dist/index.html` directly in a modern browser. No build or installation is needed. For reliable local storage, use a local HTTP server:

```sh
cd dist
python3 -m http.server 8080
```

Visit `http://localhost:8080`. You can also use VS Code Live Server. Upload the contents of `dist/` to any static host, including GitHub Pages. Navigation uses `#/` routes so refreshes work without server rewrite rules.

## Source files

- `dist/index.html` — accessible application shell, metadata, stylesheet and script loading.
- `dist/css/styles.css` — full responsive design, desktop/mobile layouts, focus states and reduced-motion support.
- `dist/js/data.js` — editable product catalog, categories, descriptions, prices and image paths.
- `dist/js/app.js` — page templates, hash router, shopping state, forms and interactions.
- `dist/assets/*.svg` — all original product illustrations and favicon; no external image dependencies.
- `tests/smoke.cjs` — dependency-free renderer and checkout integration checks.

## Implemented pages

All screens share the same HTML shell; each has its own JavaScript page template and navigable URL. This avoids duplicated headers and footers while retaining separate page behavior.

| Page | Route after index.html |
| --- | --- |
| Home | `#/` |
| All products | `#/shop` |
| Books | `#/category/books` |
| Computers | `#/category/computers` |
| Desktops | `#/category/desktops` |
| Notebooks | `#/category/notebooks` |
| Accessories and TCP training | `#/category/accessories` |
| Electronics | `#/category/electronics` |
| Camera & photo | `#/category/camera-photo` |
| Cell phones | `#/category/cell-phones` |
| Apparel & shoes | `#/category/apparel-shoes` |
| Digital downloads | `#/category/digital-downloads` |
| Jewelry | `#/category/jewelry` |
| Gift cards | `#/category/gift-cards` |
| Individual product | `#/product/studio-headphones` (and every catalog ID) |
| Search | `#/search?q=camera` |
| Sale | `#/sale` |
| New arrivals | `#/newproducts` |
| Recently viewed | `#/recentlyviewedproducts` |
| Wishlist | `#/wishlist` |
| Product comparison | `#/compareproducts` |
| Shopping cart | `#/cart` |
| Three-stage checkout | `#/checkout` |
| Order confirmation/details | `#/order/ORDER-ID` (generated after checkout) |
| Register | `#/register` |
| Sign in | `#/login` |
| Password help | `#/passwordrecovery` |
| Profile | `#/customer/info` |
| Order history | `#/customer/orders` |
| Saved addresses | `#/customer/addresses` |
| Contact | `#/contactus` |
| About | `#/about-us` |
| Shipping & returns | `#/shipping-returns` |
| Privacy | `#/privacy-policy` |
| Conditions | `#/conditions-of-use` |
| Sitemap | `#/sitemap` |
| News and individual stories | `#/news`, `#/news/thoughtful-everyday` |
| Blog and individual articles | `#/blog`, `#/blog/thoughtful-everyday` |
| Not-found state | Any unknown route |

## Working interactions

- Search by name, category or color; six sorting choices; price and rating filters; sale filter; pagination; grid/list views.
- Product details, descriptions, specifications, locally saved reviews, quantity, color, apparel/shoe sizes, and gift recipient details.
- Persistent cart with separate variants, quantity updates, item removal and a 25-item limit per variant.
- Wishlist, add-all-to-cart, comparison of up to four products, and recently viewed history.
- Coupon `WELCOME10`: 10% off products. Standard shipping: $6.95 under $75, otherwise free. Express: $15. Digital-only/training carts have no shipping charge. Tax is explicitly simulated as $0.
- Checkout: fictional address → delivery choice → review and place demo order. Order totals and item variants are saved at purchase time; reorder adds items back to the bag.
- Demo registration, sign-in, session reset, editable profile and saved addresses.
- Validated contact and newsletter forms that save locally and explicitly do not send messages.
- Responsive layouts, keyboard focus styles, labeled forms, skip link, alt text and live toast announcements.

## Important demo boundaries

There is **no backend, secure authentication, actual payment, real email delivery, inventory synchronization, downloadable paid content, or actual shipping**. Passwords are never saved or verified. Demo sign-in matches the locally saved email and accepts any sample password of six or more characters. Password help resets the local demo session. Use fictional data.

State is in browser localStorage under `dws-*` keys. Anyone using that browser can read/modify it. Clear the site's browser data to reset the demo. Hosting may have ordinary access logs; the app includes no analytics or third-party scripts/images/fonts. A public production store requires secure server-side authentication, authorization, product/order databases, payment-provider integration, server-side validation, taxes, email, inventory and security review.

## Customize

1. Edit products/categories in `dist/js/data.js`.
2. Adjust CSS variables at the top of `dist/css/styles.css` for colors and typography.
3. Edit page templates in `dist/js/app.js` for content and layout.
4. Replace local SVG image paths with your own assets as needed.
5. Update brand text and metadata in the header/footer renderers and `index.html`.

## Verification

```sh
node --check dist/js/data.js
node --check dist/js/app.js
node tests/smoke.cjs
```

The smoke suite checks 77 routes, generated asset paths, cart variants, quantity limits, coupons, shipping totals, HTML escaping, product tabs, checkout order creation and local persistence. It uses a small mocked DOM; browser visual and interaction checks complement it.
# demo-webshop
