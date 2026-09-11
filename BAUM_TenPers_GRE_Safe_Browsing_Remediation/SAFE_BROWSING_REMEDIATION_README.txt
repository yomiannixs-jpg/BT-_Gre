BAUM TenPers GRE — Google Safe Browsing Remediation Build
Date: 2026-09-11

Purpose
-------
Google Search Console reported the production homepage as a sample URL under
Security issues > Deceptive pages. This build reduces ambiguity on the public
landing URL while preserving the GRE application.

Changes
-------
1. index.html is now a public institutional/educational landing page.
   - no password fields
   - no registration form
   - no file/folder picker
   - no software/PWA install prompt
   - no automatic download
   - no automatic redirect
2. The previous authenticated homepage is preserved as app.html.
3. PWA manifest links, pwa-register.js references, and the duplicated inline
   beforeinstallprompt/service-worker registration blocks were removed from
   public HTML pages for the remediation period.
4. The new landing page unregisters any previously installed service worker
   when visited, helping retire older cached PWA behavior.
5. Supabase authentication and core test/study/dashboard functionality remain.
6. No database schema or Supabase Edge Function changes are required.

Recommended deployment
----------------------
Replace the production project files with this build, commit, push, and allow
Vercel to deploy. Test / and /app.html. Then use Google Search Console URL
Inspection > Test Live URL for the homepage. After confirming the clean build
is live, use Security issues > Request Review.

Suggested review statement
--------------------------
The reported homepage has been redesigned to remove potentially ambiguous
installation and authentication interactions. The public landing page now
clearly identifies BAUM TenPers Institute and describes the GRE educational
platform without requesting credentials, initiating downloads, requesting
filesystem access, or prompting software installation. Authentication is
separated from the public landing page and is used only for registered student
access to the GRE platform. We also disabled the site's previous PWA install
and service-worker registration behavior during remediation and reviewed the
site for deceptive content. Please review the site again.
