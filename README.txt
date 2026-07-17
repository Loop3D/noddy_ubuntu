NODDY -- LINUX (UBUNTU) RUNTIME BUNDLE
=======================================

Contains just the `noddy` binary. Unlike the Windows bundle, this is
NOT self-contained -- it dynamically links against system Qt5
libraries rather than bundling them. On a machine that doesn't already
have Qt5 installed:

  sudo apt-get install libqt5widgets5 libqt5printsupport5

(this pulls in libqt5gui5/libqt5core5a, which is also where Qt's X11
"platform plugin" comes from -- required to open any window at all).

Then run:

  chmod +x noddy
  ./noddy

Batch/CLI mode:

  ./noddy fold_tilt_fault.his -block

Use noddy -help for the full list of batch options.

To run headless (no display, e.g. CI or a WSL session with no X
server), set QT_QPA_PLATFORM=offscreen before launching -- this is how
this exact binary's own batch-mode testing was verified (see the
source project's user.txt).

Verified (ldd) against Ubuntu 20.04, all shared-library dependencies
resolved via already-installed system packages -- no other files
needed alongside the binary on a normal desktop Ubuntu install.

