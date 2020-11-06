This allows you to add a new user group and set roles for the specified group.

    add_role('newbie', __(
    'Newbie'),
    array(
        'read'            => true, // Allows a user to read
        'create_posts'    => true, // Allows user to create new posts
        'edit_posts'      => true, // Allows user to edit their own posts
    )
