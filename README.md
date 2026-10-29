# Laravel to WordPress Migrator

A WordPress content migration plugin developed for **Study In Italy** to migrate legacy Laravel website content into WordPress while preserving existing URL structures, content slugs, media assets, and SEO metadata.

**Developer:** MD Sheek Forid  
**Plugin Name:** Italy BD Content  
**Version:** 1.3  
**Plugin Type:** WordPress Migration Tool

## Overview

Laravel to WordPress Migrator helps migrate legacy website content from a Laravel database into WordPress. It provides tools to import content, repair previously migrated records, preserve legacy URLs, create essential website pages, validate URLs, and synchronize SEO metadata.

The plugin was developed for the Study In Italy website migration project.

## Features

- **University Migration:** Imports university information, descriptions, images, and SEO metadata.
- **Service Migration:** Migrates service pages while preserving their legacy slugs.
- **Blog Migration:** Imports blog posts, descriptions, publication dates, featured images, and SEO metadata.
- **Success Story Migration:** Imports student success stories, quotations, YouTube links, and associated images.
- **Team Member Migration:** Imports team member profiles, designations, biographies, and profile images.
- **Achievements Gallery:** Imports achievement images and displays them through a shortcode.
- **About Us Page:** Creates an About Us page using legacy content and images.
- **Media Import:** Imports existing images from a local server directory into the WordPress Media Library.
- **Legacy URL Preservation:** Supports legacy URL patterns such as `/university/{slug}`, `/service/{slug}`, and `/blog/{slug}`.
- **Content Repair:** Detects previously migrated records and repairs certain missing images or legacy content-type issues.
- **SEO Synchronization:** Supports Rank Math and Yoast SEO metadata for imported content and Rank Math metadata for essential pages.
- **URL Validation:** Checks legacy URLs and reports HTTP response codes and redirects.
- **Dry Run:** Previews eligible content imports without saving new content.
- **Page & Permalink Setup:** Creates essential pages and configures the blog permalink structure.

## Content Types

| Legacy Content | WordPress Destination |
|---|---|
| Universities | University custom post type |
| Services | Service custom post type |
| Blog posts | WordPress posts |
| Success stories | Success Story custom post type |
| Team members | Team custom post type |
| Achievements | WordPress Media Library attachments |
| About Us | WordPress page |

## Requirements

- WordPress
- Access to the legacy Laravel database tables
- PHP compatibility with the installed WordPress environment
- Legacy website image files accessible from the WordPress server
- Administrator access to WordPress
- Rank Math and/or Yoast SEO, if SEO integration is required

## Installation

1. Download or clone this repository.
2. Place the plugin folder inside the WordPress `wp-content/plugins/` directory.
3. Ensure the main plugin PHP file is located inside the plugin folder.
4. Activate **Italy BD Content** from the WordPress Plugins screen.
5. Prepare the required legacy database tables.
6. Place the legacy image files in an accessible server directory.

## Migration Workflow

After activating the plugin, navigate to:

**WordPress Dashboard → Tools → Italy Import**

The migration tools are designed to be used in the following order:

### 1. Dry Run

Preview which records are eligible for import without creating new posts or pages.

### 2. Import / Repair Content

Import legacy content into WordPress and repair supported missing media for previously imported records.

The importer stores legacy record IDs in WordPress metadata to help prevent duplicate imports.

### 3. Set Up Pages & Permalinks

Create essential website pages and configure the permalink structure for blog posts.

Review existing pages and site settings before running this step.

### 4. Check Old URLs

Validate legacy URLs against the current WordPress website. The tool reports non-200 responses, redirects, and request errors.

If the process stops because of the execution time limit, run the check again to continue.

### 5. Apply SEO

Synchronize available SEO metadata from legacy database records and populate empty Rank Math metadata for configured pages.

Review the generated SEO metadata and title templates before publishing changes.

## Available Shortcodes

Use these shortcodes in WordPress pages or an Elementor Shortcode widget.

| Shortcode | Purpose |
|---|---|
| `[universities_grid count="100"]` | Displays university cards |
| `[services_grid count="20"]` | Displays service cards |
| `[success_stories count="20"]` | Displays success story videos |
| `[team_grid]` | Displays current team members |
| `[achievements_gallery]` | Displays achievement images |

The card and gallery layouts use inline CSS included in the plugin.

## Legacy URL Structure

The plugin supports the following URL patterns:

- `/university/{slug}`
- `/service/{slug}`
- `/blog/{slug}`

It also creates or supports essential pages such as:

- `/universities`
- `/services`
- `/success-story`
- `/our-team`
- `/achievements`
- `/about-us`
- `/contact-us`
- `/terms-conditions`
- `/privacy-policy`
- `/blog`

Existing pages are left unchanged by the page setup routine when their slugs already exist.

**Important:** Verify permalink settings, existing page assignments, and URL responses after migration. The plugin's URL checker reports results; it does not automatically guarantee that every legacy URL returns HTTP 200.

## Database Preparation

The importer expects these legacy tables:

- `legacy_abroads`
- `legacy_blogs`
- `legacy_services`
- `legacy_success_stories`

Additional content requires:

- `legacy_abouts`
- `legacy_teams`
- `legacy_achievements`

The additional tables are optional. If they are unavailable, the plugin skips the corresponding About Us, team, and achievements imports.

Prepare the legacy tables before running the migration.

## Media Migration

The importer scans a specified directory recursively for image files and matches them by filename against legacy database records.

The default image directory is:

`wp-content/old-uploads`

You can specify a different full server path from the Italy Import administration screen.

Make sure the directory contains the required legacy images and that the WordPress process has permission to read them.

## SEO Integration

The plugin supports legacy SEO metadata fields, including:

- Meta title
- Meta description
- Meta keywords

It writes supported metadata to Rank Math and Yoast SEO fields for imported university, service, and blog content.

For configured pages, the SEO synchronization routine fills empty Rank Math fields without overwriting existing values.

Review SEO settings and generated metadata after migration.

## Important Notes

- **Back up your WordPress database and uploads before migration.**
- Back up the legacy database and image files.
- Test the migration on a staging environment before running it on a production website.
- Run the dry run before importing content.
- Verify legacy IDs, slugs, images, and publication statuses after migration.
- The importer processes records in batches constrained by an execution-time deadline; repeat the operation when prompted to continue.
- The plugin does not migrate Laravel application logic, authentication systems, or every custom database relationship automatically.
- Review the code and database schema before using the plugin on another Laravel project, as legacy table names and field mappings are project-specific.

## Developer

**MD Sheek Forid**

- Portfolio: https://sheekforid.vercel.app/
- GitHub: https://github.com/forid1026
- LinkedIn: https://linkedin.com/in/sfarid1026

## License

No license has been specified yet. Contact the repository owner for permission to reuse, modify, or redistribute this software.