# AI Jamstack Template - Claude Code Instructions

This is a master template for generating client websites in one shot. Do NOT read every file - use this document as your complete reference.

## Stack
- **Astro 4.0** static site generator with Islands Architecture
- **Tailwind CSS 3.3** with forms + typography plugins
- **js-yaml** for config loading
- **GitHub Pages** deployment via GitHub Actions
- **Formspree** for contact forms

## One-Shot Generation Workflow

When the user provides client details, do the following in order:

### Step 1: Copy Template Files
Copy the entire template into the client project directory (or clone fresh). Remove the `_template` folder, `dist/`, and `node_modules/` if present.

### Step 2: Update Config (`config.yaml`)
This is the central config file. All pages read from it at build time via `js-yaml`.

```yaml
site:
  title: "Business Name"
  description: "2-3 sentence SEO description"
  url: "https://USERNAME.github.io/REPO-NAME"
  author: "Business Name"

branding:
  logo: "/assets/logo.svg"
  primaryColor: "#hex"      # Main brand color (used in gradients, buttons)
  secondaryColor: "#hex"    # Darker shade of primary
  accentColor: "#hex"       # CTA buttons, highlights (amber/gold works well)
  fontFamily: "Inter, system-ui, sans-serif"

contact:
  email: "email@business.com"
  phone: "+1 (XXX) XXX-XXXX"
  address: "Full street address"
  businessHours: "Mon-Fri 8AM-5PM | Sat 9AM-1PM"

social:
  facebook: ""   # Full URL or empty string to hide
  twitter: ""
  instagram: ""
  linkedin: ""
  youtube: ""

features:
  blog: true       # Show/hide blog nav link and page
  products: true   # Show/hide services nav link and page
  testimonials: true
  faq: true
  search: false
  comments: false
  analytics: false

integrations:
  formspree_id: "your-formspree-id"
  google_analytics: ""
  map_coordinates:
    lat: 0.0
    lng: 0.0

seo:
  keywords: ["keyword1", "keyword2", "local SEO terms"]
  og_image: "/assets/og-image.svg"
  twitter_card: "summary_large_image"
```

### Step 3: Update `astro.config.mjs`
Change these two lines to match the client's GitHub Pages URL:
```js
site: 'https://USERNAME.github.io',
base: '/REPO-NAME',
```

### Step 4: Update Layout (`src/layouts/BaseLayout.astro`)
This file contains the JSON-LD structured data. Update these hardcoded values:

- **Line ~42**: `jsonLdObj["@type"]` - Change from `"HomeAndConstructionBusiness"` to the appropriate Schema.org type:
  - Landscaping: `"LandscapingBusiness"` (not a real schema type - use `"HomeAndConstructionBusiness"` or `"LocalBusiness"`)
  - Restaurant: `"Restaurant"`
  - Dentist: `"Dentist"`
  - Generic: `"LocalBusiness"`
  - See https://schema.org/LocalBusiness for subtypes
- **Line ~49**: `priceRange` - Adjust (e.g., "$", "$$", "$$$")
- **Lines 51-56**: `address` object - Update `streetAddress`, `addressLocality`, `addressRegion`, `postalCode`, `addressCountry`
- **Lines 65-68**: `openingHoursSpecification` - Update days and hours
- **Line 69**: `areaServed` - Update service area name
- **Line 148**: `.skip-link` background color - Match primary brand color

### Step 5: Update Header (`src/components/Header.astro`)
- **Line 63**: Subtitle text under logo (e.g., `"General Contractor"` → `"Landscaping & Design"`)
- **Lines 116-124**: Remove or rename the "Templates" nav link if not needed for this client
- **Lines 203-207**: Same for mobile nav "Templates" link

### Step 6: Update Footer (`src/components/Footer.astro`)
- **Line 30**: Subtitle under logo (same as header)
- **Lines 33-35**: Company description paragraph
- **Lines 52-70**: Services list - Replace with client's actual services
- **Lines 194-198**: Service area cities - Replace with client's service area
- **Lines 207-225**: Trust badges - Update to match client (e.g., "CO Licensed" → "BC Licensed", warranty terms, etc.)
- **Line 233**: License number text

### Step 7: Update Homepage (`src/pages/index.astro`)
The homepage has these sections (all need client-specific content):

1. **Hero Section** (~line 20-88): Badge text, h1 headline, description paragraph, CTA button text, stat counters (years, projects, rating), hero image alt text
2. **Trust Bar** (~line 98-118): 4 trust items with icons and labels
3. **Features Section** (~line 122-170): 3 feature cards with icons, titles, descriptions
4. **About Preview** (~line 174-208): Section title, two paragraphs of company story, image
5. **Testimonials** (~line 210+): 3 testimonial cards with quotes, names, project types, initials
6. **Guarantees Section**: Trust guarantees relevant to the industry
7. **CTA Section**: Final call-to-action

### Step 8: Update About Page (`src/pages/about.astro`)
- Page title and meta description
- Hero: tagline, h1, subtitle
- Company story: founder names, origin story, history, stats
- Core values: 3 value cards with icons
- Team section: team member names, roles, descriptions
- Service area section
- JSON-LD: schema type in frontmatter

### Step 9: Update Services Page (`src/pages/services.astro`)
- `services` array (~line 13-49): Replace all 6 services with client's services (title, description, icon SVG path, price)
- `process_steps` array (~line 52-57): Update the 4-step process
- Hero text, meta description
- JSON-LD service schema

### Step 10: Update Contact Page (`src/pages/contact.astro`)
- Hero text and meta description
- Form field placeholders (phone format, etc.)
- Service type dropdown options in the form
- Contact info cards (already pulled from config)
- Map integration (coordinates from config)

### Step 11: Update Blog Page (`src/pages/blog.astro`)
- `articles` array (~line 13-35): Replace 3 sample articles with industry-relevant topics
- Hero text
- Category filter buttons

### Step 12: Update FAQ Page (`src/pages/faq.astro`)
- `faqs` array (~line 13-46): Replace all Q&As with industry-specific FAQs
- Hero text
- JSON-LD FAQPage schema is auto-generated from the array

### Step 13: Update Privacy & Terms Pages
- `src/pages/privacy.astro`: Update business name references, data collection specifics, industry terms
- `src/pages/terms.astro`: Update service descriptions, jurisdiction, warranty terms

### Step 14: Update Products Data (`src/data/products.yaml`)
Replace all entries with client's actual service packages/products.

### Step 15: Update or Remove Templates Page
`src/pages/templates.astro` is a sales page for website template services. For client websites:
- **Remove it** if not relevant (delete the file)
- **Also remove** the "Templates" nav links from Header.astro and Footer.astro

### Step 16: Update Favicon (`public/favicon.svg`)
Create a simple SVG favicon that matches the client's brand colors and industry.

### Step 17: Update 404 Page (`src/pages/404.astro`)
- Update the suggestion links and messaging to match the client's pages

## Key Patterns to Maintain

### Config Loading (every .astro file)
```astro
---
import { readFileSync } from 'fs';
import { join } from 'path';
import yaml from 'js-yaml';
const configPath = join(process.cwd(), 'config.yaml');
const config = yaml.load(readFileSync(configPath, 'utf8'));
const base = import.meta.env.BASE_URL;
---
```

### Page Structure
```astro
<BaseLayout title="Page Title" description="Meta description">
  <Header slot="header" />
  <!-- page content -->
  <Footer slot="footer" />
</BaseLayout>
```

### Internal Links
Always use `${base}page-name/` with trailing slash:
```astro
<a href={`${base}services/`}>Services</a>
```

### Scroll Animations
Add `animate-on-scroll` class to elements, `stagger-children` to parent containers:
```html
<div class="stagger-children">
  <div class="animate-on-scroll">...</div>
  <div class="animate-on-scroll">...</div>
</div>
```

### Counter Animations
```html
<span data-count="15" data-suffix="+">0+</span>
```

### Card Hover Effects
```html
<div class="card-hover">
  <div class="card-icon">...</div>
</div>
```

## Color Scheme Guidelines by Industry

| Industry | Primary | Secondary | Accent |
|----------|---------|-----------|--------|
| Construction/Contracting | `#1e3a5f` (navy) | `#2563eb` (blue) | `#f59e0b` (amber) |
| Landscaping/Garden | `#166534` (forest green) | `#15803d` (green) | `#f59e0b` (amber) |
| Restaurant/Food | `#991b1b` (deep red) | `#dc2626` (red) | `#f59e0b` (amber) |
| Health/Wellness | `#0e7490` (teal) | `#0891b2` (cyan) | `#10b981` (emerald) |
| Professional Services | `#1e3a5f` (navy) | `#2563eb` (blue) | `#f59e0b` (amber) |
| Beauty/Salon | `#831843` (rose) | `#be185d` (pink) | `#f59e0b` (amber) |
| Auto/Mechanical | `#1c1917` (stone-900) | `#dc2626` (red) | `#f59e0b` (amber) |
| Cleaning Services | `#0e7490` (teal) | `#0284c7` (sky) | `#10b981` (emerald) |

## Schema.org Types by Industry

| Industry | Schema Type |
|----------|------------|
| General Contractor | `HomeAndConstructionBusiness` |
| Landscaping | `HomeAndConstructionBusiness` |
| Restaurant | `Restaurant` |
| Dentist | `Dentist` |
| Hair Salon | `HairSalon` |
| Auto Repair | `AutoRepair` |
| Legal | `LegalService` |
| Accounting | `AccountingService` |
| Plumber | `Plumber` |
| Electrician | `Electrician` |
| Generic | `LocalBusiness` |

## GitHub Actions Deployment
The `.github/workflows/deploy.yml` file handles automated deployment. No changes needed unless the branch name differs from `main`.

## What NOT to Change
- `src/components/Breadcrumbs.astro` - Works dynamically, no edits needed
- `src/env.d.ts` - TypeScript reference, leave as-is
- `package.json` - Dependencies are correct for all site types
- `tailwind.config.mjs` - Works as-is (primary color palette, animations, plugins)
- `.gitignore` - Already configured

## Client Details Template (for user to fill in)
```
Business Name:
Industry:
Location (City, State/Province):
Service Area:
Services (list 4-6):
Contact Email:
Phone:
Address:
Business Hours:
Social Media URLs:
Color Preferences (or leave blank for industry defaults):
Unique Value Proposition:
Years in Business:
Number of Projects/Clients:
Key Differentiators (3):
Team Members (names, roles):
Testimonials (3, with names and context):
FAQs (6-8):
License/Certification Info:
```
