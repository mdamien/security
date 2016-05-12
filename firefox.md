Firefox v46+ Security Hardening + Some Tweaks

* Useful Plugins
 * uBlock Origin by [Raymond Hill](https://github.com/gorhill) ( [GitHub](https://github.com/gorhill/uBlock/) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) )
 * NoScript Security Suite by [Giorgio Maone](https://maone.net/) ( [Site](https://noscript.net/) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/noscript/) )
 * RequestPolicy by [Justin Samuel](https://justinsamuel.com/) ( [Site](https://www.requestpolicy.com) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/) )
 * Random Agent Spoofer by [dillbyrne](https://dillbyrne.github.io/) ( [GitHub](https://github.com/dillbyrne/random-agent-spoofer) | [Addon](https://addons.mozilla.org/en-US/firefox/addon/random-agent-spoofer/) )

* Disable "Weak SSL" ( [Test SSL](https://www.howsmyssl.com/) )
 * ``security.ssl3.dhe_rsa_aes_128_sha = false`` *(default: true)*
 * ``security.ssl3.dhe_rsa_aes_256_sha = false`` *(default: true)*
 * ``security.ssl3.rsa_rc4_128_md5 = false`` *(default: true)*
 * ``security.ssl3.rsa_rc4_128_sha = false`` *(default: true)*
 * ``security.ssl3.rsa_des_ede3_sha = false`` *(default: true)*
 * ``security.ssl3.ecdhe_rsa_rc4_128_sha = false`` *(default: true)*
 * ``security.ssl3.ecdhe_ecdsa_rc4_128_sha = false`` *(default: true)*

* Perfect Forward Secrecy *(some sites may not work)*
 * ``security.ssl3.rsa_aes_256_sha = false`` *(default: true)*

* "Force TLS 1.2"
 * ``security.tls.version.min = 3`` *(default: 1)*

* Crypto Hardening
 * ``security.OCSP.require = true`` *(default: false)*
 * ``security.ssl.require_safe_negotiation = true`` *(default: false)*
 * ``security.ssl.treat_unsafe_negotiation_as_broken = true`` *(default: false)*

* Disable "Hello"
 * ``loop.enabled = false`` *(default: true)*

* Disable "Pocket"
 * ``extensions.pocket.enabled = false`` *(default: true)*

* Disable "Reader"
 * ``reader.parse-on-load.enabled = false`` *(default: true)*

* Disable "Sync Services"
 * ``services.sync.enabled = false`` *(default: true)*
 * ``services.sync.sendVersionInfo = false`` *(default: true)*
 * ``services.sync*`` (all other false)

* Disable "Sponsored Content"
 * ``browser.newtabpage.directory.source = ""`` *(default: https://tiles.services.mozilla.com/v3/links/fetch/%LOCALE%/%CHANNEL%)*
 * ``browser.newtabpage.directory.ping = ""`` *(default: https://tiles.services.mozilla.com/v3/links/)*

* Disable "WebSockets"
 * ``network.websocket.enabled = false`` *(default: none)* *create new boolean*

* Referer Control
 * ``network.http.sendRefererHeader = 0`` *(default: 2)*
  * 0 = disable completely
  * 1 = send referer on link click
  * 2 = always send
 * ``network.http.referer.XOriginPolicy = 1`` *(default: 0)*
  * 0 = always send
  * 1 = only on domain match
 * ``network.http.referer.spoofSource = true`` *(default: false)* *(send target uri)*
 * ``network.http.referer.trimmingPolicy = 2`` *(default: 0)*
  * 0 = full
  * 1 = scheme
  * 2 = host port and path

* Enable "Do Not Track"
 * ``privacy.donottrackheader.enabled = true`` *(default: false)*

* Disable "Geolocation"
 * ``geo.enabled = false`` *(default: true)*
 * ``browser.search.geoSpecificDefaults = false`` *(default: true)*
 * ``geo.wifi.uri = ""`` *(default: https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_API_KEY%)*
 * ``browser.geolocation.warning.infoURL = ""`` *(default: https://www.mozilla.org/%LOCALE%/firefox/geolocation/)*
 * ``browser.search.geoSpecificDefaults.url = ""`` *(default: https://search.services.mozilla.com/1/%APP%/%VERSION%/%CHANNEL%/%LOCALE%/%REGION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%)*
 * ``browser.search.geoip.url = ""`` *(default: https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%)*

* Disable "Beacons"
 * ``beacon.enabled = false`` *(defualt: true)*

* Disable "Browser Pings"
 * ``browser.send_pings = false`` *(default)*

* Disable "Health Reports"
 * ``datareporting.healthreport.uploadEnabled = false`` *(default: true)*
 * ``datareporting.policy.dataSubmissionEnabled = false`` *(default: true)*

* Disable "Telemetry Reports*
 * ``toolkit.telemetry.enabled = false`` *(default)*
 * ``toolkit.telemetry.unified = false`` *(default: true)*
 * ``toolkit.telemetry.archive.enabled = false`` *(default: true)*
 * ``toolkit.telemetry.optoutSample = false`` *(default: true)*
 * ``toolkit.telemetry.server = ""`` *(default: https://incoming.telemetry.mozilla.org)*
 * ``experiments.manifest.uri = ""`` *(default: https://telemetry-experiment.cdn.mozilla.net/manifest/v1/firefox/%VERSION%/%CHANNEL%)*

* Disable "Browser Session Restore"
 * ``browser.sessionstore.restore_on_demand = false`` *(default: true)*
 * ``browser.sessionstore.resume_from_crash = false`` *(default: true)*

* Disable "PDF Viewer"
 * ``pdfjs.disabled = true`` *(default: false)*

* Disable "DRM Video"
 * ``media.eme.enabled = false`` *(default: true)*

* Disable "WebGL"
 * ``webgl.disabled = true`` *(default: false)*

* Disable "JavaScript"
 * ``javascript.enabled = true`` *(default: false)*

* Disable "Battery Manager"
 * ``dom.battery.enabled = false`` *(default: true)*

* Disable "Link Pre-Fetching"
 * ``network.http.speculative-parallel-limit = 0`` *(default: 6)*

* Disable "WebRTC"
 * ``media.peerconnection.enabled = false`` *(default: true)*
 * ``media.peerconnection.simulcast = false`` *(default: true)*
 * ``media.peerconnection.turn.disable = true`` *(default: false)*
 * ``media.peerconnection.identity.enabled = false`` *(default: true)*
 * ``media.peerconnection.use_document_iceservers = false`` *(default: true)*
 * ``media.peerconnection.video.enabled = false`` *(default: true)*

* Disable "Safe Browsing"
 * ``browser.safebrowsing.enabled = false`` *(default: true)*
 * ``browser.safebrowsing.downloads.enabled = false`` *(default: true)*
 * ``browser.safebrowsing.malware.enabled = false`` *(default: true)*

* Disable "Social Media Integration"
 * ``social.remote-install.enabled = false`` *(default: true)*
 * ``social.toast-notifications.enabled = false`` *(default: true)*
 * ``social.directories = ""`` *(default: https://activations.cdn.mozilla.net)*
 * ``social.whitelist = ""`` *(default: https://mozsocial.cliqz.com)*

* Enable "SOCKS Remote DNS"
 * ``network.proxy.socks_remote_dns = true`` *(default: false)*

* Disable "IPv6"
 * ``network.dns.disableIPv6 = true`` *(default: false)*

* Disable "Camera Face Detection"
 * ``camera.control.face_detection.enabled = false`` *(default: true)*

* Disable "Device Statistics"
 * ``device.sensors.enabled = false`` *(default: true)*

* Enable "Tracking" Protection
 * ``privacy.trackingprotection.enabled = true`` *(default: false)*

* Disable "Browser Disk Cache"
 * ``browser.cache.disk.enable = false`` *(default: true)*

* Disable "Remote WiFi Scan"
 * ``devtools.remote.wifi.scan = false`` *(default: true)*

* Disable "Domain Guessing"
 * ``browser.fixup.alternate.enabled = false`` *(default: true)*

* Disable "Search Suggestion"
 * ``browser.search.suggest.enabled = false`` *(default: true)*

* Disable "Address Bar Search"
 * ``keyword.enabled = false`` *(default: true)*

* Enable "http://" Prefix
 * ``browser.urlbar.trimURLs = false`` *(default: true)*

* Disable "Clipboard DOM Events"
 * ``dom.event.clipboardevents.enabled = false`` *(default: true)*

* Prevent "Context Menu Disable"
 * ``dom.event.contextmenu.enabled = false`` *(default: true)*

* Prevent "Browser AutoRefresh"
 * ``accessibility.blockautorefresh = true`` *(default: false)*

* Enable "Advanced Color Profile Support"
 * ``gfx.color_management.enablev4 = true`` *(default: false)*
 
* Disable "Download History"
 * ``browser.download.manager.addToRecentDocs = false`` *(default: true)*

* Disable "Download Logs"
 * ``browser.download.loglevel = ""`` *(default: Error)*

* Disable "Download Notifications"
 * ``browser.download.animateNotifications = false`` *(default: true)*

* "View Source Code In External Editor"
 * ``view_source.editor.external = true`` *(default: false)*
 * ``view_source.editor.path = "your editor path"`` *(default: empty)*

Related Links:
 * [All "about:config" Options](https://hg.mozilla.org/mozilla-central/raw-file/3461f3cae78495f100a0f7d3d2e0b89292d3ec02/modules/libpref/init/all.js)
 * [Arch Firefox Tweaks](https://wiki.archlinux.org/index.php/Firefox_tweaks)
 * [Firefox Bullshit Removal](https://gist.github.com/haasn/69e19fc2fe0e25f3cff5)
