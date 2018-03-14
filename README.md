Node Reference URL Widget
=========================

The Node Reference URL Widget module adds a new widget to the Node Reference
field type. It auto-populates a node reference field with a value from the
URL, and does not allow this value to be changed once set.

Dependencies
------------

 * Node Reference (part of References)

Installation
------------

Installing the Node Reference URL Widget is simple:

1. Install this module using the official Backdrop CMS instructions at
  https://backdropcms.org/guide/modules
2. Enable the module using Administer -> Modules (admin/modules)
3. Add or edit a Node Reference field from admin/structure/types/manage/[type]/fields.
   When configuring the field, use the "Reference from URL" option.
4. Follow on-screen help text to configure your Node Reference URL Widget.

Advanced: Build your own links
------------------------------

Normally you can prepopulate a Node Reference URL widget simply by creating a
link with the following structure:

As HTML:
<a href="/node/add/story/10">Add a story</a>

Or in PHP code:
<a href="<?php print url('node/add/story/' . $node->nid); ?>">Add a story</a>

However if using multiple Node Reference fields, you can populate them by
using a query string instead of embedding the IDs directly in the URL. Assuming
you had two fields, named "field_ref_a" and "field_ref_b", the URL to
prepopulate both of them at the same time would look like this:

In HTML:
<a href="/node/add/story?ref_a=10&ref_b=20">Add a story</a>

Or in PHP code:
<a href="<?php print url('node/add/story', array('query' => array('ref_a' => $nid1, 'ref_b' => $nid2))); ?>">Add a story</a>

Advanced: Support for non-standard URLs
---------------------------------------
By default Node Reference URL Widget will only work with node form paths that
match the standard Drupal install: "node/add/%type", where %type is a node type
like "blog" or "story". If you want to use Node Reference URL Widget on
non-standard URLs, you may do so by informing Node Reference URL Widget of these
special paths.

To do so, add additional paths to your settings.php with the following code:

$conf['nodereference_url_paths'] = array(
  'node/add/%type/%nid',
  'node/%/add/%type/%nid',
);

Only two tokens are supported:
%type: The node type that will be created.
%nid: The node ID that will be referenced.

The % wildcard may be used when including other dynamic IDs.

In the above example, Node Reference URL Widget will work at either
"node/add/story/2" or "node/1/add/story/2", where "2" is the node ID being
referenced. Important to note: The first URL will be used in the links that Node
Reference URL Widget provides.

Support
-------
If you experience a problem with this module or have a problem, file a
request or issue in the Node Reference URL Widget queue at
http://github.com/backdrop-contrib/nodereference_url/issues.
Posting in the issue queues is a direct line of communication with the module
authors.

License
-------

This project is GPL v2 software. See the LICENSE.txt file in this directory for complete text.

Current Maintainers
-------------------

Herb v/d Dool (https://github.com/herbdool/).

Credits
-------

Ported to Backdrop by Herb v/d Dool.

This module was originally written for Drupal by Nate Lampton (https://github.com/quicksketch).

This Module Made by Robots: http://www.lullabot.com
