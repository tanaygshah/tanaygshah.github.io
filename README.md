# Elevar Amplifier - Static Web App

A static web application with two main endpoints designed for deployment on GitHub Pages with custom domain support.

## 🚀 Live Endpoints

- **`/llms.txt`** - Information about the website for LLMs and AI assistants
- **`/products`** - JSON API endpoint with detailed product information

## 📁 Project Structure

```
sample-amplifier/
├── index.html          # Main landing page
├── llms.txt           # LLM information endpoint
├── products.json      # Product data endpoint
├── 404.html          # Custom 404 page with routing
├── _config.yml       # Jekyll configuration
├── .github/
│   └── workflows/
│       └── deploy.yml # GitHub Actions deployment
└── README.md         # This file
```

## 🛠 Deployment Instructions

### 1. GitHub Repository Setup

1. Create a new GitHub repository (can be named anything)
2. Push this code to the repository:

```bash
git init
git add .
git commit -m "Initial commit: Static web app with API endpoints"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select **GitHub Actions**
4. The deployment workflow will automatically run on every push to `main`

### 3. Custom Domain Setup

#### Option A: Using a Subdomain (Recommended)

1. **Add CNAME file** to your repository:
   ```bash
   echo "your-domain.com" > CNAME
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```

2. **Configure DNS** with your domain provider:
   ```
   Type: CNAME
   Name: www (or your preferred subdomain)
   Value: YOUR_USERNAME.github.io
   TTL: 3600 (or default)
   ```

#### Option B: Using Apex Domain

1. **Add CNAME file** as above
2. **Configure DNS** with A records:
   ```
   Type: A
   Name: @ (or leave blank)
   Value: 185.199.108.153
   
   Type: A
   Name: @ (or leave blank)
   Value: 185.199.109.153
   
   Type: A
   Name: @ (or leave blank)
   Value: 185.199.110.153
   
   Type: A
   Name: @ (or leave blank)
   Value: 185.199.111.153
   ```

3. **Add CNAME for www subdomain**:
   ```
   Type: CNAME
   Name: www
   Value: YOUR_USERNAME.github.io
   ```

### 4. Enable HTTPS

1. In GitHub repository settings → Pages
2. Check **"Enforce HTTPS"** (available after domain verification)
3. Wait for SSL certificate provisioning (usually 5-10 minutes)

## 🔧 API Endpoints

### `/llms.txt`
Returns structured information about the website for LLM consumption:
- Site purpose and description
- Instructions for finding product data
- Available endpoints and data formats

### `/products`
Returns JSON array of products with detailed information:
- Product IDs, names, and descriptions
- Pricing and availability
- Technical specifications
- Categories and tags
- Customer reviews and ratings
- Images and media URLs

## 🎨 Features

- **Responsive Design**: Mobile-friendly interface
- **Clean URLs**: Client-side routing for `/products` endpoint
- **SEO Optimized**: Proper meta tags and structured data
- **Fast Loading**: Static files served via CDN
- **Custom 404**: Branded error page with endpoint links
- **CORS Enabled**: API accessible from any domain

## 🔄 Making Updates

1. Edit files locally
2. Commit and push changes:
   ```bash
   git add .
   git commit -m "Update product data"
   git push
   ```
3. GitHub Actions will automatically deploy changes
4. Changes are live within 1-2 minutes

## 📊 Monitoring

- **GitHub Actions**: Check deployment status in the Actions tab
- **GitHub Pages**: Monitor in repository Settings → Pages
- **Domain Status**: Verify DNS propagation with online tools

## 🛡 Security

- Static files only (no server-side processing)
- HTTPS enforced
- No sensitive data exposure
- CORS headers configured for API access

## 📝 Customization

### Adding Products
Edit `products.json` with new product data following the existing schema.

### Styling Changes
Modify the CSS in `index.html` or create separate stylesheets.

### Domain Changes
Update the `CNAME` file and DNS records as needed.

## 🆘 Troubleshooting

### Domain Not Working
- Check DNS propagation (can take up to 24 hours)
- Verify CNAME file contains correct domain
- Ensure DNS records point to correct GitHub IPs

### 404 Errors
- Check file names match exactly (case-sensitive)
- Verify GitHub Pages is enabled and deployed
- Clear browser cache

### JSON Not Loading
- Validate JSON syntax in `products.json`
- Check browser developer tools for errors
- Verify CORS headers if accessing from another domain

## 📞 Support

For issues with:
- **GitHub Pages**: Check GitHub Status and documentation
- **DNS/Domain**: Contact your domain registrar
- **Code Issues**: Check the repository Issues tab
