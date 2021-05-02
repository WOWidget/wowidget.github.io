---
layout: default
---

<div id="hero">
    <div id="fold">
        <h1>
            <span>Turn any</span>
            <span class="hero-color">website into</span>
            <span>a widget</span>
        </h1>

        <p>
            WOWidget is a FREE application for iPhone and iPad to create custom widgets.<br>
            Or simply put: A web browser in a widget.
        </p>
        <p>
            <a href="https://apps.apple.com/app/apple-store/id1515009616?pt=314498&ct=Website&mt=8" target="_blank"><img src="https://wowidget.github.io/images/app-store.png" alt="Download WOWidget from App Store" width="248" height="83"></a>
        </p>
    </div>
    <script>
        const cssVar = name => getComputedStyle(document.documentElement).getPropertyValue(name).trim();
        document.getElementById("fold").style.minHeight = window.innerHeight - parseInt(cssVar("--header-height"), 10) - parseInt(cssVar("--padding"), 10) + "px";
    </script>
</div>
    
<h2>Why <small>should I use it</small></h2>
<ul>
    <li>You need fresh information and want to see it within a widget.</li>
    <li>One universal app to replace many single-purpose apps. See <a href="/use-case">use cases</a>.</li>
    <li>Do not waste time and money developing your own app, connect <a href="/use-case/custom">your website</a> instead.</li>
    <li>Easy to turn any website into a widget from <a href="/pages/safari-share-extension">Safari</a>.</li>
    <li>Supported languages: English 🇺🇸🇬🇧, Français 🇫🇷, Deutsche 🇩🇪, Español 🇪🇸, Slovenčina 🇸🇰, Čeština 🇨🇿.</li>
    <li>iCloud backups and syncing between devices.</li>
    <li>No ads. No subscription. No in-app purchases. No tracking.</li>
</ul>

<h2>How <small>can I use it</small></h2>
<ol>
    <li>Download WOWidget from the <a href="https://apps.apple.com/app/apple-store/id1515009616?pt=314498&ct=Website&mt=8" target="_blank">App Store</a>.</li>
    <li>Watch <a href="https://www.youtube.com/playlist?list=PL67akN97t0MuqzpTjMB7IR9tg02yDGRPN" target="_blank">tutorial videos</a>.</li>
    <li>Check out <a href="/use-case">use cases</a>.</li>
</ol>

<h2>Who <small>made it</small></h2>
<p>
    <a href="https://www.michalgondar.com/" target="_blank">Michal Gondar</a> aka <a href="https://twitter.com/gondo" target="_blank">@gondo</a>.
</p>
<br>

{% comment %}
<!--
<a href="https://news.ycombinator.com/item?id=23541051" target="_blank"><img src="https://wowidget.github.io/images/hacker-news.png" alt="Hacker news" width="289" height="83"></a>
-->
{% endcomment %}

<p>
    <img src="/images/endorsement.png" width="430" height="129" alt="The best widget app." style="display:inline-block;max-width:327px;width:100%;height:auto;border-radius:15px;vertical-align:top;">
    <a href="https://www.producthunt.com/posts/wowidget/" target="_blank"><img src="https://wowidget.github.io/images/product-hunt.png" alt="Product hunt" width="327" height="83" style="max-width:327px;width:100%;height:auto;"></a>
</p>
