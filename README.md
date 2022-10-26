# TOC sync

I made the following changes to our standard Jekyll files:

- Added an ID to the `docs_menu.html` nav-list container (for scrolling)
- Added code to each link in the `docs_menu.html` page (for highlighting the topic in the content area):
    ```<a href="{{ site.baseurl }}/docs/filename.html" {% if page.url == "/docs/filename.html" %}class="menu_active"{% endif %}>Link Text Here</a>```
- Included new js link in the `head.html` template page:
    ```<script src="{{ site.baseurl }}/assets/js/menu_sync.js"></script>```
- Wrote new js file (to highlight and scroll, if needed):
    ```js
    (function () {
        window.addEventListener('load', function () {
            var menuItem = document.getElementsByClassName('menu_active')[0].parentElement;
            var menuItemTopLocation = menuItem.offsetTop;

            var container = document.getElementById('docs_menu_container')
            var newLocation = menuItemTopLocation - (container.offsetHeight - menuItem.scrollHeight - 50);

            container.scrollTop = newLocation;
    });
})();```
  
  
- Added styling for active menu item in `<head>` of the `docs.html` template:
  ```html
  <style>
        .menu_active{
            background-color:#337ab7;
            color: white;
        }
  </style>```