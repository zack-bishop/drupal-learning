# drupal-learning

## Introduction

- We'll be learning about waterfals
- Uses a waterfall as an analogy (metaphor?) for learning drupal
- Things we will learn:

1. Data (nodes, etc): Uses content types, probably very similar to CPTS in wordpress
2. Modules: akin to plugins?
3. Blocks & Menus:
4. User Permissions
5. Template

## Unit 1: How to be successful in this course.

- General tips:
    - watch videos more than once
    - plan on having 25 minutes per lesson
    - pause + play as necessary

## Unit 2: Introduction to Drupal

- General info about Drupal, such as it's open source, free, etc.
- https://en.wikipedia.org/wiki/Drupal
- Skipped a lot of this, its a bit of propaganda.

## Unit 3: Install Drupal Locally

- Will probably skip a lot of this as I'm using our drupal learning kit.
- Server requirements appear to be almost identical to WP.
- Composer isn't technically a requirement, but should be treated as such.
- Drupal’s code is split into three main areas: core, contributed and custom.
    - Drupal Core: similar to WP Core. Core files. Don't edit
    - Contributed: Modules and themes found via Drupal.org.
    - Custom: Custom stuff by us or other developers.
- Question: I wonder if the file structure mirrors this?
- `composer.json` vs `composer.lock`: The former is a rough idea of what you'd like to install, the lock file is
  the exact blueprint of all the versions and dependencies installed. Never really knew the difference between them.
- [Guide to composer package versions](https://getcomposer.org/doc/articles/versions.md): This seems interesting!  I'll have to read over to read over this.  Maybe it'll explain how to actually update composer dependencies.  I've just kind of winged it in the past.
- [How to install drupal via composer](https://partners.acquiaacademy.com/learn/course/669/play/5314/unit-3-installing-drupal-with-composer)
   - Installing drupal seems pretty complicated.  Definitely refer to this video down the road.
- Note: When installing Drupal, you'll have to use update the permissions of `sites/default` and `sites/default/settings.php`
- The user you punch in during the setup is a "super user".  The guy in the video stresses that this is the most important user / most attempted to be hacked user.  I wonder if the "super user" is different than a WP Adminstrator.
- Note: use `drush` for site building activities.  use `composer` to update code.  I wonder if in the past, you could use `drush` to update core?
- How to check which scaffolding is in place: `fin composer show drupal/core-recommended`
  - This checks if you're using the recommended scaffolding or if you're running pure core.
  - Returns the following:

```
name     : drupal/core-recommended
descrip. : Core and its dependencies with known-compatible minor versions. Require this project INSTEAD OF drupal/core.
keywords : 
versions : * 10.1.3
type     : metapackage
license  : GNU General Public License v2.0 or later (GPL-2.0-or-later) (OSI approved) https://spdx.org/licenses/GPL-2.0-or-later.html#licenseText
homepage : 
source   : [git] https://github.com/drupal/core-recommended.git d32977bba64355e7399cf63db4cea41b3172d6fa
dist     : [zip] https://api.github.com/repos/drupal/core-recommended/zipball/d32977bba64355e7399cf63db4cea41b3172d6fa d32977bba64355e7399cf63db4cea41b3172d6fa
path     : /var/www
names    : drupal/core-recommended

support
source : https://github.com/drupal/core-recommended/tree/10.1.3

requires
asm89/stack-cors ~v2.1.1
composer/semver ~3.3.2
doctrine/annotations ~1.14.3
doctrine/deprecations ~v1.1.1
doctrine/lexer ~2.1.0
drupal/core 10.1.3
egulias/email-validator ~4.0.1
guzzlehttp/guzzle ~7.7.0
guzzlehttp/psr7 ~2.5.0
masterminds/html5 ~2.8.0
mck89/peast ~v1.15.4
pear/archive_tar ~1.4.14
pear/console_getopt ~v1.4.3
pear/pear-core-minimal ~v1.10.13
pear/pear_exception ~v1.0.2
psr/cache ~3.0.0
psr/container ~2.0.2
psr/event-dispatcher ~1.0.0
psr/http-client ~1.0.2
psr/http-factory ~1.0.2
psr/log ~3.0.0
ralouphie/getallheaders ~3.0.3
sebastian/diff ~4.0.5
symfony/console ~v6.3.0
symfony/dependency-injection ~v6.3.0
symfony/deprecation-contracts ~v3.3.0
symfony/error-handler ~v6.3.0
symfony/event-dispatcher ~v6.3.0
symfony/event-dispatcher-contracts ~v3.3.0
symfony/http-foundation ~v6.3.0
symfony/http-kernel ~v6.3.0
symfony/mime ~v6.3.0
symfony/polyfill-ctype ~v1.27.0
symfony/polyfill-iconv ~v1.27.0
symfony/polyfill-intl-grapheme ~v1.27.0
symfony/polyfill-intl-idn ~v1.27.0
symfony/polyfill-intl-normalizer ~v1.27.0
symfony/polyfill-mbstring ~v1.27.0
symfony/polyfill-php83 ~v1.27.0
symfony/process ~v6.3.0
symfony/psr-http-message-bridge ~v2.2.0
symfony/routing ~v6.3.0
symfony/serializer ~v6.3.0
symfony/service-contracts ~v3.3.0
symfony/string ~v6.3.0
symfony/translation-contracts ~v3.3.0
symfony/validator ~v6.3.0
symfony/var-dumper ~v6.3.0
symfony/var-exporter ~v6.3.0
symfony/yaml ~v6.3.0
twig/twig ~v3.6.0

conflicts
webflo/drupal-core-strict *
```
- composer command to check for outdated: `composer outdated 'drupal/*'`
- command to update (with recommended scaffolding): `composer update drupal/core 'drupal/core-*' --with-all-dependencies`
- command to update (without recommend scaffolding): `composer update drupal/core --with-dependencies`
- update the db via: `fin drush updatedb`
- clear cache: `fin drush cache:rebuild`

## Unit 4: Preparing our Site for Success - The Drupal Essentials
- User #1 is the super user.  Question: Can the super user ever change?
- Wierd: Drupal has administrative and front-end themes.  
- `node`: every drupal content item is referred to as a "node"
- added content along with lesson.
- Seems straightforward, analogous to WP
- Structure: Different from WP?
  - The "regions" structure reminds of elementor / gutenberg.
  - `Structure -> Block Layout -> Custom Block Library` doesn't exist.  Instead, go to `Content -> Blocks`.
  - The blocks are interesting.  I wonder if these came before / after / in response to Gutenberg / WP Page builders?
### Modules:
- Core modules - Modules from the Drupal team
- Contributed modules - Modules from the Drupal community
- Custom modules - Modules from the development team
- Note: don't use the blue "Install New Module" button to install modules.  Use composer.
### Role Permissions
- It's very interesting that Drupal has so few default roles
- You can see all role permissions from the backend, which is definitely a difference from WP.
### Reports
- I really dig the Reports tab.  
- It's nice that you can see all the 404s and junk by default.
- It's super handy that you can see a log of all the actions taken by the users.
- `Configuration -> Development -> Logging Errors`: How you can enable debugging.
- The `Help` menu contains links to the documentation for all the installed modules?!  That's awesome!

## Unit 5: Content Types and Content Modeling
- `Content Entity` == `Custom Post Type`?
- Also, kind of sounds like everything is configured via the backend?  Like entities are defined in the backend. Or does the author mean that the data is filled out in the backend?
  - Its all configurable from the backend.  Interesting!
- Revisions: interesting, you have to update the revision log manually.  Or, more accurately, you're able to enter a description of the work you did.
- Are "machine names" for fields editable?  I don't think they are.  Better be mindful of this moving forward.
- Noticed the images on the Waterfalls can only be uploaded.  I wonder what needs to be done to use the media library to select pre-existing images.
  - Answer: Use the media library module.  This allows images to be re-usable
- Super-interesting that the fields that have been added already show up on the front end.  
- It's interesting that some field settings cannot be changed after content is uploaded. 

### Media
- The media system is different in version 7 as opposed to 8 and above.
- Similar to wordpress, media are a post type / entity.  However, unlike WordPress, it appears as though Media is treated more like an entity than in wordpress
  - For instance, in WP, you couldn't add fields to media as easily as in Drupal.
  - The Source field is the most important with media types.
- I like how "external media" is a thing.
- I also like how you can define the directory for media.

### Taxonomy
- I like how they describe them as "Vocabularies"
- It's interesting that you can create taxonomies that are just "out there."  You don't have to assign them to a thing.
- It's interesting that you have to create a reference field to assign a Vocabulary to a thing.
- Just noticed this, but it's interesting how all the Content just "lives together" under the Content menu.  What I mean is, individual post types aren't organized by content type.


## Unit 6: User Roles and Permissions
- Permissions given to the Authenticated User role get inherited to other user roles.  That feels weird to me, but I think I understand the logic.
- Not much else to report here.

## Unit 7: Building what appears on the page
- kinda don't like how the blocks can be filtered by the page URL.  This seems fragile.  What if the URL for the page is updated?  Does Drupal know to change this setting?
  - Tested this out.  changing the URL of the about page broke the hiking guide block.
- Hmmm.  I think I like the drupal.org/projects module details.  It's nice to have a more developer oriented view about the modules you want to install
- The pathauto module is interesting.  
- I kind of appreciate that the flushing of caches is right there under the Drupal Drop menu.  It's kind of an improvement over having to "flush permalinks" by clicking a save button buried in menus.

## Unit 8: The Views Interface, an Introduction
- Interesting.  The views section is framed around displaying "lists" (which sounds analogous to archives) of content.
- Interesting.  The author of the video says "first preference" should be given to use the Views UI over custom code.  I wonder if that holds up in practice?
- The `For` dropdown in confusing.  What exactly is this doing? Used around the 3:00 mark in [https://partners.acquiaacademy.com/learn/course/669/play/5179/unit-8-creating-blocks-with-views](https://partners.acquiaacademy.com/learn/course/669/play/5179/unit-8-creating-blocks-with-views)
  - OH!  The `For` option determines if this should be applied to all `Display` versions of this view, i.e the `Listing` view and the `Block` view.

## Unit 9: Field Entities and Managing Displays
- Neat that Drupal offers a `default` and `teaser` option for both displays by default

### View Modes
- Kind of fuzzy on what they are
- This is really interesting how you can create view modes to display stuff.  I feel like it has a lot of potential, just not seeing it at this time.  
