# Monkeyfuse Website

Simple holding page for monkeyfuse.com to meet Apple App Store requirements.

## Setup Instructions

### 1. Enable GitHub Pages

1. Go to your repository settings on GitHub
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select the branch you want to deploy (usually `main` or `master`)
4. Click "Save"

### 2. Configure DNS for Custom Domain

To use your custom domain `monkeyfuse.com` with GitHub Pages, configure your DNS records:

#### Option A: Using CNAME (Recommended for www subdomain)

Add a CNAME record:
- **Type**: CNAME
- **Name**: `www`
- **Value**: `monkeyfuse.github.io`
- **TTL**: 3600 (or default)

#### Option B: Using A Records (For root domain)

Add the following A records for the root domain (`monkeyfuse.com`):
- **Type**: A
- **Name**: `@` (or leave blank)
- **Value**: `185.199.108.153`
- **TTL**: 3600

- **Type**: A
- **Name**: `@` (or leave blank)
- **Value**: `185.199.109.153`
- **TTL**: 3600

- **Type**: A
- **Name**: `@` (or leave blank)
- **Value**: `185.199.110.153`
- **TTL**: 3600

- **Type**: A
- **Name**: `@` (or leave blank)
- **Value**: `185.199.111.153`
- **TTL**: 3600

**Note**: GitHub Pages IP addresses may change. Check [GitHub's documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain) for current IP addresses.

#### Option C: CNAME Flattening (If your DNS provider supports it)

Some DNS providers (like Cloudflare) support CNAME flattening, which allows you to use a CNAME record for the root domain:
- **Type**: CNAME
- **Name**: `@` (or root domain)
- **Value**: `monkeyfuse.github.io`

### 3. Verify Domain in GitHub

1. After configuring DNS, go back to your repository's Pages settings
2. Under "Custom domain", enter `monkeyfuse.com`
3. Check "Enforce HTTPS" (this will be available after DNS propagation)
4. GitHub will automatically generate an SSL certificate

### 4. Wait for DNS Propagation

DNS changes can take anywhere from a few minutes to 48 hours to propagate. You can check propagation status using tools like:
- [whatsmydns.net](https://www.whatsmydns.net/)
- [dnschecker.org](https://dnschecker.org/)

### 5. Verify Everything Works

Once DNS has propagated:
- Visit `http://monkeyfuse.com` - should redirect to HTTPS
- Visit `https://monkeyfuse.com` - should show your site
- Visit `https://www.monkeyfuse.com` - should also work (if configured)

## Local Development

To view the site locally, simply open `index.html` in your web browser, or use a local server:

```bash
# Using Python 3
python3 -m http.server 8000

# Using Node.js (if you have http-server installed)
npx http-server
```

Then visit `http://localhost:8000`

## Files

- `index.html` - Main landing page
- `privacy.html` - Privacy policy page (required by Apple)
- `CNAME` - GitHub Pages custom domain configuration
- `README.md` - This file

## Cost

- **Hosting**: $0/month (GitHub Pages free tier)
- **Domain**: Already owned
- **Total**: $0/month

## Support

For questions or issues, contact: contact@monkeyfuse.com

