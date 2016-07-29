---
id: 476
title: Gzip Compression Engaged!
date: 2015-12-30T09:00:55+00:00
author: Adrian Eufracio
description: Speed kills on the web and it is our duty to provide the fastest experience possible. Gzip enables HTTP compression by compressing most file types. Compressing these files has proven to reduce files sizes up to 70%!
layout: post
guid: http://adrianeufracio.com/?p=476
permalink: /gzip-compression-engaged/
categories:
  - tooling
---
As Front-End Developers, we need to always focus on creating web apps that are fast. Speed kills on the web and it is our duty to provide the fastest experience possible. There are many tasks that go into creating this experience, one of them being Gzip compression.

## GZIP Compression

Gzip enables HTTP compression by compressing most file types. Compressing files using Gzip has proven to reduce files sizes up to 70%! Most browsers support Gzip and it&#8217;s extremely simple to set-up. The code below can be copied and pasted into your <i class="code-term">.htaccess file</i> which is located in the root folder of your project.

## For Apache Servers 1.3 up to 2.0

    <ifModule mod_gzip.c>
    mod_gzip_on Yes
    mod_gzip_dechunk Yes
    mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
    mod_gzip_item_include handler ^cgi-script$
    mod_gzip_item_include mime ^text/.*
    mod_gzip_item_include mime ^application/x-javascript.*
    mod_gzip_item_exclude mime ^image/.*
    mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
    </ifModule>

## For Apache Servers 2.0 and above

    <IfModule mod_filter.c>
            AddOutputFilterByType DEFLATE "application/atom+xml" \
                                          "application/javascript" \
                                          "application/json" \
                                          "application/ld+json" \
                                          "application/manifest+json" \
                                          "application/rdf+xml" \
                                          "application/rss+xml" \
                                          "application/schema+json" \
                                          "application/vnd.geo+json" \
                                          "application/vnd.ms-fontobject" \
                                          "application/x-font-ttf" \
                                          "application/x-javascript" \
                                          "application/x-web-app-manifest+json" \
                                          "application/xhtml+xml" \
                                          "application/xml" \
                                          "font/eot" \
                                          "font/opentype" \
                                          "image/bmp" \
                                          "image/svg+xml" \
                                          "image/vnd.microsoft.icon" \
                                          "image/x-icon" \
                                          "text/cache-manifest" \
                                          "text/css" \
                                          "text/html" \
                                          "text/javascript" \
                                          "text/plain" \
                                          "text/vcard" \
                                          "text/vnd.rim.location.xloc" \
                                          "text/vtt" \
                                          "text/x-component" \
                                          "text/x-cross-domain-policy" \
                                          "text/xml"
        </IfModule>

## For Nginx Servers

    gzip on;
    gzip_buffers 16 8k;
    gzip_comp_level 2;
    gzip_min_length 1100;
    gzip_http_version 1.0;
    gzip_proxied any;
    gzip_types text/plain text/html text/css application/x-javascript text/xml application/xml application/xml+rss text/javascript;
    # Disable for IE < 6 due to compatibility issues
    gzip_disable "MSIE [1-6].(?!.*SV1)";
    gzip_vary on;

Gzip is a standard practice for websites but it's not uncommon to see websites that don’t use this great tool. Your just a <i class="code-term">Ctrl+C</i> and <i class="code-term">Ctrl+V</i> away from starting to see some major performance improvements.

## Gzip Resources

  * <a href="https://en.wikipedia.org/wiki/Gzip" target="_blank">Gzip</a>
  * <a href="https://developers.google.com/speed/docs/insights/EnableCompression" target="_blank">Google's Enable Compression</a>
  * <a href="https://varvy.com/pagespeed/enable-compression.html" target="_blank">Varvy's Enable Gzip compression</a>