# WhatsApp Link Preview Implementation Guide

This project demonstrates how to create rich link previews for WhatsApp (and other social media platforms) using Open Graph meta tags. When you share a URL on WhatsApp, it displays a preview card with an image, title, description, and deep linking support.

## 📋 Table of Contents

- [What We've Done](#what-weve-done)
- [Open Graph Tags for WhatsApp](#open-graph-tags-for-whatsapp)
- [Implementation Steps](#implementation-steps)
- [Example URLs](#example-urls)
- [Troubleshooting](#troubleshooting)

## 🎯 What We've Done

1. **Created HTML pages with Open Graph meta tags** - Each page includes all necessary meta tags for WhatsApp to generate rich previews
2. **Fixed image paths** - Used absolute URLs instead of relative paths to ensure images load correctly on GitHub Pages
3. **Added deep linking support** - Implemented App Links (Android) and Universal Links (iOS) for seamless app opening
4. **Optimized for WhatsApp** - Included all required and recommended meta tags for best preview experience

## 🏷️ Open Graph Tags for WhatsApp

WhatsApp uses **Open Graph (OG)** meta tags to generate link previews. Here are the essential tags:

### Required Tags

```html
<!-- Basic Open Graph Tags -->
<meta property="og:type" content="website" />
<meta property="og:title" content="Your Page Title" />
<meta property="og:description" content="Brief description of your content" />
<meta property="og:url" content="https://yourdomain.com/page.html" />
<meta property="og:image" content="https://yourdomain.com/image.jpg" />
```

### Recommended Tags for Better Previews

```html
<!-- Site Information -->
<meta property="og:site_name" content="Your Site Name" />

<!-- Image Details (Important for WhatsApp) -->
<meta property="og:image:type" content="image/jpeg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Description of the image" />
```

### Deep Linking Tags (App Links)

```html
<!-- Android Deep Linking -->
<meta property="al:android:url" content="yourapp://path/to/content" />
<meta property="al:android:package" content="com.yourcompany.yourapp" />
<meta property="al:android:app_name" content="Your App Name" />

<!-- iOS Deep Linking -->
<meta property="al:ios:url" content="yourapp://path/to/content" />
<meta property="al:ios:app_store_id" content="123456789" />
<meta property="al:ios:app_name" content="Your App Name" />
```

### Complete Example

Here's a complete example from `repo/123.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>Task #123 Completed</title>

    <!-- REQUIRED FOR WHATSAPP PREVIEW -->
    <meta property="og:type" content="website" />
    <meta property="og:title" content="Task #123 Completed" />
    <meta property="og:description" content="Tap to view task details in the app." />
    <meta property="og:site_name" content="Link Preview Test" />

    <!-- WHATSAPP PREVIEW IMAGE -->
    <meta property="og:image"
          content="https://akshitwiom.github.io/link-preview-test/assets/previews/task_123.jpg" />
    <meta property="og:image:type" content="image/jpeg" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />
    <meta property="og:image:alt" content="Task 123 Preview Image" />

    <!-- CANONICAL URL -->
    <meta property="og:url"
          content="https://akshitwiom.github.io/link-preview-test/repo/123.html" />

    <!-- ANDROID DEEP LINK -->
    <meta property="al:android:url" content="yourapp://task/123" />
    <meta property="al:android:package" content="com.example.yourapp" />

    <!-- IOS DEEP LINK -->
    <meta property="al:ios:url" content="yourapp://task/123" />
    <meta property="al:ios:app_name" content="Your App" />
    <meta property="al:ios:app_store_id" content="123456789" />

    <meta name="viewport" content="width=device-width, initial-scale=1" />
</head>
<body>
    <!-- Your page content -->
</body>
</html>
```

## 🚀 Implementation Steps

### Step 1: Prepare Your Images

1. **Create preview images** for each piece of content you want to share
2. **Recommended image specifications:**
   - **Size**: 1200 x 630 pixels (1.91:1 aspect ratio)
   - **Format**: JPEG or PNG
   - **File size**: Under 8MB (WhatsApp limit)
   - **Minimum size**: 200 x 200 pixels

3. **Host images** on your server with public HTTPS access

### Step 2: Create HTML Pages

For each shareable URL, create an HTML page with:

1. **Basic HTML structure** with proper DOCTYPE
2. **All required Open Graph meta tags** in the `<head>` section
3. **Use absolute URLs** for images (not relative paths)
4. **Match og:url** to the actual page URL

### Step 3: Configure Deep Linking (Optional)

If you want links to open your app:

1. **Update App Links meta tags** with your actual app package name and scheme
2. **Configure your app** to handle the deep link URLs
3. **Test deep linking** on both Android and iOS devices

### Step 4: Deploy to Your Server

1. **Upload HTML files** to your web server
2. **Ensure HTTPS** is enabled (required for WhatsApp)
3. **Verify images are accessible** via direct URL
4. **Test the URLs** in a browser first

### Step 5: Test and Debug

1. **Use Facebook Sharing Debugger** to test your preview:
   - Visit: https://developers.facebook.com/tools/debug/
   - Enter your URL and click "Scrape Again"
   - This clears WhatsApp's cache and shows how the preview will look

2. **Test on WhatsApp**:
   - Share the URL in a WhatsApp chat
   - Wait a few seconds for the preview to load
   - If preview doesn't appear, use the debugger to refresh cache

### Step 6: Implement on Your App's Website

To implement this on your app's deep linking website:

1. **Create a template** HTML file with all the meta tags
2. **Dynamically generate pages** for each shareable item (task, post, etc.)
3. **Use server-side rendering** or static site generation to populate:
   - `og:title` - Dynamic title based on content
   - `og:description` - Dynamic description
   - `og:image` - Path to the specific preview image
   - `og:url` - Current page URL
   - Deep link URLs with actual content IDs

4. **Example dynamic implementation** (pseudo-code):
   ```html
   <meta property="og:title" content="{{task.title}}" />
   <meta property="og:description" content="{{task.description}}" />
   <meta property="og:image" content="https://yourdomain.com/previews/{{task.id}}.jpg" />
   <meta property="og:url" content="https://yourdomain.com/task/{{task.id}}" />
   <meta property="al:android:url" content="yourapp://task/{{task.id}}" />
   <meta property="al:ios:url" content="yourapp://task/{{task.id}}" />
   ```

## 📱 Example URLs

### Live Example

**Task Preview Page:**
```
https://akshitwiom.github.io/link-preview-test/repo/123.html
```

**Preview Image:**
```
https://akshitwiom.github.io/link-preview-test/assets/previews/task_123.jpg
```

### URL Structure for Your App

When implementing on your own website, use this structure:

```
https://yourdomain.com/task/{task_id}.html
https://yourdomain.com/post/{post_id}.html
https://yourdomain.com/item/{item_id}.html
```

**Example:**
```
https://myapp.com/task/456.html
https://myapp.com/post/789.html
```

## 🔧 Troubleshooting

### Preview Not Showing in WhatsApp

1. **Check image accessibility:**
   - Open the image URL directly in a browser
   - Ensure it's served over HTTPS
   - Verify the image exists and loads correctly

2. **Clear WhatsApp cache:**
   - Use Facebook Sharing Debugger: https://developers.facebook.com/tools/debug/
   - Enter your URL and click "Scrape Again"
   - This forces WhatsApp to re-fetch the preview

3. **Verify meta tags:**
   - View page source and check all `og:` tags are present
   - Ensure `og:url` matches the actual page URL
   - Verify `og:image` uses absolute HTTPS URL

4. **Check image requirements:**
   - Image must be at least 200x200 pixels
   - Recommended: 1200x630 pixels
   - File size under 8MB
   - Accessible without authentication

### Common Issues

**Issue: 404 Error when accessing URL**
- **Solution**: Ensure the file path matches the `og:url` exactly
- Check GitHub Pages configuration if using GitHub Pages

**Issue: Image not loading**
- **Solution**: Use absolute URLs (full HTTPS URL) instead of relative paths
- Verify image is publicly accessible

**Issue: Preview shows old content**
- **Solution**: Use Facebook Sharing Debugger to clear cache
- Add a query parameter like `?v=2` to force refresh

**Issue: Deep link not working**
- **Solution**: Verify app package name and URL scheme are correct
- Test deep links directly in the app first
- Ensure app is configured to handle the URL scheme

## 📚 Additional Resources

- [Open Graph Protocol Documentation](https://ogp.me/)
- [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)
- [WhatsApp Sharing Guidelines](https://developers.facebook.com/docs/sharing/webmasters)
- [App Links Documentation](https://developers.facebook.com/docs/applinks)

## ✅ Checklist for Implementation

- [ ] Images are 1200x630 pixels (or at least 200x200)
- [ ] Images are hosted on HTTPS
- [ ] All required `og:` meta tags are present
- [ ] `og:url` matches the actual page URL
- [ ] `og:image` uses absolute HTTPS URL
- [ ] Deep link URLs are configured correctly
- [ ] Tested with Facebook Sharing Debugger
- [ ] Preview works in WhatsApp

---

**Note**: WhatsApp caches previews aggressively. If you make changes, use the Facebook Sharing Debugger to clear the cache before testing again.
