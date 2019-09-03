# Essential Functions in WordPress

## Header.php

```php
<?php language_attributes(); ?>
```

```php
<?php bloginfo('charset') ?>
```

```php
<?php wp_head(); ?>
```
Should include within the <head></head> section. Related with functions.php and it enques the styles and scripts.

```php
<?php echo site_url(); ?>
<?php echo site_url('/about'); ?>
```
Will return to the home url or a specific url.

## Footer.php

```php
<?php wp_footer(); ?>
```
Should include before closing the <body>. Related with functions.php and it enques the styles and scripts.

## Page.php

```php
<?php wp_list_pages(); ?>
```
Displays a list of WordPress Pages as links. It is often used to customize the Sidebar or Header, but may be used in other Templates as well.

## other

```php
<?php echo get_template_directory_uri(); ?>/images/image_1.jpg
```
Will use to include a image or something


```php
function genius_university_styles() {
    wp_enqueue_style('custom-google-fonts', '//fonts.googleapis.com/css?family=Roboto:300,400,500,700');
    wp_enqueue_style('open-iconic-bootstrap', get_template_directory_uri() . '/css/open-iconic-bootstrap.min.css');
    wp_enqueue_style('genius-university-main-style', get_stylesheet_uri());
}
add_action('wp_enqueue_scripts', 'genius_university_styles');

function genius_university_scripts() {
    wp_enqueue_script('jquery', get_template_directory_uri() . '/js/jquery.min.js', array(), false, true);
    wp_enqueue_script('map', '//maps.googleapis.com/maps/api/js?key=AIzaSyBVWaKrjvy3MaE7SQ74_uJiULgl1JY0H2s&sensor=false', array(), false, true);
}
add_action('wp_enqueue_scripts', 'genius_university_scripts');
```