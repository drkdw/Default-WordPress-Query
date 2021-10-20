<?php

/**
 * Setup Default CPT.
 *
 * File: php/name.php
 */

$atts = shortcode_atts(
	array(
		'number'   => -1,
		'orderby'  => 'menu_order',
		'category' => '',
	),
	$atts,
	'shortcode_slug'
); // Change 'shortcode_slug' as specified in FUNCTIONS.PHP.

$numberposts = $atts['number'];
$order_by    = $atts['orderby'];
$category    = $atts['category'];

// args.
$args = array(
	'post_type'      => 'my_post_type_slug', // Change 'my_post_type_slug' to your Custom Post Type slug.
	'posts_per_page' => $numberposts,
	'post_status'    => 'publish',
	'orderby'        => $order_by,
	'order'          => 'ASC',
	'tax_query'      => array(
		array(
			'taxonomy' => 'my_category_slug', // Change 'my_category_slug' to your Custom Taxonomy slug.
			'field'    => 'slug',
			'terms'    => $category,
			'operator' => 'AND',
		),
	),
);

$my_post_type = new WP_Query( $args );

if ( $my_post_type->have_posts() ) :
	while ( $my_post_type->have_posts() ) :
		$my_post_type->the_post(); ?>

		<p>Hello world!</p>

		<?php
	endwhile;
	wp_reset_postdata();

else :
	_e( 'Woops! Nothing found!', 'hoolite' );
endif;
