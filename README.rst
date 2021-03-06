VoidyBootstrap
==============

A `Bootstrap 3 <http://getbootstrap.com>`_ blog theme for the
`Pelican <http://getpelican.com>`_ static site generator.

VoidyBootstrap is a theme that aims to be mobile friendly, responsive and
easily customisable.  It can be used in single column mode, or 2 column
mode if the sidebar is enabled.

On larger screens, with the sidebar enabled, it provides a clean and
responsive 2 column layout.  At the top there's a navbar containing page
links, and jumbotron area.  The sidebar has category links and a tag-cloud.
`Font Awesome 4 <http://fontawesome.io/>`_ is used for icons.

While the theme provides lots of customisation options, care has been
taken to make it usable right out of the box with minimal configuration and
sensible defaults -- albeit with the ubiquitous Bootstrap look and feel.

It's functional but deliberately minimal in terms of design.  It can be
used as is, or as a "clean slate" for creating custom Bootstrap-based
websites -- where all the usual scaffolding and fiddly bits are taken care
of, and all that remains is to provide a custom design on top of the
Bootstrap base it provides.

The theme tries to accommodate common blogging needs and provide ways to
easily accomplish common customisations.

Customised CSS, JavaScript and other modifications can be easily
incorporated using configuration settings, and content can be added to the
base layout by strategically adding template fragments (as opposed to
modifying existing templates).


Installation
------------

Clone this repo, then in your ``pelicanconf.py`` set the ``THEME`` variable
to point to it::

  THEME = 'path/to/voidy-bootstrap/'

Out of the box what you get is the stock standard Bootstrap 3 look and
feel.  To customise things see below.


Example Settings
----------------

All of these are optional, but here is a basic example of common variables
that you might want to configure

The following should be set in ``pelicanconf.py``::

  SITESUBTITLE ='Sub-title that goes underneath site name in jumbotron.'
  SITETAG = "Text that's displayed in the title on the home page."

  # Extra stylesheets, for bootstrap overrides or additional styling.
  STYLESHEET_FILES = ("pygment.css", "voidybootstrap.css",)

  # Put taglist at end of articles, and use the default sharing button implementation.
  CUSTOM_ARTICLE_FOOTERS = ("taglist.html", "sharing.html", )
  CUSTOM_SCRIPTS_ARTICLE = "sharing_scripts.html"

  SIDEBAR = "sidebar.html"

  SOCIAL = (('Google+', 'http://plus.google.com/userid',
           'fa fa-google-plus-square fa-fw fa-lg'),
          ('Twitter', 'https://twitter.com/username', 
           'fa fa-twitter-square fa-fw fa-lg'),
          ('LinkedIn', 'http://linkedin-url', 
           'fa fa-linkedin-square fa-fw fa-lg'),
          ('BitBucket', 'http://bitbucket.org/username', 
           'fa fa-bitbucket-square fa-fw fa-lg'),
          ('GitHub', 'http://github.com/username',
           'fa fa-github-square fa-fw fa-lg'),
          )


The following are probably better suited for ``publishconf.py``::

  FEED_DOMAIN = SITEURL
  FEED_ALL_ATOM = 'feeds/all.atom.xml'

  DISQUS_SITENAME = "disqussitename"
  GOOGLE_ANALYTICS = "UA-xxxxxxxxxx"
  GOOGLE_ANALYTICS_SITEID = "gasiteid"
  TWITTER_USERNAME = "twitterusername"



Basic Configuration and Customisation
-------------------------------------

By default all required CSS and JavaScript files are downloaded from CDNs.
Intentionally little is supplied in the theme's ``static/css``.  Just a
``pygment.css`` file, and a sample css file (``voidybootstrap.css``) with
very minimal styling is provided as a starting point.

The simplest way to customise things is to override the standard Bootstrap
styles as necessary.  The theme intentionally avoids loading any additional
stylesheets by default, but this can easily be done by using the
``STYLESHEET_FILES`` setting.  ``STYLESHEET_FILES`` is a list for specifying
additional stylesheets that will be loaded by the ``base.html`` template
after the main Bootstrap CSS file.  Place any CSS stylesheet files you may
require in the ``static/css`` directory and add the filenames to the
``STYLESHEET_FILES`` setting in ``pelicanconf.py``

For example, if you've placed your own CSS styling in a stylesheet called
``custom.css`` (possibly using ``voidybootstrap.css`` as a starting point),
then you would need something like this in your ``pelicanconf.py``::

  STYLESHEET_FILES = ("pygment.css", "custom.css",)


Custom Bootstrap
----------------

As an alternative, or in addition, it's possible to easily replace the
standard Bootstrap file with a customised one.  The
``MAIN_LOCAL_STYLESHEET`` setting is provided for this.  If this variable
is *not* set, a standard ``bootstrap.min.css`` will be used from a CDN.  

To use a different (i.e. customised) Bootstrap stylesheet, set
``MAIN_LOCAL_STYLESHEET`` to the filename of a stylesheet to use instead.

This could be a customised Bootstrap stylesheet compiled manually from the
Bootstrap Less files, or perhaps one obtained from an online source.

For example, you could use the `Bootstrap customizer
<http://getbootstrap.com/customize/>`_ to create your own customised CSS
file.  Place that file in ``static/css`` and set ``MAIN_LOCAL_STYLESHEET``
to be the filename.  

Similarly, a `Bootswatch <http://bootswatch.com/>`_ theme can be easily
integrated.  Select a theme and download the files.  Place all the
necessary CSS files in ``static/css``.  Set ``MAIN_LOCAL_STYLESHEET`` to
the filename of the main Bootstrap CSS file, and specify any additional CSS
files in the ``STYLESHEETS`` list.


Further Customisation
---------------------

Like any other Pelican theme, you can just take the templates provided
and modify them to your liking.  However, if you're happy with the overall
layout and just want to add/subtract things here are there, this theme
provides "hooks" to do just that by simply setting specific
variables in your ``pelicanconf.py`` and/or providing your own template
fragments.  For simple customisations, this can make is relatively
straightforward to isolate modifications and easily keep up to date with
any upstream changes.

These customisation "hooks" are settings that can be configured in
``pelicanconf.py`` to point to filenames of custom template fragments.
These template fragments will either add or replace content in the default
layout provided by the theme.  For example, if ``pelicanconf.py`` contains
the line::

  CUSTOM_FOOTER = "custom/footer.html"

Then the bottom of every page will contain whatever is in the template
file located at::

  templates/includes/custom/footer.html

See the "Custom Includes" section below for details.

Note that for these template fragments must be relative to the theme's
``templates/includes/`` directory.


Standard Settings
-----------------

VoidyBootstrap honors the following `standard Pelican settings
<http://docs.getpelican.com/en/3.5.0/settings.html>`_:

* ``SITEURL``
* ``SITENAME``
* ``SITESUBTITLE``
* ``LINKS``
* ``SOCIAL``
* ``TWITTER_USERNAME``
* ``FEED_DOMAIN``
* ``FEED_ALL_ATOM``
* ``FEED_ALL_RSS`` 
* ``DISQUS_SITENAME``
* ``GOOGLE_ANALYTICS``

For the most part they should work as expected, although some may behave
slightly differently than in the default Pelican theme (see next section).


Settings
--------

This theme supports the following configuration settings.  All are
optional.  


``SITESUBTITLE``
  Sub-title -- displayed in jumbotron.

``SITETAG``
  Text that will be placed in the title on the home page.

``DEFAULT_METADESC``
  Default value for HTML meta description tag.  Individual articles and
  pages can specify their own meta description by using the theme's custom
  ``description`` metadata tag.

``MAIN_LOCAL_STYLESHEET``
  Local Bootstrap CSS file, as described above.

``STYLESHEET_URLS``
  A list of URLS for additional stylesheets that should be pulled in by
  the ``base.html`` template, like CSS files from a CDN.  Useful for adding
  the bootstrap theme CSS, for example.

``STYLESHEET_FILES``
  An list of filenames (relative to the ``/theme/css/`` directory) for
  additional stylesheets that should be pulled in by the ``base.html``
  template (after any STYLESHEET_URLS entries).

``SKIP_DEFAULT_CSS`` 
  No default CSS files at all will be used if this is set to True.  In this
  case the only stylesheets used will be those specified in
  ``STYLESHEET_FILES`` and ``STYLESHEET_URLS``.  This setting is provided
  to give more control over which specific Bootstrap (and Font Awesome) CSS
  files are used (i.e. it allows a specific version to be configured
  through settings).  But it means for things to work properly at a minimum
  the Bootstrap and Font Awesome need to be configured using the
  STYLESHEET_* settings.

``SKIP_DEFAULT_JS``
  Don't load any default JavaScript in the base template.  If this is set
  to True, at a minimum jQuery and the Bootstrap JavaScript must be
  provided via ``JAVASCRIPT_FILES`` and/or ``JAVASCRIPT_URLS``.

``SKIP_DEFAULT_NAVIGATION``
  Don't display navbar at the top of the page.  (If required a custom navigation
  template can be configured via ``CUSTOM_SITE_HEADERS``.)

``JAVASCRIPT_FILES`` and ``JAVASCRIPT_URLS`` 
  Similar to the STYLESHEET_* settings, these allow arbitrary JavaScript
  files to be loaded.  They will be referenced at the bottom of
  ``base.html``, after any default script files.

``ARCHIVES_URL``
  URL of archives page.  Default is ``archives.html``.  If you're modifying
  ``ARCHIVES_SAVE_AS`` in your pelicanconf.py then you'll probably need to
  change this setting as well.

``TWITTER_USERNAME``
  Set to a valid Twitter username to enable the twitter sharing button.

``TWITTER_CARD``
  If set to True, Twitter Card meta-data will be added to article pages.
  If this is enabled, ``TWITTER_USERNAME`` must also be set.

``OPEN_GRAPH``
  Set to True to enable Facebook Open Graph meta-properties.

``OPEN_GRAPH_FB_APP_ID``
  Facebook App ID.

``OPEN_GRAPH_ARTICLE_AUTHOR``
  Value for Open Graph ``article:author`` property, which will be set on
  article pages.

``OPEN_GRAPH_IMAGE``
  Default value for Open Graph ``og:image`` property.
  Articles can use the custom ``social_image`` metadata tag to specify a
  per-article page value.


Sidebar Settings
----------------

As of version 1.1 of VoidyBootstrap, the sidebar is optional.  To enable
the default sidebar, add the following line to your ``pelicanconf.py``::

  SIDEBAR = "sidebar.html"

The "sidebar" area is probably something where everyone will want something
different, so it isn't possible to create an implementation that will
satisfy everyone all the time.  However, there are things that commonly
appear in sidebars (e.g author bio, categories, tag cloud, etc).  So
VoidyBootstrap includes a default sidebar template that provides a fairly
typical sidebar implementation, with a few customisation
settings so that common things can be added and configured via settings in
``pelicanconf.py`` (see below).

However, for those who might want something completely different in a
sidebar, there is the ability to completely replace the default sidebar
template with a custom implementation.  Just create your own sidebar
template (possibly using ``includes/sidebar.html`` as a starting point),
and then set ``SIDEBAR`` to point to it. This will completely replaces the
theme's default sidebar with whatever is in your custom sidebar template.

But for those happy enough to stick with the default sidebar, the following
settings are available to customise it:

``SOCIAL``
  Social media links to display in sidebar.  This option is handled a bit
  differently than in the default theme.  This should be a list/tuple where
  each element is a tuple with 3 elements: (name, URL, Font Awesome icon
  class).  (See the "Example Settings" section above for an example.)  The
  last element (icon class) can be omitted, in which case a generic icon
  will be used instead.

``LINKS``
  Optional list of arbitrary links to display in sidebar.  Each element
  must be a tuple with 2 elements: (link title, URL).

``SIDEBAR_HIDE_CATEGORIES`` 
  A list of categories is displayed in the sidebar by default.  Set this
  option to True to not this category list.

``SIDEBAR_HIDE_TAGS``
  A tag cloud is displayed in the sidebar by default.  Set this option to
  True to disable the tag cloud.

``SIDEBAR_SIZE``
  The number of columns in the Bootstrap grid the sidebar should take up.
  The default is 3.

See also ``CUSTOM_SIDEBAR_TOP`` and ``CUSTOM_SIDEBAR_BOTTOM`` below.


Custom Includes
---------------

The following variables (all optional), if specified, should be set to
paths for template fragments that will be included at strategic points from
the primary templates.  They will usually override existing sections of
content.  All paths must be relative to the theme's ``templates/includes``
directory.


``CUSTOM_SITE_HEADERS``
  List of templates that will replace the default site header area (i.e. the
  jumbotron area).

``CUSTOM_ARTICLE_HEADERS``
  List of templates that will replace the default article header
  provided in ``includes/article_header.html`` on *article pages only*.

``CUSTOM_INDEX_ARTICLE_HEADERS``
  List of templates that will replace the default article article
  header provided in ``includes/article_header.html`` on *index pages only*.

``CUSTOM_ARTICLE_PRECONTENT``
  Template fragment that will be inserted just before the start of the
  article body text, after any headers, image and standfirst.

``CUSTOM_ARTICLE_PREFIX``
  Template fragment that will be inserted before the article headers .

``CUSTOM_ARTICLE_FOOTERS`` and ``CUSTOM_PAGE_FOOTERS``
  List of templates that will included at the bottom of articles/pages,
  after the body text but before the comments.  Can be used to configure
  any appropriate content, like sharing buttons, taglist, etc.

``CUSTOM_HEADER_*``
  Add custom content after the site headers (before any content columns) based
  on page type, which can be: INDEX, ARTICLE, PAGE, CATEGORY, TAG, ARCHIVES.

``CUSTOM_FOOTER``
  Footer template to be included by ``base.html``.  Anything here
  (e.g. copyright text) will appear between footer tags at the bottom of
  every page.

``CUSTOM_SCRIPTS_ARTICLE`` and ``CUSTOM_SCRIPTS_PAGE`` and ``CUSTOM_SCRIPTS_ARCHIVE``
  Template fragment for any additional javascript code specific to articles,
  pages and archives respectively (useful for things like social media sharing
  code).  Will be included at the bottom of pages, just before the
  closing body tag.  Set to ``includes/sharing_scripts.html`` to use the
  default provided implementation.

``CUSTOM_SCRIPTS_BASE``
  As above, but will be included on every page.

``CUSTOM_INDEX_META``
  Included by ``index.html`` between the head tags.  Can be used 
  to add extra HTML meta tags to index pages, for example.

``CUSTOM_SIDEBAR_TOP``
  Included by ``sidebar.html`` at the top of the sidebar.  Provides a
  convenient place for an "about" blurb, for example.

``CUSTOM_SIDEBAR_BOTTOM``
  Included by ``sidebar.html`` at the bottom of the sidebar.



Custom Metadata Tags
--------------------

This theme supports the following (optional) custom metadata tags.

``description``
  Can be used in pages and articles to provide a value for the HTML meta
  description tag, and social meta data (i.e. Open Graph).

``standfirst``
  Text for a summary/intro paragraph that will be placed at the start of an
  article.  This paragraph will be given a CSS class of "standfirst" so
  that additional styles can be applied.

``social_image``
  Set to an image filename (relative to ``{{ SITEURL }}/images/``) to 
  provide a value for an article's ``og:image`` meta property.

``image``
  Set to an image filename (relative to ``{{ SITEURL }}/images/``) to
  display a (responsive) "featured image" at the top of an article,
  underneath any standfirst.

``schema_type``
  Pages only.  A schema.org itemtype for the page.  Default is "WebPage".

``javascript``
  Pages only.  Filename of a JavaScript file (relative to ``theme/js/``
  directory) to load for this page.


Author
------

| Robert Iwancz
| www.voidynullness.net
| `@robulouski <https://twitter.com/robulouski>`_


Screenshot
----------

.. image:: screenshot.png
   :alt: Screenshot of VoidyBootstrap theme with default Bootstrap 3 styling.


License
-------

Licensed under the `MIT License <http://opensource.org/licenses/MIT>`_

Feel free to use as-is or as a basis for your own custom theme.
