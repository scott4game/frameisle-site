# System MKV replacement materials

The only LGPL runtime dependency in this build is AMSMB2/libsmb2. Follow [NATIVE-AMSMB2.md](NATIVE-AMSMB2.md) using the exact corresponding-source archive, ABI/install name and platform slice. This includes the source modifications permitted by the library license, notices, source availability, reverse-engineering exception for debugging modifications, and a usable replacement/relinking route.

The previous Mac ad-hoc modified-framework replacement test is retained as historical engineering evidence. It does not establish recipient replacement of this newly signed build, Intel hardware execution, or signed iPhone/Apple TV installation. Physical-device replacement/signing remains pending; do not infer full LGPL compliance from dynamic linkage alone.

libwebm is statically compiled under its BSD license and accompanying PATENTS text. Keep the required copyright, conditions and disclaimer; no LGPL relinking condition arises from libwebm itself. Do not broaden the patent grant beyond its actual terms.

Earlier replacement procedures are available through the historical commit referenced in the root README.
