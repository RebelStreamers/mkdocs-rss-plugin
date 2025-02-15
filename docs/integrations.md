---
title: Integrations
icon: octicons/plug-16
---

## Social Cards plugin (from Material theme)

Since version 1.10, the plugin integrates with the [Social Cards plugin (shipped with Material theme)](https://squidfunk.github.io/mkdocs-material/setup/setting-up-social-cards/) (see also [the full plugin documentation here](https://squidfunk.github.io/mkdocs-material/plugins/social/)).

Here's how the RSS plugin prioritizes the image to be used in the feed:

1. an image (local path or URL) is defined in the page's YAML header of the page with the key `image`. Typically: `image: path_or_url_to_image.webp`.
1. an image (local path or URL) is defined in the page's YAML header with the key `illustration`. Typically: `illustration: path_or_url_to_image.webp`.
1. if neither is defined, but both the social plugin and the cards option are enabled, then the social card image is used.

If you don't want this integration, you can disable it with the option: `use_material_social_cards=false`.

> See [related section in settings](./configuration.md#use_material_social_cards-enabledisable-integration-with-material-social-cards-plugin).

----

## Reference RSS feeds in HTML meta-tags

To facilitate the discovery of RSS feeds, it's recommended to add relevant meta-tags in `<head>` section in HTML pages.

### Automatically set with Material theme

If you're using the Material theme, everything is automagically set up (see [the related documentation page](https://squidfunk.github.io/mkdocs-material/setup/setting-up-a-blog/#rss)) :partying_face:.

### Manually

You need to customize the theme's template. Typically, in `main.html`:

```html
{% extends "base.html" %}

{% block extrahead %}
  <!-- RSS Feed -->
  <link rel="alternate" type="application/rss+xml" title="RSS feed of created content" href="{{ config.site_url }}feed_rss_created.xml">
  <link rel="alternate" type="application/rss+xml" title="RSS feed of updated content" href="{{ config.site_url }}feed_rss_updated.xml">
{% endblock %}
```
