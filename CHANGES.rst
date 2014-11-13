ChangeLog - VoidyBootstrap
==========================


1.1 (under development)
-----------------------------------

* Updated Dependencies: 
  - Pelican 3.5 (should work with 3.3 and 3.4, but untested)
  - Bootstrap 3.3.0
  - Font Awesome 4.2.0
  - JQuery 1.11.1

* Sidebar changes:
  - Support for LINKS setting added.
  - SOCIAL setting changed a bit.
  - New settings to disable category links and tag cloud.

* Footer taken out of main container, so now spans entire width of page.
  - If you're using a custom footer.html template, you'll probably want to
    put any content inside a container div.

* More flexible CSS and script handling.
  - New settings: STYLESHEET_URLS, JAVASCRIPT_URLS, JAVASCRIPT_FILES.
  - STYLESHEET_FILES setting replaces STYLESHEETS.
  - Ability to disable loading any default CSS or scripts from CDNs via
    new SKIP_DEFAULT_CSS and SKIP_DEFAULT_JS settings.
  - The above means it's now possible to configure a site to load all CSS
    and JS files from static (sub)directory, without using CDN files at
    all.

* Replaced article_*.html optional templates with custom includes:
  - Removed most CUSTOM_ARTICLE_*.
  - Added CUSTOM_ARTICLE_HEADERS, CUSTOM_INDEX_ARTICLE_HEADERS,
    CUSTOM_ARTICLE_PRECONTENT, CUSTOM_ARTICLE_FOOTERS.

* New custom includes:
  - CUSTOM_PAGE_FOOTERS, CUSTOM_PAGE_SCRIPTS, CUSTOM_FOOTER.

* Added javascript metatag for pages.



1.0 Initial Release (February 2014)
-----------------------------------

* Dependencies: 
  - Bootstrap 3.0.3
  - Font Awesome 4.0.3
  - JQuery 1.9.1

* Includes Open Graph and Twitter Summary Card meta data.

* Some initial microdata support.

* Archives grouped by year, reverse chronological.

* Featured images, social images, standfirst, meta descriptions.
