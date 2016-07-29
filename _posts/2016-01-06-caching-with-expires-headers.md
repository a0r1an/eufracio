---
id: 494
title: Caching With Expires Headers
date: 2016-01-06T09:00:16+00:00
author: Adrian Eufracio
description: "Caching is the process of storing data for future use in the cache's memory. The stored data is used to serve the same data even faster for future requests. On the web we can store our websites CSS, JavaScript, Images, fonts and many more file types to the browsers cache."
layout: post
guid: http://adrianeufracio.com/?p=494
permalink: /caching-with-expires-headers/
categories:
  - tooling
---
Caching is the process of storing data for future use in the cache&#8217;s memory. The stored data is used to serve the same data even faster for future requests. On the web we can store our websites CSS, JavaScript, Images, fonts and many more file types to the browsers cache. The browser won&#8217;t request the same file over and over again from the server if the file is stored in the cache. Configuring browser caching can be done within your <i class="code-term">.htaccess</i> file on Apache servers using **Expires Headers**. You can modify the code below to increase the length of time the files are stored and the types of files that are stored.

    # ----------------------------------------------------------------------
    # | Expires headers                                                    |
    # ----------------------------------------------------------------------
    
    <IfModule mod_expires.c>
    
        ExpiresActive on
        ExpiresDefault                                      "access plus 1 month"
    
      # CSS
        ExpiresByType text/css                              "access plus 1 year"
    
      # HTML
        ExpiresByType text/html                             "access plus 0 seconds"
    
      # JavaScript
        ExpiresByType application/javascript                "access plus 1 year"
        ExpiresByType application/x-javascript              "access plus 1 year"
        ExpiresByType text/javascript                       "access plus 1 year"
    
      # Media files
    
        ExpiresByType audio/ogg                             "access plus 1 month"
        ExpiresByType image/bmp                             "access plus 1 month"
        ExpiresByType image/gif                             "access plus 1 month"
        ExpiresByType image/jpeg                            "access plus 1 month"
        ExpiresByType image/png                             "access plus 1 month"
        ExpiresByType image/svg+xml                         "access plus 1 month"
        ExpiresByType image/webp                            "access plus 1 month"
        ExpiresByType video/mp4                             "access plus 1 month"
        ExpiresByType video/ogg                             "access plus 1 month"
        ExpiresByType video/webm                            "access plus 1 month"
    
    
      # Web fonts
    
        # Embedded OpenType (EOT)
        ExpiresByType application/vnd.ms-fontobject         "access plus 1 month"
        ExpiresByType font/eot                              "access plus 1 month"
        # OpenType
        ExpiresByType font/opentype                         "access plus 1 month"
        # TrueType
        ExpiresByType application/x-font-ttf                "access plus 1 month"
        # Web Open Font Format (WOFF) 1.0
        ExpiresByType application/font-woff                 "access plus 1 month"
        ExpiresByType application/x-font-woff               "access plus 1 month"
        ExpiresByType font/woff                             "access plus 1 month"
    
        # Web Open Font Format (WOFF) 2.0
        ExpiresByType application/font-woff2                "access plus 1 month"
    
    </IfModule>

## Implement and Audit

As always, it&#8217;s best to audit the performance of your site once you implement new code. Some file types can be cached longer than others if they don&#8217;t change regularly where as files that do change regularly, like stylesheets and JavaScript files, should be cached for a shorter amount of time.

## Caching Resources

  * <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching" target="_blank">HTTP Caching</a>
  * <a href="https://gtmetrix.com/add-expires-headers.html" target="_blank">Add Expires Headers</a>
  * <a href="https://github.com/h5bp/server-configs-apache/blob/master/dist/.htaccess" target="_blank">H5BP&#8217;S Server Configs</a>