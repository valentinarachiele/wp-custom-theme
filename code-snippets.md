**video 09** (inserimento dello slider e tag conditionali — conditional tags)
https://developer.wordpress.org/themes/basics/conditional-tags/

```php+HTML
<?php if(is_page('Homepage')) : ?>
    <!-- fai qualcosa -->
<?php else : ?>
    <!-- fai un'altra cosa -->
<?php endif; ?>
```



---

**video 10** (wp_query)
https://developer.wordpress.org/reference/classes/wp_query/

```php+HTML
<?php
$args = array(
    'category_name' => '',
    'post_type' => 'post',
    'posts_per_page' => '',
    'post_type' => 'post',
    'post_status' => 'publish',
    'order' => 'ASC',
    'orderby' => 'date',
);
$query = new WP_Query( $args );
if ( $query->have_posts() ) {
    echo '<ul class="category posts">';
        while ( $query->have_posts() ) {
            $query->the_post();
?>
            <li <?php post_class( 'left' ); ?>>
                <a href="<?php the_permalink(); ?>" title="<?php the_title_attribute(); ?>">
                    <?php the_title(); ?>
                </a>
            </li>
            <?php 
        }
    echo '</ul>';
}
wp_reset_postdata(); 
?>
```

https://github.com/Automattic/underscores.me/blob/master/templates/homepage.php

---

**video 11** (registrazione e creazione di una nuova zona widget — sidebar)

```php+HTML
// dentro a functions.php
add_action( 'widgets_init', 'miasidebar' );
function miasidebar() {
  $args = array(
    'name'          => 'Header sidebar',
    'id'            => 'header-sidebar',
    'description'   => 'Nuova area widget nella testata del mio tema',
    'class'         => '',
    'before_widget' => '<div>',
    'after_widget'  => '</div>',
    'before_title'  => '<h2 class="widgettitle">',
    'after_title'   => '</h2>' 
  );
  register_sidebar( $args );
}

// nel file php dove si desidera visualizzare la zona widget
<?php if ( is_active_sidebar( 'header-sidebar' )  ) : ?>
  <?php dynamic_sidebar( 'header-sidebar' ); ?>
<?php endif; ?>
```



---

**video 13** (inserimento di contenuti speciali: accordions, tabs, tooltips, drawers)

```php
//per inserire uno shortcode dentro ad un file php
<? php echo do_shortcode( "[your_shortcode]" ); ?>
```



---

**video 14** (inserimento di icone nel menu e inserimento di altri menu)

```php
//dentro a functions.php
wp_enqueue_style( 'fontawesome', 'https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css' );
```



---

**video 18** (personalizzazione del template di un singolo contenuto personalizzato)

```php
<?php the_field(' '); ?>
```



---

**video 22** (personalizzazione della search form)

<form role="search" method="get" class="search-form" action="<?php echo esc_url( home_url( '/' ) ) ?>">
	<label>
		<span class="screen-reader-text"><?php _x( 'Search for:', 'label' )?></span>
		<input type="search" class="search-field" placeholder="<?php echo esc_attr_x( 'Search &hellip;', 'placeholder' ) ?>" value="<?php echo get_search_query() ?>" name="s" />
	</label>
	<button type="submit" class="search-submit"><i class="fa fa-search"></i></button>
</form>

---

[*](#*)Per togliere i link di Altervista nel footer del sito

```css
.av-credit-link {
    visibility: hidden;
    display: none;
}
```

