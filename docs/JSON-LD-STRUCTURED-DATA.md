# JSON-LD Structured Data Implementation

## Overview

This document describes the JSON-LD structured data schemas implemented for the Helix landing page to improve SEO and enable rich results in search engines.

## Implemented Schemas

### 1. Organization Schema

```json
{
  "@type": "Organization",
  "@id": "https://openclaw.ai/#organization"
}
```

**Purpose:** Defines OpenClaw as the parent organization behind Helix.

**Properties included:**
- `name`: "OpenClaw"
- `url`: https://openclaw.ai
- `logo`: ImageObject pointing to helix-logo.svg
- `sameAs`: Social links (GitHub, Twitter, Discord)
- `description`: Organization description

### 2. WebSite Schema

```json
{
  "@type": "WebSite",
  "@id": "https://helix.openclaw.ai/#website"
}
```

**Purpose:** Defines the Helix landing page as a website, linked to the Organization.

**Properties included:**
- `name`: "Helix"
- `url`: https://helix.openclaw.ai
- `description`: Site description
- `publisher`: Reference to Organization
- `inLanguage`: "en-US"

**Note:** SearchAction was not included as Helix is a landing page without site-wide search functionality.

### 3. SoftwareApplication Schema

```json
{
  "@type": "SoftwareApplication",
  "@id": "https://helix.openclaw.ai/#software"
}
```

**Purpose:** Defines Helix as a software product for rich results.

**Properties included:**
- `name`: "Helix"
- `description`: Full product description
- `url`: Product URL
- `applicationCategory`: "DeveloperApplication"
- `operatingSystem`: "Linux, macOS, Windows"
- `offers`: Free pricing ($0 USD)
- `author`: Reference to Organization
- `isAccessibleForFree`: true
- `license`: MIT License URL
- `screenshot`: Dashboard overview image
- `featureList`: Array of key features
- `softwareRequirements`: "Node.js 18+"
- `downloadUrl`: GitHub repository
- `installUrl`: Installation instructions
- `releaseNotes`: GitHub releases page

## Schema Relationships

The schemas are interconnected using `@id` references:

```
Organization (@id: "https://openclaw.ai/#organization")
    ↑
    │ publisher / author
    │
WebSite (@id: "https://helix.openclaw.ai/#website")
SoftwareApplication (@id: "https://helix.openclaw.ai/#software")
```

## Validation

### Google Rich Results Test
Test the structured data at: https://search.google.com/test/rich-results

Enter URL: `https://helix.openclaw.ai`

### Schema.org Validator
Alternative validation at: https://validator.schema.org/

### Expected Rich Result Types
- Organization knowledge panel (for OpenClaw brand searches)
- Software application rich results (for product searches)
- Enhanced search snippets

## Files Modified

- `index.html` - Added three `<script type="application/ld+json">` blocks in the `<head>` section

## Resources

- [Schema.org Organization](https://schema.org/Organization)
- [Schema.org WebSite](https://schema.org/WebSite)
- [Schema.org SoftwareApplication](https://schema.org/SoftwareApplication)
- [Google Structured Data Guidelines](https://developers.google.com/search/docs/appearance/structured-data)
