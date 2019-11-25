# DRM

* What is DRM / Why?
  * Protect content from being misused / easily downloaded in its "raw" quality.
  * Requirements from content owners
    * Usually different requirements based on the type of content
    * Video stricter than audio
    * 8K/4K stricter than SD
    * "Hollywood grade" usually strict requirements.
  * How?
    * Encrypt the content so it can't easily be downloaded
    * Provide a secure/obfuscated way of transfering encryption keys needed to decrypt the content
* Standards
  * Common Encryption (CENC)
  * Encrypted Media Extensions (EME)
* Actors
  * CDM
  * License server
  * Key server
  * Content / On the fly packager
* DRM
  * Systems
    * Widevine (Google)
    * PlayReady (Microsoft)
    * Fairplay (Apple)
  * Other stuff
    * A device often supports only one DRM system
      * This means that you usually need to support all the major DRM providers in backend to be able to reach the devices you want.
    * Different levels of security L1-L3, Software vs Hardware
      * Decryption vs Decryption and decoding in protected environment
        * => Higher levels of protection require codec support in the DRM system
      * Different levels can be specified by the license server so it can require content to only play on compliant devices
    * Offline support
      * Some systems supports offline protection with things like expiry etc.
  * Works by having a obfuscated software on the client (software drm)  and trusted execution environment (TEE) in the hardware (hardware drm)
* General architecture
  * Storage
  * On the fly packager
  * Key server
  * License server
    * Different implementations
      * Proxy requests to provider
        * Widevine
      * Host and implement server with library from the provider
        * PlayReady
      * Implement the spec
        * Fairplay
  * Device
    * CDM
* Technical solutions
  * Store files encrypted with a fixed key(s)
    * What if key is found? Need to reencrypt the content
    * Need different renditions stored with cenc and cbcs if apple => 2x storage cost
  * On the fly packaging
    * Store files in a unencrypted mezzanine format
    * On the fly apply encryption to segments
    * Stored in the CDN
    * => Simple to change keys if broken
    * => Cheaper storage cost
    * => More flexible
* Things to think about
  * CENC vs CBCS
    * Need to store double the content or compete in the CDN
  * When things are broken, what to do?
    * Depends on drm system
      * Widevine was broken in 2019, but it was just a client and server update, and things were back to normal
        * This is probably different if are actually implementing widevine on HW instead of using their servers
      * If PlayReady is broken the library needs to be distributed to the people implementing it and they then need to upgrade and redeploy their service
* **TODO**
  * Figure out terminology
    * Provider (Provider is a service that implements DRM systems?)
    * System (The actual technology?)
    * ...
  * Explain Common encryption
    * What is standardized
    * PSSH
  * "Multi-DRM"
    * Support multiple DRM systems for the same content
    * Common encryption in the file it self
      * => Much storage and contention in CDN
    * ... or on the fly packager for each type
      * => Less storage, but still contention in CDN
    * ... or same encrypted content, but different PSSH info in manifest (DASH)
      * => Less storage and same content in CDN
  * Explain EME
    * Browser features
  * Manifests
    * DASH - Embedded PSSH
    * HLS - Another way
  * Can use multiple keys for an asset
    * Change key over time
    * Different key per renditions
    * Both++
  * Different ways to encrypt content
    * How much of the samples are actually encrypted
      * Different ratios based on some guidelines?

## Links

* https://bitmovin.com/docs/encoding/articles/digital-rights-management-drm-overview
* https://bitmovin.com/whitepapers/DRM-State-of-Web-Bitmovin-2018.pdf
* https://www.encoding.com/digital-rights-management-drm/
* https://medium.com/@eyevinntechnology/securing-ott-content-drm-1af2c08fdd31
