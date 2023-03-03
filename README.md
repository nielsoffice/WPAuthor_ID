# WPAuthor_ID
WP Get Author ID base on current post display for pages dynamic fetch for meta data value design for wp function get_user_meta($author_id);

This is who you will get the AUTHOR ID for wp function get_user_meta() will display for a page which current ID base on Developer or Page administrator 
Dispite the fact that the page ID is not base on current post AUTHOR ID from post type with this method you can display the AUTHOR Meta dynamic approach reflect with 
the current post author ID. 

Page ID => Developer account which normally 1 <br />
Post ID => Author or writter create a post   <br />

If you use global $post;  you will take the page ID which made by developer  
and if you use that ID it will reflect the developer user meta not the post author here is interesting things? 
What if yuou have multitple author? and user information or user_meta() must be display on a page that base on the current author post? 

ex.  <br />

Post 1 by author 2 | in about page reflect Post 1 and author 2 information  <br />
Post 2 by author 3 | in about page reflect Post 2 and author 3 information  <br />
Post 3 by author 7 | in about page reflect Post 3 and author 7 information  <br />

This method you can suse thi apprach.  <br />

```PHP

  // Get User ID By Post in Page 
  function get_wp_current_author_post_user_id() {
	 
	$queryPost = new WP_Query([
	   
     // make sure this configuration is match to your about page or main page query result ! 
	   'post_type'     => 'post',
	   'post_per_page' => 1,
	   'orderby'       => 'date',
	   'order'         => 'DESC'
		
	]);  
  
   $queryPost = json_decode(json_encode( $queryPost ), true);
   $queryPost = $queryPost["posts"][0]["post_author"];
  
   return( $queryPost );
  
   }
   
   // Usage: 
   $post_id = get_wp_current_author_post_user_id();
   
   // checking !
   var_dump($post_id);
   
```





