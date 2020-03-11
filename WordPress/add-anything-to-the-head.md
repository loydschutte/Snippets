# Add anything to the head in WordPress

function your_function_name() {
  
//Add your code here. Whatever you need except JS and CSS. They have their own way of being added.


add_filter('wp_head', 'your_function_name’);