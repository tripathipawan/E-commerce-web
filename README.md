# E-Commerce Web

A fully multi-page e-commerce website built with HTML, CSS, and JavaScript — spanning 7 interconnected pages: Home, Shop, Single Product, Cart, Blog, About, and Contact. All pages share a single `Style.css` and `Script.js`, use a sticky responsive navbar with a hamburger menu slide-in on mobile, and are styled with the `Spartan` Google Font and Font Awesome 6.7.2 icons. No framework, no backend — a complete front-end e-commerce UI template.

---

## Pages

### 1. Home — `Index.html`

The main landing page. Contains 8 sections stacked vertically:

**Header (sticky navbar):**
The `#header` is `position: sticky; top: 0; z-index: 999` — it stays fixed at the top as the user scrolls. Contains the logo image (`logo.png`), 5 navigation links (Home, Shop, Blog, About, Contact), a shopping bag icon linking to `cart.html`, a hamburger icon (`fa-solid fa-outdent`) for mobile, and a close icon (`fa-solid fa-times`) inside the nav for mobile close. The active page link has `class="active"` applied, which colors it `#088178` (teal) and adds a `2px` underline via `::after`.

**Hero section (`#hero`):**
Full-width `90vh` hero with `background-image: url(Assets/hero4.png)` at `background-position: top 25% right 0`. Text content positioned left: `h4` subheading ("Trade-in-offer"), `h2` ("Super value"), `h1` in teal ("On all products"), a paragraph, and a "Shop Now" button. The button uses `background-image: url(Assets/button.png)` — a custom button PNG image — with transparent fill and teal text.

**Feature strip (`#feature`):**
6 feature boxes in a flex row — Free Shipping, Online Order, Save Money, Promotions, Happy Sell, F24/7 Support — each with a `.fe-box` card (PNG icon + `<h6>` label). Each box has `box-shadow: 20px 20px 34px rgba(0,0,0,0.03)` with a hover shadow upgrade. Each `<h6>` label has a unique background color set by `:nth-child()` selectors:

| Box | Label | Background |
|---|---|---|
| 1st | Free Shipping | `#fddde4` (pink) |
| 2nd | Online Order | `#cdebbc` (green) |
| 3rd | Save Money | `#d1e8f2` (blue) |
| 4th | Promotions | `#cdd4f8` (purple) |
| 5th | Happy Sell | `#f6dbf6` (lavender) |
| 6th | F24/7 Support | `#fff2e5` (peach) |

**Featured Products (`#product1`):**
8 product cards in a flex-wrap grid. Each `.pro` card is `width: 23%; min-width: 250px; border-radius: 25px` with a `0.3s ease` hover shadow deepening. Each card contains: a product image, a `.des` div with brand `<span>` ("Adidas"), product `<h5>` name, 5 gold `fa-star` icons, a teal `<h4>` price ("$78"), and a circular cart icon (`#cart`) absolutely positioned at `bottom: 20px; right: 10px` with a `#e8f6ea` (light green) background. The first product card has `onclick="window.location.href='sproduct.html'"` — clicking it navigates to the Single Product page.

**Promo banner (`#banner`):**
`40vh` full-width banner with `background-image: url(Assets/b2.jpg)`. White text heading "Up to **70% Off** - All t-Shirts & Accessories" (the "70% Off" span is red `#ef3636`). "Explore More" button turns teal on hover.

**New Arrivals (`#product1`, second instance):**
8 more product cards using the identical `.pro` card structure but with `n1.jpg`–`n8.jpg` images and different product name variants (Shirts, Pants).

**Small dual-banner (`#sm-banner`):**
2 side-by-side banners, each `min-width: 47%; height: 50vh`. Left uses `b17.jpg`, right uses `b10.jpg`. Each has an "h4 + h2 + span + white button" layout. On hover, the button fills teal (`#088178`).

**Triple banner strip (`#banner3`):**
3 side-by-side banners, each `min-width: 30%; height: 30vh`. Uses `b7.jpg`, `b4.jpg`, and `b18.jpg`. Each shows "SEASONAL SALE" in white and "Winter Collection -50% OFF" in red `#ec544e`.

**Newsletter (`#newsletter`):**
Dark navy `#041e42` background with a decorative `b14.png` image positioned at `20% 30%`. Left side: heading + description with a gold `#ffbd27` "special offers" span. Right side: an email input (left-radius `0` on right side) paired flush with a teal "Sign Up" button (right-radius `0` on left side), forming a single connected input-button unit.

**Footer:**
4-column flex layout: Contact info column (logo, address, phone, hours, social icons), About links column, My Account links column, Install App column (App Store/Play Store images + payment gateway image). `© 2025, Pawan Tripathi` copyright at the bottom. Social icons (`facebook`, `twitter`, `instagram`, `pinterest`, `youtube`) turn teal on hover.

---

### 2. Shop — `Shop.html`

Shares the same sticky header. Contains a `#page-header` banner with `b1.jpg` background showing "#Stayhome" heading. Below that, the same `#product1` grid of product cards — all with the same `.pro` card structure. The first card here also links to `sproduct.html` via `onclick`. A `#pagination` section at the bottom provides navigation links styled as teal pill buttons.

---

### 3. Single Product — `sproduct.html`

The product detail page, linked from the first product card on both Home and Shop pages.

**Left side (`.single-pro-image`, `width: 40%`):**
A large main product image (`id="MainImg"`) displaying `f1.jpg` by default. Below it, a `.small-img-group` flex row of 4 thumbnail images (`.small-img` class) — `f1.jpg`, `f2.jpg`, `f3.jpg`, `f4.jpg`. Clicking any thumbnail swaps the main image:

```js
smallImg[0].onclick = function () { MainImg.src = smallImg[0].src; }
smallImg[1].onclick = function () { MainImg.src = smallImg[1].src; }
smallImg[2].onclick = function () { MainImg.src = smallImg[2].src; }
smallImg[3].onclick = function () { MainImg.src = smallImg[3].src; }
```

Each `smallImg[i].src` holds the thumbnail's own source — clicking it copies that source into `MainImg.src`, updating the main display image.

**Right side (`.single-pro-details`, `width: 50%`):**
Breadcrumb (`h6`: "Home / T-Shirt"), product title (`h4`: "Men's Fashion T-Shirt"), price (`h2`: "$139.00"), a size `<select>` dropdown (Select Size, XL, XXL, Small, Large), a quantity `<input type="number" value="1">`, an "Add To Cart" button (teal background), a "Product Details" `<h4>`, and a long `<span>` description paragraph about the fabric.

Below the product detail, a second `#product1` section shows related Featured Products cards.

---

### 4. Cart — `Cart.html`

**Cart table (`#cart`):**
A `<table>` with `border-collapse: collapse; table-layout: fixed; white-space: nowrap; overflow-x: auto`. 6 columns: Remove (`fa-times-circle` icon), Image (70px product thumbnail), Product name, Price, Quantity (`<input type="number">`), Subtotal. 2 pre-filled rows of items are shown as static HTML.

**Cart actions (`#cart-add`):**
Side-by-side flex layout of 2 panels:
- `#coupon` (50% width) — coupon code input + "Apply Coupon" button
- `#subtotal` (50% width, bordered) — a summary table with Subtotal, Shipping, Total rows, and a "Proceed to Checkout" button

---

### 5. Blog — `Blog.html`

`#page-header` with `b19.jpg` background. The `#blog` section uses `padding: 150px 150px 0 150px` (heavy padding). Each `.blog-box` is a flex row with `.blog-img` (50% width, fixed `height: 300px` images with `object-fit: cover`) and `.blog-details` (50%). A large decorative number `<h1>` is positioned absolutely at `top: -40px; left: 0; font-size: 70px; color: #c9cbce; z-index: -9` — a background watermark number. Blog links have a `::after` pseudo-element that adds a `50px` horizontal line to the right of the link text.

---

### 6. About — `About.html`

`#page-header` with `banner.png` background. `#about-head` is a flex row — left side is a 50%-wide image, right side is a text block with `padding-left: 40px`. `#about-app` contains a centered video section — a `<video>` element in a `width: 70%` container with `border-radius: 20px`, playing `1.mp4` from the local assets.

---

### 7. Contact — `Contact.html`

`#contact-details` is a flex row — left `.details` panel (40%) shows contact address, phone, and hours in a list with Font Awesome icons; right `.map` panel (55%) embeds a `400px` tall `<iframe>` Google Map. `#form-details` below has a contact `<form>` (name, email, phone, message textarea, Send button) on the left and a `.people` testimonials panel on the right with circular staff photos.

---

## JavaScript — `Script.js`

The script handles 2 features that apply across all pages:

**1. Mobile hamburger nav — used on all pages:**
```js
let bar   = document.getElementById("bar");
let nav   = document.getElementById("navbar");
let close = document.getElementById("close");

if (bar) {
  bar.addEventListener('click', () => { nav.classList.add('active'); })
}
if (close) {
  close.addEventListener('click', () => { nav.classList.remove('active'); })
}
```
Both selectors are wrapped in `if` guards — if `bar` or `close` are null (elements not present on a page), the listener is skipped without throwing an error. `classList.add('active')` slides the navbar into view from the right; `classList.remove('active')` slides it back out. The CSS defines the mobile nav as `position: fixed; right: -300px; width: 300px` with `transition: 0.3s`, and `.active` sets `right: 0px`.

**2. Product image gallery — only active on `sproduct.html`:**
```js
let MainImg  = document.getElementById("MainImg");
let smallImg = document.getElementsByClassName("small-img");

smallImg[0].onclick = function () { MainImg.src = smallImg[0].src; }
smallImg[1].onclick = function () { MainImg.src = smallImg[1].src; }
smallImg[2].onclick = function () { MainImg.src = smallImg[2].src; }
smallImg[3].onclick = function () { MainImg.src = smallImg[3].src; }
```
`smallImg` is an `HTMLCollection` of all elements with `class="small-img"`. On pages where no `.small-img` elements exist, `smallImg[0]` is `undefined` — and `undefined.onclick` would throw a runtime error. This is not guarded with an `if` check (unlike the navbar), which means the script throws on every page except `sproduct.html`. The navbar still works despite this error because the hamburger listeners are registered before the `smallImg` assignments.

---

## Responsive Design

`Style.css` has 3 media query breakpoints:

**`max-width: 799px`:**
- `#navbar` transforms into a slide-in panel: `position: fixed; right: -300px; width: 300px; height: 100vh; flex-direction: column; transition: 0.3s`. Activated by adding `.active` class via JS
- `#mobile` (hamburger + cart icon) becomes visible (`display: flex`)
- `#close` (× icon inside nav) becomes visible (`display: initial; position: absolute; top: 30px; left: 30px`)
- `#lg-bag` (cart icon in the desktop nav) is hidden (`display: none`)
- Hero height drops to `70vh`
- Small banner boxes go full-width (`min-width: 100%`)
- Single product (`#prodetails`) switches from `flex row` to `flex column`
- Blog, About, Contact sections adjust padding and layout

**`max-width: 477px`:**
- Section padding reduces to `20px`
- `h1` reduces from `50px` to `38px`, `h2` from `46px` to `32px`
- Product cards go full width (`#product1 .pro { width: 100% }`)
- Triple banner boxes go full-width and stack vertically
- Newsletter form takes full width
- Blog boxes switch from `flex row` to `flex column`
- About head stacks vertically
- Contact details stack vertically
- Cart add section stacks vertically, coupon and subtotal go full-width

**`max-width: 350px`:**
- Feature boxes center-justify

---

## Tech Stack

| Technology | Role |
|---|---|
| HTML5 | 7 separate pages — full semantic structure for each section |
| CSS3 | Single shared stylesheet — sticky header, product card grid, all section layouts, 3 responsive breakpoints |
| JavaScript (Vanilla) | Mobile nav slide-in toggle, thumbnail-to-main image swap on Single Product page |
| Google Fonts (CDN) | `Spartan` font family — all weights 100–900 |
| Font Awesome 6.7.2 (CDN) | Nav icons, star ratings, cart icon, social media icons, contact list icons |

---

## Project Structure

```
E-commerce-web/
├── Index.html          # Home — hero, features, products, banners, newsletter, footer
├── Shop.html           # Shop — page banner, product grid, pagination
├── sproduct.html       # Single Product — image gallery (4 thumbnails), size/qty selectors, description
├── Cart.html           # Cart — table with 2 items, coupon input, subtotal panel
├── Blog.html           # Blog — numbered posts with image + details layout
├── About.html          # About — image + text split, embedded video (1.mp4)
├── Contact.html        # Contact — address panel, Google Maps iframe, contact form
├── Style.css           # Shared stylesheet for all 7 pages — 3 breakpoints
├── Script.js           # Mobile nav toggle + product image gallery swap
├── logo.png            # Site logo used in header and footer across all pages
├── hero4.png           # Hero section background image
├── button.png          # Custom "Shop Now" button background image
├── 1.mp4               # About page embedded video
├── pay.png             # Payment gateway logos image (footer)
├── app.jpg, play.jpg   # App Store and Google Play badge images (footer)
├── banner.png          # About page header background
├── f1.jpg–f8.jpg       # Featured Products images
├── n1.jpg–n8.jpg       # New Arrivals images
├── b1–b20.jpg          # Banner section background images
├── a1–a6.png/jpg       # Contact page people/staff images
└── f1.png–f6.png       # Feature strip icons (Free Shipping, Online Order, etc.)
```

---

## How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/tripathipawan/E-commerce-web.git
   ```
2. Open `Index.html` directly in any modern browser — all assets are local. Navigate between pages using the navbar links. No server, no build step, no internet connection required (Font Awesome and Google Fonts load from CDN).

---

## Repository

[https://github.com/tripathipawan/E-commerce-web](https://github.com/tripathipawan/E-commerce-web)
