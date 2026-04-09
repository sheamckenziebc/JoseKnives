# AI Jamstack Template

A next-generation GitHub Pages template designed for AI-driven static site generation. This template empowers AI agents to create fully-functional, high-performance websites for small businesses in a single run.

## 🚀 Features

- **Performance-First**: Built with Core Web Vitals in mind (LCP < 2.5s, CLS < 0.1)
- **SEO-Optimized**: Complete structured data, meta tags, and sitemap generation
- **Accessibility**: WCAG 2.x compliant with skip links and semantic HTML
- **Mobile-First**: Responsive design with progressive enhancement
- **Zero Runtime**: Static files with optional JavaScript islands
- **AI-Friendly**: Clear structure and configuration for automated generation

## 🏗️ Built With

- **[Astro](https://astro.build/)** - Static Site Generator with Islands Architecture
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **GitHub Pages** - Free hosting with custom domain support
- **GitHub Actions** - Automated build and deployment

## 📁 Project Structure

```
/
├── public/                 # Static assets (images, fonts, favicon)
├── src/
│   ├── components/        # Reusable UI components
│   ├── layouts/          # Page layouts and templates
│   ├── pages/            # File-based routing
│   ├── content/          # Markdown content (blog posts, etc.)
│   ├── data/             # JSON/YAML data files
│   └── assets/           # Processed assets
├── config.yaml           # Central configuration file
├── astro.config.mjs      # Astro configuration
└── package.json          # Dependencies and scripts
```

## 🤖 AI Agent Instructions

### Quick Start for AI Agents

1. **Clone this template repository**
2. **Configure `config.yaml`** with client information
3. **Generate content** in appropriate directories
4. **Build and deploy** using GitHub Actions

### Configuration (`config.yaml`)

The central configuration file that AI agents should populate:

```yaml
site:
  title: "Client Business Name"
  description: "Brief business description"
  url: "https://username.github.io/repo-name"
  
branding:
  primaryColor: "#2563eb"
  logo: "/assets/logo.png"
  
contact:
  email: "contact@business.com"
  phone: "+1 (555) 123-4567"
  address: "123 Main St, City, State 12345"
  
features:
  blog: true
  products: true
  testimonials: true
```

### Content Generation Guidelines

#### Homepage Content
- **Hero Section**: Compelling headline and value proposition
- **Features**: 3-4 key differentiators with icons
- **About Preview**: Brief company overview
- **Testimonials**: 3 customer reviews (if enabled)
- **Call-to-Action**: Clear next steps

#### Product/Service Listings
Create `src/data/products.yaml`:

```yaml
- name: "Product Name"
  description: "Compelling product description"
  price: "$99"
  image: "/assets/product-1.jpg"
  features:
    - "Feature 1"
    - "Feature 2"
```

#### Blog Posts
Create markdown files in `src/content/blog/`:

```markdown
---
title: "Blog Post Title"
description: "SEO description"
date: "2024-01-15"
author: "Author Name"
tags: ["tag1", "tag2"]
---

Blog content here...
```

### Performance Budgets

Maintain these limits for optimal performance:
- **JavaScript**: < 150 KB (gzipped)
- **Critical CSS**: < 14 KB
- **Images**: WebP format, responsive sizes
- **Fonts**: System fonts or self-hosted with `font-display: swap`

## 🛠️ Development

### Prerequisites

- Node.js 18+ and npm
- Git

### Local Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

### Deployment

This template automatically deploys to GitHub Pages via GitHub Actions when you push to the `main` branch.

#### Manual Setup

1. Enable GitHub Pages in repository settings
2. Set source to "GitHub Actions"
3. Push changes to trigger deployment

## 📊 Performance Features

### Core Web Vitals Optimization

- **Largest Contentful Paint (LCP)**: Optimized images and critical CSS inlining
- **First Input Delay (FID)**: Minimal JavaScript with deferred loading
- **Cumulative Layout Shift (CLS)**: Proper image dimensions and font loading

### SEO Features

- Semantic HTML5 structure
- Open Graph and Twitter Card meta tags
- JSON-LD structured data
- Automatic sitemap generation
- Breadcrumb navigation with schema markup

### Accessibility Features

- Skip navigation links
- Proper heading hierarchy
- Alt text for images
- Keyboard navigation support
- ARIA labels and landmarks

## 🔧 Customization

### Styling

The template uses Tailwind CSS with custom CSS variables:

```css
:root {
  --color-primary: #2563eb;
  --color-secondary: #1e40af;
  --color-accent: #f59e0b;
}
```

### Adding New Pages

1. Create `.astro` file in `src/pages/`
2. Use existing layout: `import BaseLayout from '../layouts/BaseLayout.astro'`
3. Add navigation link in `src/components/Header.astro`

### Form Integration

The contact form is pre-configured for Formspree:

1. Sign up at [Formspree.io](https://formspree.io)
2. Update `formspree_id` in `config.yaml`
3. Form submissions will be emailed automatically

## 🚀 Advanced Features

### Static Search (Optional)

The template supports client-side search using Pagefind:

```bash
# Add search functionality
npm install pagefind

# Build search index
npx pagefind --site dist
```

### Comments (Optional)

Blog comments via GitHub Issues using Utterances:

1. Install Utterances GitHub App
2. Add to blog post template:

```html
<script src="https://utteranc.es/client.js"
        repo="username/repo"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
```

## 📝 Content Guidelines

### Writing for SEO

- Use descriptive, keyword-rich titles
- Include meta descriptions (150-160 characters)
- Structure content with proper headings (H1, H2, H3)
- Add alt text to all images

### Image Optimization

- Use WebP format when possible
- Include multiple sizes for responsive images
- Compress images to < 200KB
- Add proper alt text for accessibility

## 🤝 Contributing

This template is designed to be forked and customized. Contributions that improve AI compatibility, performance, or accessibility are welcome.

## 📄 License

MIT License - feel free to use for commercial projects.

## 🆘 Support

For issues with the template:
1. Check the [Issues](https://github.com/yourusername/ai-jamstack-template/issues) page
2. Review the [Astro documentation](https://docs.astro.build/)
3. Consult the [Tailwind CSS docs](https://tailwindcss.com/docs)

---

## AI Generation Checklist

When using this template, ensure you:

- [ ] Update `config.yaml` with client information
- [ ] Generate homepage content with proper headings
- [ ] Create product/service listings if applicable
- [ ] Write 2-3 blog posts with proper frontmatter
- [ ] Add contact information and business hours
- [ ] Include social media links if provided
- [ ] Optimize images and add alt text
- [ ] Test form submission endpoint
- [ ] Verify mobile responsiveness
- [ ] Check accessibility with Lighthouse
- [ ] Validate HTML and fix any errors

This template provides the foundation for professional, high-performance websites that can be generated entirely by AI agents while maintaining best practices in web development, SEO, and user experience.