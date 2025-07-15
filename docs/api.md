## REST API

The plugin provides a REST API endpoint to retrieve user bookmarks.

### Endpoint: Get User Bookmarks

- **URL**: `/wp-json/post-bookmark/v1/user-bookmarks/{user_id}`
- **Method**: GET
- **Parameters**:
  - `user_id` (required, integer): The ID of the user whose bookmarks are retrieved.
  - `page` (optional, integer, default: 1): The page number for pagination.
  - `per_page` (optional, integer, default: 16, max: 100): Number of bookmarks per page.
  - `post_type` (optional, string): Filter by post type (`post` or `product`).
- **Response**:
  - **Success (200)**:
    ```json
    {
      "data": [
        {
          "id": 123,
          "title": "Post Title",
          "image_sizes": {
            "full": "http://example.com/wp-content/uploads/image.jpg",
            "thumbnail": "http://example.com/wp-content/uploads/image-150x150.jpg",
            ...
          },
          "short_content": "Post excerpt..."
        },
        ...
      ],
      "meta": {
        "page": 1,
        "per_page": 16,
        "count": 25
      }
    }
    ```
  - **Error (400)**:
    ```json
    {
      "code": "invalid_user",
      "message": "Invalid user ID",
      "data": {
        "status": 400
      }
    }
    ```
- **Permission**: Public (`__return_true`).

### Example Request
```bash
GET /wp-json/post-bookmark/v1/user-bookmarks/1?page=1&per_page=10&post_type=product
```

## AJAX Actions

The plugin uses AJAX for bookmark toggling.

### Action: Toggle and Render Bookmarks

- **Action**: `toggle_and_render_bookmarks`
- **Method**: POST
- **Parameters**:
  - `security` (required, string): Nonce for security (`fast_bookmark_nonce`).
  - `post_id` (required, integer): ID of the post or product to toggle.
  - `post_type` (optional, string): Type of post (`post` or `product`, default: `post`).
  - `group_id` (optional, integer, default: 0): Bookmark group ID.
- **Response**:
  - **Success**:
    ```json
    {
      "success": true,
      "data": {
        "bookmarked": true/false,
        "html": "<div class='Woocommerce'>...</div>"
      }
    }
    ```
  - **Error**:
    ```json
    {
      "success": false,
      "data": {
        "message": "Please login to see your bookmarks."
      }
    }
    ```
- **Security**: Requires a valid nonce (`fast_bookmark_nonce`) and user login.


**API Access**:
   - Fetch user bookmarks: `GET /wp-json/post-bookmark/v1/user-bookmarks/1?post_type=product`.