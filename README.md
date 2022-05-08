# RSSGenerator

`RSSGenerator` is RSS generator library for PHP 5.5 or later.

![GitHub repo size](https://img.shields.io/github/repo-size/darkterminal/php-rss-generator?label=Repository%20Size&logo=github) ![GitHub all releases](https://img.shields.io/github/downloads/darkterminal/php-rss-generator/total?logo=github) ![GitHub issues](https://img.shields.io/github/issues/darkterminal/php-rss-generator?logo=github) ![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/darkterminal/php-rss-generator?logo=github) ![GitHub Repo stars](https://img.shields.io/github/stars/darkterminal/php-rss-generator?style=social)
[![Packagist](https://img.shields.io/packagist/v/rssgen/php-rss-generator?logo=packagist&labelColor=white&logoCOlor=orange)](https://packagist.org/packages/rssgen/php-rss-generator/) [![Packagist Downloads](https://img.shields.io/packagist/dm/rssgen/php-rss-generator.svg?label=packagist%20downloads&logo=packagist&labelColor=white&logoCOlor=orange)](https://packagist.org/packages/rssgen/php-rss-generator) [![Open Source Software](https://img.shields.io/badge/open_source-🤍-3DA639.svg)](https://opensource.org/)


## Installation

You can install via Composer.

```
composer require rssgen/php-rss-generator
```

## RSS Feed Implementation:

```php
<?php
$feed = new Feed();

$channel = new Channel();
$channel
	->title("Programming")
	->description("Programming with php")
	->url('http://bhaktaraz.com.np/?cat=2')
	->appendTo($feed);

// RSS item
$item = new Item();
$item
	->title("CACHING DATA IN SYMFONY2")
	->description("It is not too easy to enhance the performance of your application. In Symfony2 you could get benefit from caching.")
	->url('http://bhaktaraz.com.np/?p=194')
	->enclosure('http://bhaktaraz.com.np/wp-content/uploads/2014/08/bhakta-672x372.jpg', 4889, 'audio/mpeg')
	->appendTo($channel);

echo $feed;
```

<details>
	<summary>Output</summary>

```xml
<?xml version="1.0"?>
<rss version="2.0">
	<channel>
		<title>Programming</title>
		<link>http://bhaktaraz.com.np/?cat=2</link>
		<description>Programming with php</description>
		<item>
		<title>CACHING DATA IN SYMFONY2</title>
		<link>http://bhaktaraz.com.np/?p=194</link>
		<description>It is not too easy to enhance the performance of your application. In Symfony2 you could get benefit from caching.</description>
		<enclosure url="http://bhaktaraz.com.np/wp-content/uploads/2014/08/bhakta-672x372.jpg" type="audio/mpeg" length="4889"/>
		</item>
	</channel>
</rss>
```
</details>

## Facebook product feed implementation:

```php
<?php
$feed = new Feed();

$channel = new Channel();
$channel
	->title("geekyrepo")
	->description("geekyrepo - for geeks by a geek")
	->url('https://geekyrepo.pasls.com')
	->appendTo($feed);

// Product feed item
$item = new FacebookProductItem();
$item
	->id(78)
	->title("elePHPant Small")
	->description("elePHPant hand made in nepal.")
	->url('https://geekyrepo.pasls.com/product/elephpant-small')
	->availability('in stock')
	->condition('new')
	->googleProductCategory('Apparel & Accessories > Clothing > Underwear & Socks')
	->imageLink('https://geekyrepo.pasls.com/u/591415cc603dc_elephant-blue-small.jpg')
	->brand('GeekyRepo')
	->customLabel0('elephpant-small')
	->customLabel1('ELESM')
	->customLabel2('https://geekyrepo.pasls.com/product/elephpant-small')
	->appendTo($channel);

echo $feed;
```

<details>
	<summary>Output</summary>

```xml
<rss xmlns:content="http://purl.org/rss/1.0/modules/content/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:sy="http://purl.org/rss/1.0/modules/syndication/" xmlns:g="http://base.google.com/ns/1.0" version="2.0">
<channel xmlns:g="http://base.google.com/ns/1.0">
	<title>geekyrepo</title>
	<link>https://geekyrepo.pasls.com</link>
	<description>geekyrepo</description>

	<item xmlns:g="http://base.google.com/ns/1.0">
		<g:id xmlns:g="http://base.google.com/ns/1.0">78</g:id>
		<g:title xmlns:g="http://base.google.com/ns/1.0">elePHPant Small</g:title>
		<g:link xmlns:g="http://base.google.com/ns/1.0">
		https://geekyrepo.pasls.com/product/elephpant-small
		</g:link>
		<g:description xmlns:g="http://base.google.com/ns/1.0">elePHPant hand made in nepal.</g:description>
		<g:availability xmlns:g="http://base.google.com/ns/1.0">in stock</g:availability>
		<g:price xmlns:g="http://base.google.com/ns/1.0">699 NPR</g:price>
		<g:condition xmlns:g="http://base.google.com/ns/1.0">new</g:condition>
		<g:google_product_category xmlns:g="http://base.google.com/ns/1.0">
		Apparel & Accessories > Clothing > Underwear & Socks
		</g:google_product_category>
		<g:image_link xmlns:g="http://base.google.com/ns/1.0">
		https://geekyrepo.pasls.com/u/591415cc603dc_elephant-blue-small.jpg
		</g:image_link>
		<g:brand xmlns:g="http://base.google.com/ns/1.0">geekyrepo</g:brand>
		<g:custom_label_0 xmlns:g="http://base.google.com/ns/1.0">elephpant-small</g:custom_label_0>
		<g:custom_label_1 xmlns:g="http://base.google.com/ns/1.0">
		https://geekyrepo.pasls.com/product/elephpant-small
		</g:custom_label_1>
		<g:custom_label_2 xmlns:g="http://base.google.com/ns/1.0">ELESM</g:custom_label_2>
	</item>

</channel>
</rss>
```
</details>
