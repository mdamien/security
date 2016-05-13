Firefox v46+ Security Hardening + Some Tweaks

* Useful Plugins
 * uBlock Origin by [Raymond Hill](https://github.com/gorhill) ( [GitHub](https://github.com/gorhill/uBlock/) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) )
 * NoScript Security Suite by [Giorgio Maone](https://maone.net/) ( [Site](https://noscript.net/) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/noscript/) )
 * RequestPolicy by [Justin Samuel](https://justinsamuel.com/) ( [Site](https://www.requestpolicy.com) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/) )
 * Random Agent Spoofer by [dillbyrne](https://dillbyrne.github.io/) ( [GitHub](https://github.com/dillbyrne/random-agent-spoofer) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/random-agent-spoofer/) )

Copy paste these settings in `user.js` (`~/.mozilla/firefox/<profile>.default/user.js` on linux) to override the defaults.

```javascript
// Disable "Weak SSL" ( [Test SSL](https://www.howsmyssl.com/) )
user_pref("security.ssl3.dhe_rsa_aes_128_sha", false); //(default: true)*
user_pref("security.ssl3.dhe_rsa_aes_256_sha", false); //(default: true)*
user_pref("security.ssl3.rsa_rc4_128_md5", false); //(default: true)*
user_pref("security.ssl3.rsa_rc4_128_sha", false); //(default: true)*
user_pref("security.ssl3.rsa_des_ede3_sha", false); //(default: true)*
user_pref("security.ssl3.ecdhe_rsa_rc4_128_sha", false); //(default: true)*
user_pref("security.ssl3.ecdhe_ecdsa_rc4_128_sha", false); //(default: true)*

// Perfect Forward Secrecy //(some sites may not work)*
user_pref("security.ssl3.rsa_aes_256_sha", false); //(default: true)*

// "Force TLS 1.2"
user_pref("security.tls.version.min", 3); //(default: 1)*

// Crypto Hardening
user_pref("security.OCSP.require", true); //(default: false)*
user_pref("security.ssl.require_safe_negotiation", true); //(default: false)*
user_pref("security.ssl.treat_unsafe_negotiation_as_broken", true); //(default: false)*

// Disable "Hello"
user_pref("loop.enabled", false); //(default: true)*

// Disable "Pocket"
user_pref("extensions.pocket.enabled", false); //(default: true)*

// Disable "Reader"
user_pref("reader.parse-on-load.enabled", false); //(default: true)*

// Disable "Sync Services"
user_pref("services.sync.enabled", false); //(default: true)*
user_pref("services.sync.sendVersionInfo", false); //(default: true)*
user_pref("services.sync.migrated", false); // (all other false)
// TODO: disable sync of ublock filters ?

// Disable "Sponsored Content"
user_pref("browser.newtabpage.directory.source", ""); //(default: https://tiles.services.mozilla.com/v3/links/fetch/%LOCALE%/%CHANNEL%)*
user_pref("browser.newtabpage.directory.ping", ""); //(default: https://tiles.services.mozilla.com/v3/links/)*

// Disable "WebSockets"
user_pref("network.websocket.enabled", false); //(default: none)// *create new boolean*

// Referer Control
user_pref("network.http.sendRefererHeader", 0); //(default: 2)*
  // 0 = disable completely
  // 1 = send referer on link click
  // 2 = always send
user_pref("network.http.referer.XOriginPolicy", 1); //(default: 0)*
  // 0 = always send
  // 1 = only on domain match
user_pref("network.http.referer.spoofSource", true); //(default: false)// //(send target uri)*
user_pref("network.http.referer.trimmingPolicy", 2); //(default: 0)*
  // 0 = full
  // 1 = scheme
  // 2 = host port and path

// Enable "Do Not Track"
user_pref("privacy.donottrackheader.enabled", true); //(default: false)*

// Disable "Geolocation"
user_pref("geo.enabled", false); //(default: true)*
user_pref("browser.search.geoSpecificDefaults", false); //(default: true)*
user_pref("geo.wifi.uri", ""); //(default: https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_API_KEY%)*
user_pref("browser.geolocation.warning.infoURL", ""); //(default: https://www.mozilla.org/%LOCALE%/firefox/geolocation/)*
user_pref("browser.search.geoSpecificDefaults.url", ""); //(default: https://search.services.mozilla.com/1/%APP%/%VERSION%/%CHANNEL%/%LOCALE%/%REGION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%)*
user_pref("browser.search.geoip.url", ""); //(default: https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%)*

// Disable "Beacons"
user_pref("beacon.enabled", false); //(defualt: true)*

// Disable "Browser Pings"
user_pref("browser.send_pings", false); //(default)*

// Disable "Health Reports"
user_pref("datareporting.healthreport.uploadEnabled", false); //(default: true)*
user_pref("datareporting.policy.dataSubmissionEnabled", false); //(default: true)*

// Disable "Telemetry Reports*
user_pref("toolkit.telemetry.enabled", false); //(default)*
user_pref("toolkit.telemetry.unified", false); //(default: true)*
user_pref("toolkit.telemetry.archive.enabled", false); //(default: true)*
user_pref("toolkit.telemetry.optoutSample", false); //(default: true)*
user_pref("toolkit.telemetry.server", ""); //(default: https://incoming.telemetry.mozilla.org)*
user_pref("experiments.manifest.uri", ""); //(default: https://telemetry-experiment.cdn.mozilla.net/manifest/v1/firefox/%VERSION%/%CHANNEL%)*

// Disable "Browser Session Restore"
user_pref("browser.sessionstore.restore_on_demand", false); //(default: true)*
user_pref("browser.sessionstore.resume_from_crash", false); //(default: true)*

// Disable "PDF Viewer"
user_pref("pdfjs.disabled", true); //(default: false)*

// Disable "DRM Video"
user_pref("media.eme.enabled", false); //(default: true)*

// Disable "WebGL"
user_pref("webgl.disabled", true); //(default: false)*

// Disable "JavaScript"
user_pref("javascript.enabled", true); //(default: false)*

// Disable "Battery Manager"
user_pref("dom.battery.enabled", false); //(default: true)*

// Disable "Link Pre-Fetching"
user_pref("network.http.speculative-parallel-limit", 0); //(default: 6)*

// Disable "WebRTC"
user_pref("media.peerconnection.enabled", false); //(default: true)*
user_pref("media.peerconnection.simulcast", false); //(default: true)*
user_pref("media.peerconnection.turn.disable", true); //(default: false)*
user_pref("media.peerconnection.identity.enabled", false); //(default: true)*
user_pref("media.peerconnection.use_document_iceservers", false); //(default: true)*
user_pref("media.peerconnection.video.enabled", false); //(default: true)*

// Disable "Safe Browsing"
user_pref("browser.safebrowsing.enabled", false); //(default: true)*
user_pref("browser.safebrowsing.downloads.enabled", false); //(default: true)*
user_pref("browser.safebrowsing.malware.enabled", false); //(default: true)*

// Disable "Social Media Integration"
user_pref("social.remote-install.enabled", false); //(default: true)*
user_pref("social.toast-notifications.enabled", false); //(default: true)*
user_pref("social.directories", ""); //(default: https://activations.cdn.mozilla.net)*
user_pref("social.whitelist", ""); //(default: https://mozsocial.cliqz.com)*

// Enable "SOCKS Remote DNS"
user_pref("network.proxy.socks_remote_dns", true); //(default: false)*

// Disable "IPv6"
user_pref("network.dns.disableIPv6", true); //(default: false)*

// Disable "Camera Face Detection"
user_pref("camera.control.face_detection.enabled", false); //(default: true)*

// Disable "Device Statistics"
user_pref("device.sensors.enabled", false); //(default: true)*

// Enable "Tracking" Protection
user_pref("privacy.trackingprotection.enabled", true); //(default: false)*

// Disable "Browser Disk Cache"
user_pref("browser.cache.disk.enable", false); //(default: true)*

// Disable "Remote WiFi Scan"
user_pref("devtools.remote.wifi.scan", false); //(default: true)*

// Disable "Domain Guessing"
user_pref("browser.fixup.alternate.enabled", false); //(default: true)*

// Disable "Search Suggestion"
user_pref("browser.search.suggest.enabled", false); //(default: true)*

// Disable "Address Bar Search"
user_pref("keyword.enabled", false); //(default: true)*

// Enable "http://" Prefix
user_pref("browser.urlbar.trimURLs", false); //(default: true)*

// Disable "Clipboard DOM Events"
user_pref("dom.event.clipboardevents.enabled", false); //(default: true)*

// Prevent "Context Menu Disable"
user_pref("dom.event.contextmenu.enabled", false); //(default: true)*

// Prevent "Browser AutoRefresh"
user_pref("accessibility.blockautorefresh", true); //(default: false)*

// Enable "Advanced Color Profile Support"
user_pref("gfx.color_management.enablev4", true); //(default: false)*
 
// Disable "Download History"
user_pref("browser.download.manager.addToRecentDocs", false); //(default: true)*

// Disable "Download Logs"
user_pref("browser.download.loglevel", ""); //(default: Error)*

// Disable "Download Notifications"
user_pref("browser.download.animateNotifications", false); //(default: true)*

// "View Source Code In External Editor"
// user_pref("view_source.editor.external", true); //(default: false)*
// user_pref("view_source.editor.path", "your editor path"); //(default: empty)*
```

Related Links:
 * [All "about:config" Options](https://hg.mozilla.org/mozilla-central/raw-file/3461f3cae78495f100a0f7d3d2e0b89292d3ec02/modules/libpref/init/all.js)
 * [Arch Firefox Tweaks](https://wiki.archlinux.org/index.php/Firefox_tweaks)
 * [Firefox Bullshit Removal](https://gist.github.com/haasn/69e19fc2fe0e25f3cff5)
