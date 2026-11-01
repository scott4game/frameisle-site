# Rebuilding AMSMB2 without the private application project

These minimal host examples let you build the dynamic library independently. They do not contain FrameIsle application/business code. Keep the original dependency copyright and license notices with all source copies and modifications.

## Source

Download [AMSMB2 4.0.3 with its exact libsmb2 submodule](https://raw.githubusercontent.com/scott4game/frameisle-site/32b9ebe662846c8b6eb62b92edb0d429888f2db8/sources/AMSMB2-4.0.3/AMSMB2-4.0.3-corresponding-source.tar.gz).

SHA-256: `4532a6622dbe7fb02a95bf757d4dc622333a124eef6ea4faf2282d639b195b14`

Extract it next to this README so `AMSMB2-4.0.3/Package.swift` sits beside `project.yml`. Make any library changes in that extracted copy. This archive includes libsmb2; a plain upstream tag download may omit the submodule. The package's Swift Atomics dependency is for its upstream tests and is not linked into the example app's playback/library runtime.

## Build

Requires Xcode 27.1 and XcodeGen. Run in this folder:

```sh
xcodegen generate
xcodebuild -project FrameIsleLibraryReplacement.xcodeproj -scheme MacHost \
  -configuration Release -destination 'generic/platform=macOS' \
  -derivedDataPath output/mac ONLY_ACTIVE_ARCH=NO CODE_SIGNING_ALLOWED=NO build
xcodebuild -project FrameIsleLibraryReplacement.xcodeproj -scheme DeviceHost \
  -configuration Release -destination 'generic/platform=iOS' \
  -derivedDataPath output/ios CODE_SIGNING_ALLOWED=NO build
```

The rebuilt framework is under `output/<platform>/Build/Products/Release*/PackageFrameworks/AMSMB2.framework` and embedded in the example host. Mac output must contain both arm64 and x86_64. iOS device output must contain arm64; simulator output is not interchangeable.

## Replace in a copy

1. Preserve an unmodified copy of the application's matching build and its framework. Compare `otool -D` install names and `lipo -archs` architectures before replacing.
2. Replace only the embedded AMSMB2.framework in a disposable application copy. Keep the library's public interface compatible. libsmb2 is built into AMSMB2, not a second embedded framework.
3. Re-sign the replacement framework and application with an identity/profile valid for the recipient's platform. On iOS replace the embedded provisioning profile and use matching application/keychain entitlements; do not revoke an existing certificate. On Mac local ad-hoc signing is useful for testing but is not notarization or App Store signing. Preserve sandbox/network/file-access entitlements when testing the same behavior.
4. Install that copy separately from the user's normal app where possible, verify the modified framework is loaded, then test SMB authentication, shares, directory listing, playback and seeking. Record the library and app hashes, changed source, platform and signing method.

These steps describe engineering validation, not guaranteed modification of an App Store-downloaded/FairPlay-protected binary. Recipient access to any further usable replacement materials and distribution/signing restrictions must be resolved before declaring LGPL obligations complete. Contact `otsgame@yahoo.com` for the exact build's materials and assistance.

Apple's Standard EULA includes an exception to its reverse-engineering/modification restrictions where the included open-source component license permits those actions. This does not by itself settle every licensing or distribution question: [Standard EULA, section a](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/).
