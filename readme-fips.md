Eclipse FIPS capable Mosquitto
==============================

This version of Mosquitto uses an embedded FIPS 140-2-validated cryptographic module (OpenSSL FIPS Object Module 2.0, Certificate #1747)
running on Ubuntu 16.04LTS, 18.04LTS platform per FIPS 140-2 Implementation Guidance section G.5 guidelines.

Curently this mosquitto package is only verified on Ubuntu 16.04LTS and 18.04LTS.

Prior to building this version you have to have built and installed the OpenSSL FIPS Object Module 2.0 and an OpenSSL FIPS capable
version <https://www.openssl.org/docs/fips.html>.

Build using "make CXX=fipsld CC=fipsld FIPSLD_CC=gcc"

