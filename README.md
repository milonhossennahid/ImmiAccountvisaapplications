# Architecture Overview — Immigration & Citizenship (static site)

This diagram shows a high-level architecture for the provided static site (HTML page). It highlights hosting, CDN, static assets, external services (VEVO, ImmiAccount, PDFs), analytics, and operational pieces such as CI/CD, monitoring and s


Notes
- The site appears to be a static HTML site served from a static host (Netlify in links). Static assets (images) are hosted on an external image host (uploads.onecompiler.io). External links point to authoritative services (VEVO, ImmiAccount, embassy PDFs).
- Recommended improvements:
  - Ensure all external links use HTTPS and include rel="noopener noreferrer" when opening in new tabs.
  - Serve images via the same CDN or a trusted object storage (S3/Cloud Storage) with proper caching headers and optional signed URLs for protected assets.
  - Add Content Security Policy (CSP) and Subresource Integrity (SRI) for critical scripts.
  - Monitor external dependency availability (VEVO/Immi APIs) and display graceful fallbacks.
  - Instrument analytics and error tracking (Sentry/Datadog) with privacy/consent handling for end users.

Deployment checklist (quick)
- [ ] TLS for custom domain + HSTS
- [ ] CDN caching + cache-control headers
- [ ] WAF and bot protection
- [ ] CI checks (lint, accessibility, security scan)
- [ ] Automated backups for important assets
