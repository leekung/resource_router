# Template Routes

Control your URLs by remapping URI routes to a specific template, using [CodeIgniter-style](http://ellislab.com/codeigniter/user-guide/general/routing.html) routing rules.

## Installation

* Copy the /system/expressionengine/third_party/template_routes/ folder to your /system/expressionengine/third_party/ folder
* Install the extension

## Usage

### Setting up your routing rules

Your routing rules must be set in your system/expressionengine/config/config.php file.

	$config['template_routes'] = array(
		'blog/category/:any' => 'site/blog-category',
		'blog/:year/:pagination' => 'site/blog-yearly-archive',
		'blog/:any' => 'site/blog-single',
	);

On the left are the URIs you wish to match, and on the right are `template_group/template_name` pairs. You may use wildcard matching in your rule definitions.

### Wildcards

#### :any

Matches any non-backslash character(s).

#### :num

Matches a numeric value.

#### :year

Matches 4 digits in a row.

#### :month

Matches 2 digits in a row.

#### :day

Matches 2 digits in a row.

#### :pagination

Matches a P:num segment.

#### :category

Matches `<your_reserved_category_word>/<category_id_or_url_title>`.

#### :all

Matches all possible segments.

### Matches

If you encapsulate a wildcard in parentheses, that segment will be available as a variable to dynamically call a template:

	$config['template_routes'] = array(
		'blog/:any/:any' => 'site/$1_$2',
	);

It will also be available within your template as a tag variable:

	{route_1} - the first parenthesized match
	{route_2} - the 2nd, and so forth

### Regular Expressions

Like standard CodeIgniter routing, you may also use regular expressions in your routing rules:

	$config['template_routes'] = array(
		'blog/([A-Z])/:any' => 'blog/alphabetized',
	);