---
layout: post
title: "Recording preview video for App Store"
---

<h2>Video specifications</h2>
<ul>
    <li>
        Accepted dimensions:
        <ul>
            <li>iPhone 6.5 inch: 886 x 1920</li>
            <li>iPhone 5.5 inch: 1080 x 1920</li>
            <li>iPad 12.9 inch: 1200 x 1600</li>
        </ul>
    </li>
    <li>Min length: 15 seconds</li>
    <li>Max length: 30 seconds</li>
    <li>Max file size: 500MB</li>
    <li>Must include audio (even if it is silent)</li>
    <li>Upload <dfn style="cursor:help;" title="Most of the time it doesn't work at all 😠">works</dfn> only in Safari</li>
</ul>
<p>
    Source: <a href="https://help.apple.com/app-store-connect/#/dev4e413fcb8" target="_blank">App Store Connect Help</a>.
</p>

<h2>Recording</h2>

<h3>Cursor</h3>
<p>
    Change MacOS default arrow pointer cursor.
</p>
<ul>
    <li>Download and run <a href="https://github.com/alexzielenski/Mousecape/releases/download/0.0.5/Mousecape.zip">Mousecape v 0.0.5</a></li>
    <li>Mousecape → Install Helper Tool (can be uninstalled later)</li>
    <li>Download WOWidget <a href="/assets/2020-06-01/com.wowidget.cape">config</a>, also called <i>cape</i></li>
    <li>Import <i>cape</i> into Mousecape: File → Import Cape</li>
    <li>Double click to activate</li>
    <li>To deactivate simply delete <i>cape</i></li>
</ul>
<p>
    Source: <a href="https://github.com/alexzielenski/Mousecape" target="_blank">Mousecape GitHub</a>
</p>

<h3>Xcode Simulator</h3>
<ul>
    <li>Run Xcode Simulator</li>
    <li>Window → Show Device Bezels: Off 🔴</li>
    <li>Window → Point Accurate: On ✅</li>
    <li>
        Simulator → Preferences
        <ul>
            <li>Show single touches: On ✅</li>
            <li>Show pinch gestures: On ✅</li>
        </ul>
    </li>
</ul>

<h3>QuickTime Player</h3>
<ul>
    <li>Start Xcode Simulator</li>
    <li>Start QuickTime Player</li>
    <li>File → New Screen Recording</li>
    <li>Choose: Record Selected Portion</li>
    <li>
        Options:
        <ul>
            <li>Timer: None</li>
            <li>Microphone: None</li>
            <li>
                Options:
                <ul>
                    <li>Show Floating Thumbnail: Off 🔴</li>
                    <li>Remember Last Selection: On ✅</li>
                    <li>Show Mouse Clicks: Off 🔴</li>
                </ul>
            </li>
        </ul>
    </li>
    <li>
        Resize Selected Portion:
        <ul>
            <li>iPhone 6.5 inch: 414 x 897</li>
            <li>iPhone 5.5 inch: 414 x 736</li>
            <li>iPad 12.9 inch: 726 x 968</li>
        </ul>
    </li>
    <li>To start, click Record</li>
    <li>To stop recording, click the Stop Recording button in the menu bar</li>
</ul>
<p>
    Source: <a href="https://support.apple.com/en-gb/guide/quicktime-player/qtp97b08e666/mac" target="_blank">QuickTime Player User Guide</a>
</p>

<h3>Audio</h3>
<p>
    App Store Preview requires audio, even if it is silent.
    Download <a href="https://github.com/anars/blank-audio/raw/master/1-second-of-silence.mp3" target="_blank">one second of silence</a>.
</p>

<h3>Editing</h3>
<p>
    Use <a href="https://www.apple.com/final-cut-pro/trial/" target="_blank">Final Cut Pro X Trial</a>.<br>
    iMovie does not support custom resolutions.
</p>

<h2>Result</h2>
<iframe width="295" height="640" src="https://www.youtube-nocookie.com/embed/M4kmUnK_hHQ?controls=0&rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

