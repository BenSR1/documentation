---
title: Varnish Caching for High Performance with Drupal and WordPress
description: Configure and verify Varnish is working on your WordPress or Drupal sites.
categories: [developing]
tags: [code, varnish]
keywords: wordpress varnish, drupal varnish, cache, caching, pantheon, performance
---
Varnish is an HTTP accelerator that quickly serves both static content and anonymous pages for sites on Pantheon. By serving data from virtual memory, a response is returned without needing to access the application server, which in turns frees application container workers to build more dynamic requests. Each Varnish server can handle thousands of requests per second, much faster than a site's framework alone.  

Every site on Pantheon already uses Varnish; each HTTP request first goes to the pool of Varnish servers to seamlessly cache your site content. If a current cache isn't found, the request will continue to the application container worker, then the response will be cached on the way back to the browser.  

![Varnish Diagram](/source/docs/assets/images/varnish.png)

Varnish can also improve the availability of your site. For example, if a PHP fatal error breaks your site, anonymous page requests can still be served by Varnish and end-users won't realize anything is wrong.


## Configure Your Drupal or WordPress Site for Varnish
<div class="alert alert-info" role="alert">
<h4>Note</h4>
No module or plugin installation is required; do <strong>not</strong> install the Drupal Varnish module.  </div>

Varnish has been configured to respect any HTTP headers served by your site. If you set pages to expire in 5 minutes, Varnish will expire the content as requested. If your site sends headers that forbid caching, Varnish won't cache your content.  

For detailed instructions on how to optimize your caching configuration, see [Drupal's Performance Settings](/docs/drupal-cache) or [WordPress Pantheon Cache Plugin Configuration](/docs/wordpress-cache-plugin/).


## See Also
* [Understanding and Debugging Varnish Cache Issues](/docs/debug-cache/)
* [Testing Varnish](/docs/test-varnish/)
* [Caching: Advanced Topics](/docs/caching-advanced-topics/)
