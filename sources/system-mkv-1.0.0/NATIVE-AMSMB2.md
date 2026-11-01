# Native branch dependency evidence

This branch is a development candidate, not an assertion of legal clearance.

## Actual dependency graph

- AVFoundation/CoreMedia/VideoToolbox and other Apple system frameworks provide playback.
- AMSMB2 4.0.3 (`1726aaaf7adf63d7d1d2a0c5d1b0e635028215c0`) declares a **dynamic** Swift package library.
- Its `libsmb2` submodule is pinned at `aff9fa6ba9f41cfd3c15d184554601ec3f6d8d03`, compiled into that dynamic framework.
- Package.swift compiles libsmb2 `lib/` and `include/`; its BSD example applications are not compiled. The upstream Swift Atomics dependency is used by upstream tests, not the app's runtime target.
- The checked-in AMSMB2 LICENSE is LGPL 2.1. Individual Swift headers also contain copyright/MIT wording; retain both the upstream LICENSE and individual notices. libsmb2 COPYING identifies its library as LGPL 2.1-or-later. Never infer exemption merely from a top-level README or dynamic linkage.
- No package source changes are made. Component source notices and corresponding-source tarball are included. Source archive SHA-256 is in `native-source-manifest.json`; the tarball includes the libsmb2 submodule, which a plain GitHub tag archive may omit.

## Build and source availability

Extract `sources/AMSMB2-4.0.3-corresponding-source.tar.gz`. Use the extracted folder as the AMSMB2 local Swift package path in a copy of `project.yml`; replace its URL/version keys with `path: /absolute/path/to/AMSMB2-4.0.3`. Run `xcodegen generate` and build the appropriate scheme with Xcode 27.1 and Swift 5 language mode. For Mac universal builds set `ONLY_ACTIVE_ARCH=NO` for all targets. Public source examples/tests may resolve swift-atomics 1.2.0; it is not a playback runtime component.

For every shipped binary retain: exact source archive, notice files, manifest, compiler version, build flags, library/app binaries and signing/export metadata. Publish the matching source download or a valid source offer at distribution time, including patches if any. The offer in the development app points to support and does not constitute completed public-release preparation.

## Replacement/relinking checklist

1. Build an interface-compatible modified AMSMB2 framework for the same platform and architectures, preserving the framework's install name.
2. In a copy of the app replace the embedded AMSMB2 framework; preserve required Swift runtime dependencies.
3. Re-sign the framework and application with the recipient's valid signing identity/profile. For Mac local verification ad-hoc signing can be used; this is not notarization or an App Store distribution signature.
4. Install the modified app, confirm it loads the replaced framework, then verify SMB authentication, share enumeration, range reads and video playback.
5. Ensure application license terms do not prohibit reverse engineering necessary to debug modifications of this library. Address applicable distribution/signing restrictions before claiming compliance.

Mac replacement was exercised locally: extract the supplied source archive, add `public func frameIsleReplacementProbe() -> String { "modified-library-test" }`, rebuild the universal dynamic framework, replace it in a copy of the Debug app, re-sign framework and app ad-hoc, and rerun SMB playback/seek against that copy. Both architectures contain the new exported symbol; the Apple-silicon Mac test passed. Test DYLD framework paths were restricted to the copied app so they could not select the original package framework. The dated local experiment and logs are retrievable from commit `d852858` in Git history; this is not a fresh verification of a later signed build. This is local replacement evidence, not a legal conclusion or Intel hardware test.

Actual recipient replacement on signed iPhone/Apple TV hardware is pending. No physical-device test or blanket patent clearance is claimed. Independent review of the release terms remains required before paid public distribution.
