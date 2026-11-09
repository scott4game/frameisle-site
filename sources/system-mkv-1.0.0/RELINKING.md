# System MKV replacement materials

The only LGPL runtime dependency in this build is AMSMB2/libsmb2. Follow [NATIVE-AMSMB2.md](NATIVE-AMSMB2.md) using the exact corresponding-source archive, ABI/install name and platform slice. This includes the source modifications permitted by the library license, notices, source availability, reverse-engineering exception for debugging modifications, and a usable replacement/relinking route.

The previous Mac ad-hoc modified-framework replacement test is retained as historical engineering evidence. It does not establish recipient replacement of this newly signed build, Intel hardware execution, or signed iPhone/Apple TV installation. Physical-device replacement/signing remains pending; do not infer full LGPL compliance from dynamic linkage alone.

libwebm is statically compiled under its BSD license and accompanying PATENTS text. Keep the required copyright, conditions and disclaimer; no LGPL relinking condition arises from libwebm itself. Do not broaden the patent grant beyond its actual terms.

Earlier replacement procedures are available through the historical commit referenced in the root README.


## Current Mac evidence and clause distinction — November 8

Candidate Mac 10 now passed the modified-library UI test after desktop unlock. The actual exported Release executable was used in a separately identified, ad-hoc-signed copy with sandbox/network/file entitlements retained. SMB authentication/share navigation, MP4 playback and seeking passed; loaded-image inspection confirmed the embedded modified framework. Both framework architectures are present; only Apple silicon executed. See the recorded Mac 10 replacement validation.

LGPL 2.1 section 6 offers alternatives. A suitable shared-library mechanism under 6(b) does not automatically require the proprietary application's source or object files. Section 6(a)'s executable/relink material requirement and 6(c)'s written-offer route must not be indiscriminately applied to a 6(b) assessment. Apple's Standard EULA section (a) expressly carves out rights permitted by included open-source licenses. Neither point is a blanket legal or patent clearance.

## Recipient delivery — authorized November 9

Existing FrameIsle recipients may request the matching iOS 1.0.0 (15) or Mac 1.0.0 (10) replacement package from **otsgame@yahoo.com**, specifying platform, version and build. The owner explicitly authorized this arrangement. Packages contain an unencrypted copy of the exported application, exact AMSMB2/libsmb2 source and independent build/replacement instructions. They contain no application business source or private signing key. The application binaries are retained locally for on-request delivery, not public website downloads.

These are shared-library replacement aids, not a static-relink object-code kit. The source and original component-license rights remain available without an additional NDA. No request or package has yet been sent to another person. Package hashes are supplied with the requested materials.

The bundled notice in builds 15/10 records the pending review at build time and already gives the same support mailbox and fixed source link. This public addendum records the later recipient-delivery decision; uploaded binaries have not been modified. Mac replacement validation passed on Apple silicon; iOS replacement execution and Intel execution remain unverified. Owner-deferred device work is not relabeled as passed.


References: https://www.gnu.org/licenses/gpl-faq.en.html#LGPLStaticVsDynamic ; https://opensource.org/license/LGPL-2.1 ; https://www.apple.com/legal/internet-services/itunes/dev/stdeula/ .
