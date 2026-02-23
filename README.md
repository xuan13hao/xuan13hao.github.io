# Academic Homepage

A clean, minimal, professional academic website built with Jekyll for GitHub Pages.

## Features

- **Mobile-first responsive design** with dark mode support
- **Accessible** with semantic HTML and keyboard navigation
- **SEO-friendly** with jekyll-seo-tag and jekyll-sitemap
- **Data-driven content** via YAML files in `_data/`
- **Card-style layouts** for publications, projects, and news
- **System fonts only** - no external dependencies

## Local Development

### Prerequisites

- Ruby (2.7 or higher)
- Bundler gem
- Ruby development headers (for building native extensions)
  - On Ubuntu/Debian: `sudo apt-get install ruby-dev`
  - On Fedora/RHEL: `sudo dnf install ruby-devel`
  - On macOS: Usually included with Xcode Command Line Tools

### Setup

1. Configure bundler to install gems locally (optional, but recommended):
   ```bash
   bundle config set --local path 'vendor/bundle'
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

3. Build and serve locally:
   ```bash
   bundle exec jekyll serve
   ```

4. Open your browser to `http://localhost:4000`

The site will automatically rebuild when you make changes to source files.

**Note:** Local development is optional. GitHub Pages will build your site automatically when you push to the repository, so you can skip local setup if you prefer.

## Updating Content

All content is managed through YAML files in the `_data/` directory:

### Profile Information (`_data/profile.yml`)

Update your personal information, bio, interests, education, and contact links.

### News (`_data/news.yml`)

Add news items with:
- `date`: Date in YYYY-MM-DD format
- `text`: News text
- `link`: Optional URL

Example:
```yaml
- date: "2025-01-28"
  text: "New paper published!"
  link: "https://example.com"
```

### Publications (`_data/publications.yml`)

Add publications with:
- `title`: Publication title
- `authors`: Author list
- `venue`: Journal/conference name
- `year`: Publication year
- `type`: Type tag (journal/conference/preprint/software)
- `selected`: Boolean for featured publications
- `doi`, `pdf`, `code`: Optional links

Example:
```yaml
- title: "My Paper Title"
  authors: "John Doe, Jane Smith"
  venue: "Nature"
  year: 2025
  type: "journal"
  selected: true
  doi: "https://doi.org/..."
  pdf: "/assets/papers/paper.pdf"
  code: "https://github.com/..."
```

### Projects (`_data/projects.yml`)

Add projects with:
- `title`: Project name
- `description`: Short description
- `featured`: Boolean for featured projects
- `highlights`: List of key features
- `links`: Object with paper/code/demo URLs
- `image`: Optional image path

Example:
```yaml
- title: "My Project"
  featured: true
  description: "A cool project description"
  highlights:
    - "Feature 1"
    - "Feature 2"
  links:
    paper: "https://..."
    code: "https://github.com/..."
```

## Deployment to GitHub Pages

1. Push your repository to GitHub (branch: `main`)

2. Go to your repository Settings → Pages

3. Under "Source", select:
   - Branch: `main`
   - Folder: `/ (root)`

4. GitHub Pages will automatically build and deploy your site

5. Your site will be available at `https://xuan13hao.github.io`

### Notes

- GitHub Pages uses Jekyll 4.x with a limited set of plugins
- Only whitelisted plugins are supported (jekyll-seo-tag, jekyll-sitemap, jekyll-feed)
- The site builds automatically on push to the main branch
- Build logs are available in the Actions tab

## Site Structure

```
.
├── _config.yml          # Jekyll configuration
├── _data/               # YAML data files
│   ├── profile.yml
│   ├── news.yml
│   ├── publications.yml
│   └── projects.yml
├── _includes/           # Reusable components
│   ├── header.html
│   └── footer.html
├── _layouts/            # Page layouts
│   ├── default.html
│   ├── home.html
│   └── page.html
├── _posts/              # Blog posts (optional)
├── assets/
│   └── css/
│       └── main.css     # Main stylesheet
├── index.html           # Home page
├── publications.md      # Publications page
├── projects.md          # Projects page
├── cv.md               # CV page
├── blog.md             # Blog page
├── 404.html            # 404 error page
├── Gemfile             # Ruby dependencies
└── README.md           # This file
```

## Customization

### Styling

Edit `assets/css/main.css` to customize colors, fonts, and layout. The CSS uses CSS variables for easy theme customization, including dark mode support via `prefers-color-scheme`.

### Layouts

Modify files in `_layouts/` to change page structure.

### Navigation

Update the navigation menu in `_includes/header.html`.

## License

This template is provided as-is for personal academic use.
