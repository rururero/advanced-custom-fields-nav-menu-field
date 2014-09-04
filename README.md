# Advanced Custom Fields: Nav Menu Field #

This is an [Add-On plugin](http://wordpress.org/extend/plugins/advanced-custom-fields/) for Advanced Custom Fields (ACF) [4](http://www.advancedcustomfields.com/) & [Pro 5](http://www.advancedcustomfields.com/pro) that adds a 'Nav Menu' Field type, allowing you to select from the [menus](http://codex.wordpress.org/Navigation_Menus) you create in the WordPress Admin backend to use on your website's frontend. 

![](http://faisonz.com/wp-content/uploads/2014/01/acf-nav-menu-field-banner-770x250.png)


Using ACF, you can set the Nav Menu Field to return the selected menu’s:

| Return Value   | Usage  |
| ------ | ------------ |
| ID     | for lightweight coding |
| Object | for more involved programming  |
| HTML   | (generated from [wp_nav_menu](http://codex.wordpress.org/Function_Reference/wp_nav_menu)) for quickly displaying a menu  |


## ACF 4 & Pro 5

This version adds support for [ACF Pro 5](http://www.advancedcustomfields.com/pro) to the exisiting [Nav Menu Field plugin](http://wordpress.org/plugins/advanced-custom-fields-nav-menu-field/) by [Faison Zutavern](http://faisonz.com/wordpress-plugins/advanced-custom-fields-nav-menu-field/)  [@Faison](https://github.com/Faison) [@FaisonZ](https://twitter.com/FaisonZ/).

## Example

1. Set up your ACF in the backend and select "Nav Menu ID" as the Return Value
2. On a page or post, select your menu from the dropdown and update the entry
3. Then get the menu you always wanted with:

````php
// Your post id
$post_id = 259; 

// Your ACF field id
$acf_field_id = 'sidebar_menu'; 

// Get the menu id
$field = get_field($acf_field_id, $post_id);  // Object | HTML | ID

$titles = array();

if(!empty($field)){

  // Assuming we selected "Nav Menu ID" as our return type
  // Get the menu object
  $items = wp_get_nav_menu_items($field);
  
  if($items){
  
    foreach($items as $key => $value){
    
      $titles[] = $value->title;
    }
  }
}

// Now do something with the titles
echo implode (" / ", $titles);
print_r($titles);
error_log(json_encode($items));
````

## Links

* [Original ACF 4 Plugin](http://wordpress.org/plugins/advanced-custom-fields-nav-menu-field/)
* [ACF 4 on WordPress.org](http://wordpress.org/plugins/advanced-custom-fields/)
* [ACF 4](http://www.advancedcustomfields.com/)
* [ACF Pro 5](http://www.advancedcustomfields.com/pro)
* [ACF Support Forum: User Submitted Thread : Nav Menu Field] (http://support.advancedcustomfields.com/forums/topic/nav-menu-field/)
* [Creating an ACF Plugin](http://wordpress.org/extend/plugins/advanced-custom-fields/)
* [Get Field in ACF](http://www.advancedcustomfields.com/resources/get_field/)
* [Nav Menus](http://codex.wordpress.org/Navigation_Menus)
