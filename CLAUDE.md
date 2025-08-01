# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a comprehensive SEO analytics and brand intelligence dashboard project for TITIKA, a premium women's activewear brand. The project consists of multiple HTML dashboards that visualize SEO diagnostics, AI visibility analysis, competitive intelligence, and strategic recommendations using ECharts for data visualization.

## Critical File Naming Issue

**IMPORTANT**: There is a naming discrepancy between the portal navigation (index.html) and actual dashboard files:
- index.html references: `step1-discover-*.html` and `step2-analyze-*.html`
- Actual files are named: `geo-*.html`
- This needs to be resolved by either renaming files or updating index.html references

## Project Structure

```
/Titika/
├── index.html                 # Main portal page with navigation
├── TITIKA_LOGO.webp          # Brand logo asset
├── titika-faq-100.svg        # FAQ visualization diagram
├── md/                       # Markdown documentation
│   ├── step1-discover-*.md   # Discovery phase analysis
│   ├── step2-*.md           # Analysis and remediation docs
│   └── TITIKA_Remediation_Plan.md  # Comprehensive action plan
└── *.html                    # Dashboard files
```

### Dashboard Files

1. **Portal & Navigation**
   - `index.html` - Main entry point with sidebar navigation (默认加载 titika-brand-intr.html)

2. **Brand Dashboards**
   - `titika-brand-intr.html` - Brand introduction page (default)
   - `titika-brand-global.html` - Global market positioning
   - `titika-brand-china.html` - China market analysis
   - `titika-brand-seo.html` - Brand SEO analysis

3. **Discovery Dashboards** (Currently named as geo-*.html)
   - `geo-discover-citation.html` - Citation analysis across platforms
   - Expected: `step1-discover-ai-visibility.html` - AI platform visibility (missing)

4. **Analysis Dashboards** (Currently named as geo-*.html)
   - `geo-authority-gap.html` - Authority gap analysis
   - `geo-content-structure.html` - Content structure optimization
   - `geo-remediation.html` - Remediation strategies

5. **Legacy Dashboards** (Not in current navigation)
   - `titika-seo-diagnostic.html` - Main SEO diagnostic dashboard
   - `titika-seo-diagnostic-a.html` - Alternative SEO analysis

## Technology Stack

- **Frontend**: Pure HTML5, CSS3, JavaScript (ES6+)
- **Charting Library**: ECharts v5.4.3 (CDN)
- **Design System**: Dark theme with brand colors (#e4007c primary)
- **Layout**: CSS Grid, Flexbox, responsive design
- **Animation**: CSS keyframes and transitions

## Development Commands

```bash
# Open any dashboard directly in browser
open [dashboard-name].html

# Serve with Python (if installed)
python3 -m http.server 8000

# Serve with Node.js (if installed)
npx http-server

# Serve with Live Server VS Code extension
# Right-click HTML file → "Open with Live Server"
```

## Code Architecture

### Portal Navigation Pattern (index.html)

The main portal uses a collapsible sidebar navigation:

```javascript
// Menu structure: 3 main categories with submenus
1. Brand 品牌
2. Discover AI可见度分析  
3. Analyze 竞争情报分析

// Key functions:
toggleMenu(header) - Expands/collapses menu sections
loadPage(url, element) - Loads dashboard in iframe
toggleSidebar() - Mobile menu toggle
```

### Dashboard Structure Pattern

Each dashboard follows this consistent pattern:

```javascript
// 1. CSS Variables & Theme
:root {
    --primary-color: #e4007c;  // TITIKA brand pink
    --bg-dark: #0a0e27;        // Dark theme background
    --bg-darker: #050814;      // Darker variant for contrast
}

// 2. Chart Initialization
const chartName = echarts.init(document.getElementById('chartId'));

// 3. Chart Options with Brand Styling
const chartOption = {
    tooltip: { /* hover interactions */ },
    series: { /* data visualization */ }
};

// 4. Responsive Handling
window.addEventListener('resize', () => chartName.resize());
```

### Data Integration

- All data is currently hardcoded in JavaScript
- Charts use static datasets for demonstration
- Real-time data integration points are marked with comments

### Key Visual Patterns

1. **Dark Theme**: All dashboards use dark backgrounds (#0a0e27)
2. **Glass Morphism**: Cards use backdrop-filter and transparency
3. **Gradient Accents**: Linear gradients for visual hierarchy
4. **Hover States**: Transform and shadow effects on interaction

## Important Implementation Notes

### Multi-language Support
- Some dashboards have Chinese content that should remain as-is
- When creating new dashboards, use English for code/comments
- Content can be bilingual based on target audience

### Performance Considerations
- ECharts instances should be properly disposed when not needed
- Large SVG files (like titika-faq-100.svg) should be loaded via iframe
- Implement lazy loading for charts below the fold

### Brand Guidelines
- Primary color: #e4007c (TITIKA pink)
- Typography: -apple-system, BlinkMacSystemFont, 'Segoe UI'
- Spacing: 20px base unit for consistency
- Border radius: 10-20px for modern feel

### Chart Best Practices
- Always include tooltips for data exploration
- Implement resize handlers for responsive behavior
- Use consistent color schemes across related charts
- Add loading states for better UX

## Common Customization Tasks

### Adding New Dashboard
1. Copy existing dashboard as template
2. Update title and meta information
3. Modify chart configurations and data
4. Ensure responsive breakpoints are set
5. Test across different screen sizes

### Updating Chart Data
1. Locate the chart option object
2. Update the `data` array in series
3. Adjust axis ranges if needed
4. Refresh browser to see changes

### Modifying Theme Colors
1. Update CSS variables in `:root`
2. Adjust ECharts color arrays
3. Update gradient definitions
4. Maintain contrast ratios for accessibility