# ScriptStore

A dark, responsive community library for educational Roblox Studio Luau resources.

## Hosting: GitHub Pages

This repository is configured to deploy from the `main` branch using GitHub Actions.

1. Open **Settings → Pages** in this repository.
2. Under **Build and deployment**, select **GitHub Actions** as the source.
3. The workflow in `.github/workflows/pages.yml` publishes the repository root after each push to `main`.
4. The public URL will be `https://mm2vault.github.io/ScriptStore/` once the first deployment succeeds.

## Supabase setup

1. Create a **separate Supabase project** named **ScriptStore**. Do not reuse the MM2 project's database.
2. In the new project's SQL Editor, run `supabase-schema.sql`.
3. In **Project Settings → API**, copy the Project URL and the **publishable key**.
4. Put those two public values in `supabase-config.js`.
5. Never put a Supabase secret key or `service_role` key in browser code or GitHub.

Until the Supabase project is connected and the schema is installed, the website runs in demo/preview mode. GitHub Pages hosts the frontend; Supabase provides authentication and database services.

## Current MVP

- Search and category filters
- Newest / popular sorting
- Script detail view and copy button
- Supabase email/password authentication
- User submissions enter a pending moderation queue
- Public browsing is limited to approved (published) posts
- Row Level Security on community tables
- Responsive desktop, tablet and mobile layout

## Planned next features

- Author profiles and display names
- Likes and favorites
- Comments
- User dashboard for managing pending submissions
- Secure administrator moderation workflow
- Reporting and abuse prevention

## Content policy

This community is for legitimate Roblox Studio development and learning: gameplay systems, UI, utilities, data patterns, and tutorials. Do not submit exploit executors, cheating scripts, account/session theft, credential collection, or code intended to disrupt other experiences.

## Moderation and security

Submissions are inserted with `status = 'pending'`. The public browser client must never be allowed to approve its own submissions. Administrator moderation will be added through a trusted server-side workflow using protected credentials that are never exposed in this repository.
