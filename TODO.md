# TODO 

* Glass to glass flow
  * Camera
  * Contribution encoders (low latency, maybe)
  * Encoder (possibly multiscreen / OTT)
  * Packager
  * CDN
  * Player
  * Screen
* Formats / Standards
  * CMAF
  * CENC
  * MP4 / fMP4
  * MPEG-TS
  * H264
  * AAC
    * Gapless
  * FLAC
* Ingestion
  * On demand content
    * Files
  * Live content
  * Encoding / Transcoding
* Storing content
  * Source file > Mezzanine > Deliverables
* Packaging
  * On the fly
    * Save storage cost
    * More dynamic to changes
    * Behind CDN, done on demand
  * Offline
    * Create static files
    * Done once
* Adaptive bitrate streaming (ABR)
  * Contiguous chunks
    * GOP sizes
    * File chunks
  * Bitrate latters
  * Bandwidth estimation algorithms
  * Audio and video sync
    * Different frame sizes can cause weird transitions
  * Per title / per shot encoding
* Manifests
  * HLS
  * DASH
  * Live versions: LHLS, LL-HLS
    * Lots of requests to CDN
  * Custom
* Serving content
  * CDNs
    * Signed URLs
    * Cache bustable URLs
    * How does it work
      * POPs
      * Shields
      * How does content stay in cache?
    * Edge compute
    * Utilization & performance
      * Same content on most devices / players
      * Time to first byte
        * Stream on miss
    * Zero rating traffic
* Live
  * Low latency / Ultra low latency
    * Glass to glass < X s
  * DVR window
    * How long a user can watch behind real time
    * Typically causes large manifests
  * LHLS
  * LL-HLS (apple)
  * DASH
* DRM
  * Concepts
  * Solutions
    * Widevine
    * PlayReady
    * Fairplay
* Ads
  * SCTE 35
    * Marks where in the stream to insert ads
  * VAST
  * Personalization
* Players
  * AVPlayer
  * ExoPlayer
  * Shaka player
  * Shaka embedded
  * dash.js
  * hls.js
  * Metrics
    * Startup time
    * Rebuffer rate
* Vocabulary
  * Source file
  * Mezzanine
  * Deliverable
  * Manifest
  * CDN
  * DRM
  * Packager
  * Encoder
  * Transcoder
