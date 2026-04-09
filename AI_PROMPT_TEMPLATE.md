# AI Agent Prompt Template

Use this template to generate a complete website using the AI Jamstack Template.

## Client Information Template

```
Business Name: [Client's Business Name]
Industry: [e.g., Bakery, Consulting, Photography, etc.]
Location: [City, State/Country]
Target Audience: [Who are their customers?]
Key Services/Products: [List 3-5 main offerings]
Unique Value Proposition: [What makes them special?]
Brand Personality: [Professional, Friendly, Modern, Traditional, etc.]
Color Preferences: [Any specific colors or leave for AI to choose]
Contact Information:
  - Email: [business email]
  - Phone: [phone number]
  - Address: [physical address]
  - Business Hours: [operating hours]
Social Media: [List any existing social accounts]
Existing Content: [Any brochures, old websites, marketing materials to reference]
Special Requests: [Any specific features or pages needed]
```

## Step-by-Step AI Generation Process

### 1. Configuration Setup
First, update the `config.yaml` file with the client's information:

```yaml
site:
  title: "[Business Name]"
  description: "[2-3 sentence description of the business and what they offer]"
  url: "https://[username].github.io/[repo-name]"
  author: "[Owner's Name]"
  
branding:
  logo: "/assets/logo.png"
  primaryColor: "[Choose based on industry - e.g., #2563eb for professional, #059669 for eco/health, #dc2626 for food/energy]"
  secondaryColor: "[Darker shade of primary]"
  accentColor: "[Complementary color for CTAs]"
  fontFamily: "Inter, system-ui, sans-serif"
  
contact:
  email: "[Business Email]"
  phone: "[Phone Number]"
  address: "[Full Address]"
  businessHours: "[Operating Hours]"
  
social:
  facebook: "[Facebook URL if provided]"
  twitter: "[Twitter URL if provided]"
  instagram: "[Instagram URL if provided]"
  linkedin: "[LinkedIn URL if provided]"
  youtube: "[YouTube URL if provided]"
  
features:
  blog: true  # Set to false if client doesn't need a blog
  products: true  # Set to false if service-only business
  testimonials: true
  faq: true
  search: false  # Advanced feature
  comments: false  # For blog comments via GitHub Issues
  analytics: false  # Client can add later
  
integrations:
  formspree_id: "your-formspree-id"  # Client needs to set up
  google_analytics: ""  # Leave empty initially
  map_coordinates:
    lat: [Latitude of business address]
    lng: [Longitude of business address]
    
seo:
  keywords: ["[relevant", "business", "keywords", "for", "local", "seo]"]
  og_image: "/assets/og-image.jpg"
  twitter_card: "summary_large_image"
```

### 2. Homepage Content Generation
Update `src/pages/index.astro` with personalized content:

**Hero Section:**
- Create a compelling headline that includes the business name and value proposition
- Write a 2-3 sentence description that clearly explains what they do and who they serve
- Ensure CTA buttons point to relevant pages (products/services or contact)

**Features Section:**
- Replace generic features with 3 specific benefits of choosing this business
- Use industry-appropriate icons and language
- Focus on what makes them unique in their market

**About Preview:**
- Write 2-3 paragraphs about the business story, experience, and mission
- Make it personal and authentic to build trust
- Include any relevant credentials, years in business, or achievements

**Testimonials (if enabled):**
- Create 3 realistic testimonials with customer names and titles
- Make them specific to the industry and services
- Include relevant details that would resonate with target audience

### 3. About Page Content
Update `src/pages/about.astro`:

**Company Story:**
- Write the business origin story and mission
- Include founder background if relevant
- Mention years of experience, key achievements
- Update the statistics (years in business, customers served)

**Mission & Values:**
- Customize the three value propositions to match the business
- Use industry-specific language and benefits
- Make each value unique and meaningful

**Team Section:**
- Update with actual team members if provided
- Otherwise, create realistic team member profiles
- Include relevant roles and brief, professional descriptions

### 4. Products/Services Data
Update `src/data/products.yaml`:

- Replace sample products with actual client offerings
- Use appropriate pricing (or "Contact for Quote" if varies)
- Write compelling descriptions that highlight benefits
- Include relevant features and specifications
- Categorize appropriately for the business type
- Mark the most popular or recommended items as "featured"

### 5. Contact Page
The contact page should work with the config settings, but verify:
- Form integration (client needs to set up Formspree account)
- Map coordinates are accurate for the business location
- Contact information matches across all pages
- Business hours are clearly stated

### 6. Content Writing Guidelines

**Tone and Style:**
- Match the brand personality specified by the client
- Use industry-appropriate terminology
- Keep paragraphs short and scannable
- Include relevant keywords naturally for SEO
- Write in active voice when possible

**SEO Optimization:**
- Include location-based keywords for local businesses
- Use the business name consistently
- Create unique, descriptive page titles
- Write compelling meta descriptions under 160 characters
- Include alt text for all images

**Call-to-Actions:**
- Make CTAs clear and action-oriented
- Use verbs like "Get Started," "Contact Us," "Learn More"
- Ensure they're prominent and easy to find
- Direct users to the most important next step

### 7. Image Placeholders
Note where images are needed and provide suggestions:
- Logo: `/assets/logo.png`
- Hero image: `/assets/hero-image.jpg`
- About page images: `/assets/about-story.jpg`
- Product images: `/assets/products/[product-name].jpg`
- OG image: `/assets/og-image.jpg`

Suggest appropriate stock photo searches or image types for each placeholder.

### 8. Blog Content (if enabled)
Create 2-3 sample blog posts in `src/content/blog/`:
- Industry tips and advice
- Behind-the-scenes content
- Case studies or success stories
- Seasonal or trending topics relevant to the business

### 9. Final Quality Checks
- Ensure all placeholder content is replaced
- Verify contact information consistency
- Check that navigation links work properly
- Confirm social media links are correct or removed
- Test that the form integration is properly configured
- Validate that SEO elements are complete

## Industry-Specific Customizations

### For Restaurants/Food Services:
- Focus on menu items in products section
- Include food safety certifications
- Emphasize local ingredients or specialties
- Add hours and reservation information prominently

### For Professional Services:
- Highlight credentials and certifications
- Include case studies or client success stories
- Focus on consultation and custom solutions
- Emphasize expertise and experience

### For Retail/E-commerce:
- Feature best-selling products
- Include product categories and filters
- Add shipping and return information
- Highlight customer service and guarantees

### For Health/Wellness:
- Include certifications and credentials
- Focus on client testimonials and results
- Add privacy and confidentiality notes
- Emphasize personalized approaches

## Success Metrics

A successful AI-generated site should:
- Score 90+ on Google Lighthouse Performance
- Have unique, engaging content throughout
- Include proper SEO meta tags and schema markup
- Be fully mobile-responsive
- Have working contact forms and clear CTAs
- Reflect the client's brand and industry appropriately
- Be ready for immediate deployment to GitHub Pages

## Post-Generation Client Instructions

Provide the client with:
1. Instructions for setting up Formspree for contact forms
2. How to update content and add new blog posts
3. How to connect a custom domain if desired
4. Basic analytics setup instructions
5. How to update contact information and business hours

This template ensures that AI agents can create professional, customized websites that truly serve the client's needs while maintaining the high standards and performance optimizations built into the template. 