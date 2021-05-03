---
layout: use-case
title: "Create your own widget"
---

<p>
    You can use WOWidget to turn any website into a widget.<br>
    If you already have your own website, simply open it in the WOWidget app.<br>
    If you have a <a href="/use-case/json-xml">JSON or XML feed</a>, you can open it using the WOWidget and use the built-in field editor to select the fields that interest you.<br>
    If you don't have a website ready, you can easily create one.
</p>

<h2>Template</h2>
<pre>
    &#x3C;!DOCTYPE html&#x3E;
    &#x3C;html lang=&#x22;en&#x22;&#x3E;
    &#x3C;head&#x3E;
        &#x3C;meta charset=&#x22;utf-8&#x22;&#x3E;
        &#x3C;!-- Title tag will be parsed as widget name. --&#x3E;
        &#x3C;title&#x3E;Widget name&#x3C;/title&#x3E;
        &#x3C;!-- Ensure proper and consistent scaling. --&#x3E;
        &#x3C;meta name=&#x22;viewport&#x22; content=&#x22;width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0&#x22;&#x3E;
        &#x3C;!-- Prevent iOS from changing numbers to clickable links. --&#x3E;
        &#x3C;meta name=&#x22;format-detection&#x22; content=&#x22;telephone=no&#x22;&#x3E;
        &#x3C;style&#x3E;
            /* Transparent background. */
            html, body { background: transparent; }
            /* Remove the default spacing. */
            html, body { margin: 0; padding: 0; }
            /* Disable user selection. */
            * { user-select: none; }
            /* Style for dark mode. Dark mode does not affect widgets. */
            @media (prefers-color-scheme: dark) {}
        &#x3C;/style&#x3E;
    &#x3C;/head&#x3E;
    &#x3C;body&#x3E;
        Widget content.
    &#x3C;/body&#x3E;
    &#x3C;/html&#x3E;
</pre>

<h2>Dimensions</h2>
<p>
    Widget dimensions vary depending on the iPad and iPad model. See a <a href="/blog/2020-05-28-dimensions">summary of widget screen dimensions</a>.
</p>

<h2>Meta tags</h2>
<p>
    WOWidget sends the following meta tags with the initial request:
</p>
<dl>
    <dt>X-width</dt>
    <dd>Widget width.</dd>

    <dt>X-min-height</dt>
    <dd>Minimum widget height.</dd>

    <dt>X-max-height</dt>
    <dd>Maximum widget height.</dd>

    <dt>X-version</dt>
    <dd>Widget version.</dd>
</dl>
<p>
    ⚠️ JavaScript requests do not send any additional meta tags.
</p>

<h2>Security</h2>
<p>
    If possible, always use an <var>https</var> connection.<br>
    You can use a URL with a token as authentication.<br>
    ⚠️ Safari does not support basic access authentication in URL.<br>
    ⚠️ WOWidget does not support states.<br>
</p>

<h2>Distribution</h2>
<p>
    You can share any widget directly from the app.<br>
    You can also programmatically create a <a href="/blog/2020-06-08-share-url-scheme.html">share url</a>.<br>
    There is also a <a href="/tools/share-url">tool for creating a share URL</a>.
</p>

<h2>Limitations</h2>
<p>
    ⚠️ iOS has a bug that prevents any website from loading on the lock screen. WOWidget regularly takes snapshots of active widgets and displays them as a fallback on the lock screen.
</p>
