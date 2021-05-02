---
layout: empty
title: "Share"
---

<p>
    Open <a id="link" href="wowidget://">WOWidget app</a> or download WOWidget:
</p>

<a href="https://apps.apple.com/app/apple-store/id1515009616?pt=314498&ct=Share&mt=8" target="_blank"><img src="/images/app-store.png" alt="Download WOWidget from App Store" width="250" height="83"></a>

<script>
    // window.addEventListener("focus", () => {
    //     clearTimeout(timer);
    // });

    // window.addEventListener("blur", () => {
    //     clearTimeout(timer);
    // });

    // window.addEventListener("visibilitychange", (e) => {
    //     if (e.target.visibilityState == "hidden") {
    //         clearTimeout(timer);
    //     }
    // });

    let base64separator = "-";
    if (window.location.search) {
        url = "wowidget://share/" + window.location.search.replace(base64separator, "");
    } else {
        url = "wowidget:/" + window.location.pathname.replace(base64separator, "");
    }
    document.getElementById("link").href = url;

    // let timer = setTimeout(function() {
    //     window.location = "https://apps.apple.com/app/apple-store/id1515009616?pt=314498&ct=Share&mt=8";
    // }, 100);
    window.location = url;
</script>
