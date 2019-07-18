# GStreamer WebRTC demos

All demos use the same signalling server in the `signalling/` directory

## Filing bugs

Please only file bugs about the demos here. Bugs about GStreamer's WebRTC implementation should be filed on the [GStreamer bugzilla](https://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer&component=gst-plugins-bad).

You can also find us on IRC by joining #gstreamer @ FreeNode.

## Documentation

Currently, the best way to understand the API is to read the examples. This post breaking down the API should help with that:

http://blog.nirbheek.in/2018/02/gstreamer-webrtc.html

### sendrecv: Send and receive audio and video

* Serve the `js/` directory on the root of your website, or open https://webrtc.nirbheek.in
  - The JS code assumes the signalling server is on port 8443 of the same server serving the HTML

* Open the website in a browser and ensure that the status is "Registered with server, waiting for call", and note the `id` too.

#### Running the Rust version

* Install a recent Rust toolchain, e.g. via [rustup](https://rustup.rs/).
* Run `cargo build` for building the executable.
* Run `cargo run -- --peer-id=ID` with the `id` from the browser. You will see state changes and an SDP exchange.

You can pass a --server argument to all versions, for example `--server=wss://127.0.0.1:8443`.