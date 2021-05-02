---
layout: post
title: "WOWidget share url scheme"
---

<style>
    code {
        background: #e4e6e8;
    }
    ruby {
        font-size: 3em;
    }
    ruby > span {
        padding: 0 .5em;
    }
</style>

<p>
    WOWidget share feature allows users to export/import pre-configured widgets.
</p>

<h2>Technical details</h2>

<p>
    The share url consists of <code>https://www.wowidget.com/share</code> and base64 encoded parameters.<br>
    Base64 is used to hide (not encrypt) your shared URL.<br>
    iOS makes the URL invalid (cuts out part of the URL) if any of the URL part is longer than 301 characters. Therefore base64 data are split by a <a href="https://en.wikipedia.org/wiki/Hyphen" target="_blank">hyphen</a> character into 301 long chunks.
</p>

<h2>Parameters</h2>
<p>
    The order of the parameters does not matter. Parameters are joined with a <a href="https://en.wikipedia.org/wiki/Vertical_bar" target="_blank">vertical bar</a> character and string values are <a href="https://developer.apple.com/documentation/foundation/nsstring/1411946-addingpercentencoding" target="_blank">percent-encoded</a> as <code>"value".addingPercentEncoding(withAllowedCharacters: .alphanumerics)</code>. JavaScript <a href="https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent" target="_blank">encodeURIComponent</a> can also be used.
</p>
<dl>
    <dt><var>u</var></dt>
    <dd>Valid url. Percent-encoded string.</dd>

    <dt><var>n</var></dt>
    <dd>Name, title. Percent-encoded string.

    <dt><var>t</var></dt>
    <dd>Type of content. Number (<a href="#types">see below</a>).</dd>

    <dt><var>s</var></dt>
    <dd>Slot. Number between 1 and 5 included.</dd>

    <dt><var>c</var></dt>
    <dd><i>Optional</i> config. Percent-encoded json string. (<a href="#config">see below</a>).</dd>
</dl>

<h2 id="types">Type</h2>
<dl>
    <dt><var>1</var></dt>
    <dd>html</dd>

    <dt><var>2</var></dt>
    <dd>json</dd>

    <dt><var>3</var></dt>
    <dd>xml</dd>

    <dt><var>4</var></dt>
    <dd>image</dd>
</dl>

<h2 id="config">Config</h2>
<p>
    Config is represented as a JSON object. Config is optional and depends on the <var>type</var>. The order of the values in config does not matter.
</p>

<h2 id="config-html">HTML config</h2>
<dl>
    <dt><var>origin</var></dt>
    <dd>Scroll to coordinates <code>[x, y]</code> as floats.</dd>

    <dt><var>height</var></dt>
    <dd>Widget height as float (see <a href="/blog/2020-05-28-dimensions">screen dimensions</a>).</dd>

    <dt><var>zoom</var></dt>
    <dd>Zoom level. Float between 1 and 10 included.</dd>

    <dt><var>javascript</var></dt>
    <dd>Bool. Indicating if JavaScript is enabled.</dd>

    <dt><var>allowInteraction</var></dt>
    <dd>Bool. Indicating if user interaction (clicking on links) is enabled.</dd>

    <dt id="html-config-background"><var>background</var></dt>
    <dd>
        Background color. 4 hexadecimal numbers representing red, green, blue, alpha:<br>
        <ruby>
            <span style="color:#f00;">EF</span>
            <rp>(</rp><rt>Red</rt><rp>)</rp>
            
            <span style="color:#0f0;">D5</span>
            <rp>(</rp><rt>Green</rt><rp>)</rp>

            <span style="color:#00f;">00</span>
            <rp>(</rp><rt>Blue</rt><rp>)</rp>

            <span>FF</span>
            <rp>(</rp><rt>Alpha</rt><rp>)</rp>

            =

            <span style="color:#EFD500FF;">EFD500FF</span>
            <rp>(</rp><rt>Yellow</rt><rp>)</rp>
        </ruby>
    </dd>
</dl>

<h2>HTML config example</h2>
<pre>
    {
        "zoom": 1.11,
        "allowInteraction": false,
        "javascript": true,
        "height": 238.5,
        "origin": [0, 333.33333333333333],
        "background": "EFD500FF"
    }
</pre>


<h2>Image config</h2>
<p>
    Same as <a href="#config-html">HTML config</a>.
</p>

<h2 id="config-json">JSON config</h2>
<dl>
    <dt><var>fields</var></dt>
    <dd>Array of <var>Field</var>s</dd>
</dl>

<h3>Field</h3>
<dl>
    <dt><var>label</var></dt>
    <dd>String. If empty, than the last string item of the path will be used.</dd>

    <dt><var>path</var></dt>
    <dd>Array. Consists of strings (key names) and numbers (array indexes). If empty, than the first value found in object (JSON or XML) will be used.</dd>

    <dt><var>background</var></dt>
    <dd>Background color (see <a href="#html-config-background">HTML config background</a>)</dd>
</dt>

<h2>JSON config example</h2>
<pre>
    {
        "fields": [
            {
                "label": "Name of field",
                "path": ["Path", "to", 1, "field"],
                "background": "EFD500FF"
            },
            {
                "label": "",
                "path": [],
                "background": "00000000"
            },
            {
                "label": "Emoji",
                "path": ["Emoji"],
                "background": "F0F0F0F0"
            }
        ]
    }
</pre>

<h2>XML config</h2>

<p>
    Same as <a href="#config-json">JSON config</a>.
</p>

<h2>Share url example</h2>
<ol>
    <li>
        Input:
        <ul>
            <li><var>u</var> = https://www.wowidget.com</li>
            <li><var>n</var> = WOWidget 😀</li>
            <li><var>t</var> = html</li>
            <li><var>s</var> = 1</li>
            <li>
                <var>c</var> = {"allowInteraction":false,"background":"EFD500FF","height":300,"javascript":true,"origin":[0,0],"zoom":1}
                <ul>
                    <li><var>allowInteraction</var> = false</li>
                    <li><var>background</var> = EFD500FF</li>
                    <li><var>height</var> = 300</li>
                    <li><var>javascript</var> = true</li>
                    <li><var>origin</var> = [0, 0]</li>
                    <li><var>zoom</var> = 1</li>
                </ul>
            </li>
        </ul>
    </li>
    <li>
        Percent-encoding:
        <ul>
            <li><var>u</var> = https%3A%2F%2Fwww%2Ewowidget%2Ecom</li>
            <li><var>n</var> = WOWidget%20%F0%9F%98%80</li>
            <li><var>t</var> = 1</li>
            <li><var>s</var> = 1</li>
            <li>
                <var>c</var> = %7B%22allowInteraction%22%3Afalse%2C%22background%22%3A%22EFD500FF%22%2C%22height%22%3A300%2C%22javascript%22%3Atrue%2C%22origin%22%3A%5B0%2C0%5D%2C%22zoom%22%3A1%7D
            </li>
        </ul>
    </li>
    <li>
        Concatenation:<br>
        <code>u=https%3A%2F%2Fwww%2Ewowidget%2Ecom|n=WOWidget%20%F0%9F%98%80|t=1|s=1|c=%7B%22allowInteraction%22%3Afalse%2C%22background%22%3A%22EFD500FF%22%2C%22height%22%3A300%2C%22javascript%22%3Atrue%2C%22origin%22%3A%5B0%2C0%5D%2C%22zoom%22%3A1%7D</code>
    </li>
    <li>
        Base64 encoding:<br>
        <code>dT1odHRwcyUzQSUyRiUyRnd3dyUyRXdvd2lkZ2V0JTJFY29tfG49V09XaWRnZXQlMjAlRjAlOUYlOTglODB8dD0xfHM9MXxjPSU3QiUyMmFsbG93SW50ZXJhY3Rpb24lMjIlM0FmYWxzZSUyQyUyMmJhY2tncm91bmQlMjIlM0ElMjJFRkQ1MDBGRiUyMiUyQyUyMmhlaWdodCUyMiUzQTMwMCUyQyUyMmphdmFzY3JpcHQlMjIlM0F0cnVlJTJDJTIyb3JpZ2luJTIyJTNBJTVCMCUyQzAlNUQlMkMlMjJ6b29tJTIyJTNBMSU3RA==</code>
    </li>
    <li>
        Split data into 301 long chunks separated by a hyphen.<br>
        <code>dT1odHRwcyUzQSUyRiUyRnd3dyUyRXdvd2lkZ2V0JTJFY29tfG49V09XaWRnZXQlMjAlRjAlOUYlOTglODB8dD0xfHM9MXxjPSU3QiUyMmFsbG93SW50ZXJhY3Rpb24lMjIlM0FmYWxzZSUyQyUyMmJhY2tncm91bmQlMjIlM0ElMjJFRkQ1MDBGRiUyMiUyQyUyMmhlaWdodCUyMiUzQTMwMCUyQyUyMmphdmFzY3JpcHQlMjIlM0F0cnVlJTJDJTIyb3JpZ2luJTIyJTNBJTVCMCUyQzAlNUQlMkMlMjJ6<mark>-</mark>b29tJTIyJTNBMSU3RA==</code>
    </li>
    <li>
        Final share url:<br>
        <a href="https://www.wowidget.com/share?dT1odHRwcyUzQSUyRiUyRnd3dyUyRXdvd2lkZ2V0JTJFY29tfG49V09XaWRnZXQlMjAlRjAlOUYlOTglODB8dD0xfHM9MXxjPSU3QiUyMmFsbG93SW50ZXJhY3Rpb24lMjIlM0FmYWxzZSUyQyUyMmJhY2tncm91bmQlMjIlM0ElMjJFRkQ1MDBGRiUyMiUyQyUyMmhlaWdodCUyMiUzQTMwMCUyQyUyMmphdmFzY3JpcHQlMjIlM0F0cnVlJTJDJTIyb3JpZ2luJTIyJTNBJTVCMCUyQzAlNUQlMkMlMjJ6-b29tJTIyJTNBMSU3RA==" target="_blank">https://www.wowidget.com/share?dT1odHRwcyUzQSUyRiUyRnd3dyUyRXdvd2lkZ2V0JTJFY29tfG49V09XaWRnZXQlMjAlRjAlOUYlOTglODB8dD0xfHM9MXxjPSU3QiUyMmFsbG93SW50ZXJhY3Rpb24lMjIlM0FmYWxzZSUyQyUyMmJhY2tncm91bmQlMjIlM0ElMjJFRkQ1MDBGRiUyMiUyQyUyMmhlaWdodCUyMiUzQTMwMCUyQyUyMmphdmFzY3JpcHQlMjIlM0F0cnVlJTJDJTIyb3JpZ2luJTIyJTNBJTVCMCUyQzAlNUQlMkMlMjJ6-b29tJTIyJTNBMSU3RA==</a>
    </li>
</ol>

<h2>Tools</h2>

<ul>
    <li><a href="/tools/share-url">WOWidget share url encoder</a></li>
    <li><a href="https://www.base64decode.org/" target="_blank">Base64 decoder</a></li>
    <li><a href="https://www.urldecoder.org/" target="_blank">Url encoder</a></li>
</ul>

