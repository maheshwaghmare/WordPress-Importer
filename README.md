# WordPress Importer Redux
This repository contains the new version of the [WordPress Importer][] currently in development. [Learn more about the rewrite](https://make.wordpress.org/core/?p=15550).

Fast, lightweight, consistent. Pick three. :palm_tree: :sunglasses:

This fork of [WordPress Importer Redux][] contains many modifications, chief of them are:

1. It is able to import [WXR 1.3-proposed][] instances, while still being able to import
	WXR 1.0, 1.1 and 1.2 instances by seemlessly tranforming them into WXR 1.3-proposed instances
1. Correctly imports WXR instances (of any version) in an [XML Namespaces](http://www.w3.org/TR/xml-names11/)
	aware manner.  See [wordpress-importer's lack of understanding of XML Namespaces causing compatibility issues](https://core.trac.wordpress.org/ticket/27896)
1. Includes the following PRs which have not yet been merged in the main repo:
   1. [Improved hierarchical term handling](https://github.com/humanmade/WordPress-Importer/pull/129)
   1. [Fix bug whereby non-xml files in the media library are shown when "Select it from the Media Library" is clicked](https://github.com/humanmade/WordPress-Importer/pull/124)
   1. [Fix bug on mime-type of uploaded files](https://github.com/humanmade/WordPress-Importer/pull/126)
1. Correctly imports terms that are mentioned in `item/category` but for which there is no `wxr:term`.
	This can happen with exports generated by the standard exporter for terms in the `post_format` taxonomy.
1. There are unit tests
1. I is able to run along side [WordPress Importer][], which is helpful (to me, at least) in evaluating its performance
	in relation to [WordPress Importer][].

Most of the changes are not yet ready to merge into [WordPress Importer Redux][], but I am coordinating with [Ryan McCue](https://github.com/rmccue)
and when they are ready we will merge.

**Note:** You can install [WordPress Exporter Redux][], which is a rewrite of the standard WordPress Exporter, that among other things,
is able to export native [WXR 1.3-proposed][] instances.

[WordPress Importer]: https://wordpress.org/plugins/wordpress-importer/
[WordPress Importer Redux]: https://github.com/humanmade/WordPress-Importer
[WordPress Exporter Redux]: https://github.com/pbiron/WordPress-Exporter
[WXR 1.3-proposed]: https://github.com/pbiron/wxr/1.3-proposed

## How do I use it?

### Via the Dashboard

1. Install the plugin directly from GitHub. ([Download as a ZIP](https://github.com/pbiron/WordPress-Importer/archive/master.zip))
2. Activate the plugin (make sure you also deactivate the original Wordpress Importer if you have it installed).
3. Head to Tools &rarr; Import
4. Select "WordPress (v2)"
5. Follow the on-screen instructions.

### Via the CLI

The plugin also includes CLI commands out of the box.

Simply activate the plugin, then run:

```sh
wp wxr-importer import import-file.xml
```

Run `wp help wxr-importer import` to discover what you can do via the CLI.

## Current Status

The current major items are currently missing or suboptimal in the Importer:

1. UI to inform user performing the import that the WXR instance contains extension markup produced
   by plugins and to give them the opportunity to install/activate those plugins before starting the import
1. Hooks to allow plugins to process/import extension markup in the WXR instance

## How can I help?

The best way to help with the importer right now is to **try importing and see what breaks**. Compare the old importer to the new one, and find any inconsistent behaviour.

We have a [general feedback thread](https://github.com/humanmade/WordPress-Importer/issues/7) so you can let us know how it goes. If the importer works perfectly, let us know. If something doesn't import the way you think it should, you can file a new issue, or leave a comment to check whether it's intentional first. :)

## License

The WordPress Importer is licensed under the GPLv2 or later.

## Credits

Original plugin created by Ryan Boren, [Jon Cave][duck_] (@joncave), [Andrew Nacin][nacin] (@nacin), and [Peter Westwood][westi] (@westi). Redux project by [Ryan McCue](https://github.com/rmccue), [Paul Biron](https://github.com/pbiron) and [contributors](https://github.com/humanmade/WordPress-Importer/graphs/contributors).

[duck_]: https://profiles.wordpress.org/duck_
[nacin]: https://profiles.wordpress.org/nacin
[westi]: https://profiles.wordpress.org/westi
