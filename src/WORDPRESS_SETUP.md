# 📝 WordPress Configuration for The Igniting Studio

## **Current Integration: Headless WordPress on VPS**

Your React application integrates with **WordPress as a headless CMS** running on the same VPS.

---

## 🏗️ **WordPress Directory Structure**

```
/var/www/igniting-studio/dist/
├── index.html                 # React application entry point
├── assets/                    # React build assets
├── wp/                        # WordPress installation
│   ├── wp-admin/             # WordPress admin interface  
│   ├── wp-content/           # Themes, plugins, uploads
│   ├── wp-includes/          # WordPress core files
│   └── wp-config.php         # WordPress configuration
└── .htaccess                 # Server configuration
```

---

## 🔗 **API Endpoints Available**

### **WordPress REST API Base:** `https://yourdomain.com/wp-json/wp/v2/`

### **Standard Endpoints:**
- **Posts:** `/wp-json/wp/v2/posts`
- **Pages:** `/wp-json/wp/v2/pages`  
- **Media:** `/wp-json/wp/v2/media`

### **Custom Post Types:**
- **Portfolio:** `/wp-json/wp/v2/portfolio`
- **Services:** `/wp-json/wp/v2/services`
- **Testimonials:** `/wp-json/wp/v2/testimonials`

---

## 🎯 **WordPress Admin Access**

### **Admin URL:** `https://yourdomain.com/wp/wp-admin/`

### **Content Management Areas:**
1. **Posts** - Blog content
2. **Pages** - Static page content
3. **Portfolio** - Portfolio items with custom fields
4. **Services** - Service descriptions and pricing
5. **Testimonials** - Client testimonials with ratings
6. **Media Library** - Images and documents

---

## ⚙️ **Custom Fields Configuration**

### **Portfolio Items:**
- `project_url` - Live project URL
- `technologies` - Technologies used (comma-separated)
- `client_name` - Client name
- `featured_image` - Project screenshot

### **Services:**
- `price_range` - Service pricing
- `duration` - Project duration
- `features` - Service features (array)

### **Testimonials:**
- `client_name` - Client name  
- `client_company` - Client company
- `rating` - Star rating (1-5)

---

## 🔧 **WordPress Configuration**

### **Key wp-config.php Settings:**
```php
// URLs for headless setup
define('WP_HOME', 'https://yourdomain.com');
define('WP_SITEURL', 'https://yourdomain.com/wp');

// CORS for React frontend
define('WP_CORS_ALLOW_ORIGIN', 'https://yourdomain.com');

// Performance optimizations
define('WP_MEMORY_LIMIT', '512M');
define('WP_CACHE', true);
```

---

## 📦 **Required Plugins**

### **Essential Plugins:**
1. **Contact Form 7** - Contact form handling
2. **Polylang** - Multi-language support (EN/HU)
3. **Advanced Custom Fields (ACF)** - Custom field management
4. **WP REST API Cache** - API response caching

### **Installation via WordPress Admin:**
1. Go to `Plugins → Add New`
2. Search for each plugin
3. Install and activate

---

## 🌍 **Multi-Language Setup**

### **Polylang Configuration:**
1. **Languages:** English (default), Hungarian
2. **URL Structure:** 
   - English: `yourdomain.com/page/`
   - Hungarian: `yourdomain.com/hu/page/`

### **Content Translation:**
- Each post/page can have EN and HU versions
- React app automatically fetches correct language content
- Language switching handled by React Router

---

## 🔄 **React ↔ WordPress Integration**

### **Data Flow:**
```
React Components → WordPress API → Database
     ↑                                ↓
User Interface ← JSON Response ← WordPress Content
```

### **WordPress Components in React:**
- `WordPressHero` - Dynamic hero content
- `WordPressBlog` - Blog posts display
- `WordPressPortfolio` - Portfolio items
- `WordPressServices` - Services listing
- `WordPressContact` - Contact form integration

---

## 🚀 **Content Management Workflow**

### **Adding New Content:**
1. **Login** to WordPress admin
2. **Create/Edit** content with custom fields
3. **Publish** content
4. **React app** automatically displays new content (cached for 5 minutes)

### **Updating Existing Content:**
1. **Edit** content in WordPress admin
2. **Update** and publish changes
3. **Cache clears** automatically after 5 minutes
4. **Changes appear** on frontend

---

## 🔍 **Testing WordPress Integration**

### **API Endpoint Tests:**
```bash
# Test posts endpoint
curl https://yourdomain.com/wp-json/wp/v2/posts

# Test portfolio endpoint  
curl https://yourdomain.com/wp-json/wp/v2/portfolio

# Test services endpoint
curl https://yourdomain.com/wp-json/wp/v2/services
```

### **Expected Response:**
- **Status:** 200 OK
- **Content-Type:** application/json
- **CORS Headers:** Present for React app

---

## 📊 **Performance Optimization**

### **Caching Strategy:**
- **React Frontend:** 5-minute cache for API responses
- **WordPress:** Object caching with Redis (optional)
- **Static Assets:** 1-year browser cache
- **API Responses:** 5-minute cache headers

### **Database Optimization:**
- **Custom post type** indices for fast queries
- **WordPress transients** for expensive operations
- **Query optimization** for REST API endpoints

---

## 🛡️ **Security Configuration**

### **WordPress Security:**
- **Admin directory** protected (`/wp/wp-admin/`)
- **File permissions** properly configured
- **Security headers** in place
- **Regular updates** scheduled

### **API Security:**
- **CORS** properly configured for React domain only
- **Authentication** for admin operations
- **Rate limiting** on API endpoints

---

## 📞 **Content Management Support**

### **Adding New Portfolio Items:**
1. Go to `Portfolio → Add New`
2. Fill in project details and custom fields
3. Upload featured image
4. Publish - appears automatically on frontend

### **Managing Blog Posts:**
1. Go to `Posts → Add New`  
2. Write content with rich text editor
3. Set featured image and excerpt
4. Publish - appears in blog section

### **Updating Services:**
1. Go to `Services → Edit`
2. Update pricing, duration, features
3. Save changes
4. Frontend updates within 5 minutes

---

**Your WordPress backend provides powerful content management while your React frontend delivers exceptional user experience and performance.** 🚀