# FrameIsle website

Static English, Simplified Chinese and Japanese product/support/privacy/license pages. Public support address: otsgame@yahoo.com. No application source, credentials or private media belong in this repository. Its source has no analytics scripts; the delivery layer must also be checked for injected scripts. Cloudflare Web Analytics injection was observed on the new domain and is disclosed in the policy while owner-side disabling is pending.

Preview: `python3 -m http.server 8765 --bind 127.0.0.1` from this directory.

GitHub Pages: create a dedicated `frameisle-site` repository, push these files to `main`, select Pages → Deploy from a branch → main / root, enable HTTPS. Confirm the signed-in owner's account and repository visibility first. Private-repository Pages availability depends on the account plan; do not publish application source to work around it. The configured custom domain is https://frameisle.icqnft.com/; preserve CNAME when publishing. Enforce HTTPS in the Pages settings and verify the old github.io URL does not downgrade to HTTP.

Verify the public HTTPS home, all three support/privacy page variants, license links and review-assets/review-demo.mp4 without authentication before putting URLs into App Store Connect. Public site content is intentionally visible for store review. The app is not yet released, so no download badge claims current availability.

The review sample is generated from FFmpeg testsrc2 and a synthesized tone; no third-party movie/TV material is included. The SRT text is original. Open-source component notices are attributed separately. Corresponding-source/relinking delivery remains a public-release gate, explicitly stated on the site.
