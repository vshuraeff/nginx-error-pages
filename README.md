# Nginx Modern Error Pages

This repository contains a collection of modern, responsive, and visually appealing error pages for Nginx servers. These pages are designed to provide clear and user-friendly error messages for various HTTP status codes, improving the user experience when encountering server errors.

<img width="1173" alt="image" src="https://github.com/user-attachments/assets/dc083172-2b59-4c38-9dd0-42ab09f84cbc" />
<img width="1173" alt="image" src="https://github.com/user-attachments/assets/781c9eb6-8404-44e7-977d-3cfe26c1317f" />


## Features

- **Responsive Design**: Pages are fully responsive and adapt to both mobile and desktop screens, including 5K displays.
- **Self-Contained**: Each HTML file includes its own CSS, requiring no external files.
- **Customizable**: Easily modify the styles and content to match your branding.
- **Comprehensive Coverage**: Includes error pages for common HTTP status codes (e.g., 400, 404, 500) and special cases like 418 (I'm a Teapot) and 451 (Unavailable for Legal Reasons).
- **Maintenance Page**: A dedicated maintenance page for scheduled downtime.
<img width="1173" alt="image" src="https://github.com/user-attachments/assets/e84fe151-b321-49b6-915a-44608cb786b6" />

## Included Files

- **HTML Files**: Individual error pages for each HTTP status code (e.g., `400.html`, `404.html`, `500.html`), each containing its own embedded styles.
- **Nginx Configuration**: A sample `nginx.conf` file to integrate the error pages with your Nginx server.

## Installation Instructions

Follow these steps to set up the error pages on your Nginx server:

### 1. Clone the Repository

```bash
git clone https://github.com/vshuraeff/nginx-error-pages.git
cd nginx-error-pages
```

### 2. Copy Files to Your Server

Copy the error pages to a directory on your server. For example:

```bash
sudo cp *.html /usr/share/nginx/html/error_pages/
```

### 3. Update Nginx Configuration

Edit your Nginx configuration file (e.g., `/etc/nginx/nginx.conf`) and add the following lines to configure the error pages:

```nginx
# Error pages configuration
error_page 400 /error_pages/400.html;
error_page 401 /error_pages/401.html;
error_page 403 /error_pages/403.html;
error_page 404 /error_pages/404.html;
error_page 405 /error_pages/405.html;
error_page 408 /error_pages/408.html;
error_page 418 /error_pages/418.html;
error_page 429 /error_pages/429.html;
error_page 451 /error_pages/451.html;
error_page 500 /error_pages/500.html;
error_page 501 /error_pages/501.html;
error_page 502 /error_pages/502.html;
error_page 503 /error_pages/503.html;
error_page 504 /error_pages/504.html;
error_page 505 /error_pages/505.html;

# Maintenance configuration
# Uncomment the following line when maintenance is needed
# return 503 /error_pages/maintenance.html;

# Under construction configuration
# Uncomment this line and provide full path to file
# index underconstruction.html;

# Location for error pages
location ^~ /error_pages/ {
    internal;
    alias /usr/share/nginx/html/error_pages/;
    try_files $uri =404;
}

```

Make sure to update the paths to match the location where you copied the HTML files.

### 4. Test the Configuration

Check the Nginx configuration for syntax errors:

```bash
sudo nginx -t
```

If the test is successful, reload Nginx to apply the changes:

```bash
sudo systemctl reload nginx
```

### 5. Verify the Setup

Trigger different HTTP errors (e.g., by accessing non-existent pages) to verify that the custom error pages are displayed correctly.

## Customization

- **Modify Content**: Edit the HTML files to customize the error messages or add additional information.
- **Change Styles**: Update the styles within each HTML file to match your website's branding.
- **Add New Pages**: Create additional error pages as needed and update the Nginx configuration to include them.

<img width="1173" alt="image" src="https://github.com/user-attachments/assets/5f54bdf2-1bec-40d2-b78d-977834b7f3a8" />


## Benefits of Self-Contained Pages

Each HTML file contains its own CSS styles, providing several advantages:

- **Simplified Deployment**: No need to manage external CSS files.
- **Better Reliability**: Pages will still display correctly even if external resources are unavailable.
- **Faster Loading**: No additional HTTP requests for external stylesheets.
- **Easy Maintenance**: Each page can be edited independently.

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute it as needed.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests to improve the project.
