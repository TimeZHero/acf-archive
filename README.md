# ACF Archive

[Forked](https://wordpress.org/plugins/acf-archive/) by Stefano Fasoli due to inactivity

Requires at least: 4.1

Tested up to: 5.4

Requires PHP: 5.4

License: GPLv2 or later

License URI: http://www.gnu.org/licenses/gpl-2.0.html

## Installation

### Via Composer

1. Add a line to your repositories array: `{ "type": "github", "url": "https://github.com/TimeZHero/acf-archive" }`
2. Add a line to your require block: `"timezhero/acf-archive"`
3. Run `composer update`
4. Activate the plugin via the plugins admin page

### Manually

1. Copy the `acf-archive` folder into your `wp-content/plugins` folder
2. Activate the plugin via the plugins admin page

## Description

ACF Archives will add a submenu for each public custom post type with archive defined
and you can attach ACF fields to it.

In headless environments it also exposes a REST API to get those fields, with a `permalink` field generated based on the `HEADLESS_MODE_CLIENT_URL` constant if defined, `wp_home()` otherwise

## Code examples

### Programmatically add / remove the archive page

```
add_filter('acf_archive_post_types', function (array $cpts) {
	// Remove archive page for the 'book' post_type
	unset($cpts['book']);

	// Add archive page for the 'movies' post_type
	$cpts['movie'] = 'Movies Archive';

	return $cpts;
});
```

### Get the archive data

```
$object = get_queried_object();
$field = get_field('field_name', $object->name);

var_dump($field);
```
