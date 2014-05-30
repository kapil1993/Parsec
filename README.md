PARSEC benchmarks are generally very easy to build and run, given their super awesome parsecmgmt script. For recent 64 bit systems (with higher versions of gcc and binutils) though, 'dedup' creates a problem. When I try to compile the 'dedup' kernel it fails with "md5-x86_64.s:41: Error: 0xd76aa478 out range of signed 32bit displacement" and similar other errors in the same file at other locations.

If you just want a quick fix do the following:
1) download the latest openssl library. It has been fixed in the recent versions of the ssl library.
http://www.openssl.org/source/openssl-1.0.1c.tar.gz worked for me.
2) replace the source in {PARSECDIR}/pkgs/libs/ssl/src.
3) cd to {PARSECDIR}/pkgs/libs/ssl/src
4) ./config threads -D_REENTRANT --openssldir={PARSECDIR}/pkgs/libs/ssl/inst/amd64-linux.gcc-pthreads (this is for the pthreads config. change accordingly for your needs)
5) Now build dedup.

This should work without any problems. Enjoy :)Parsec
======
PARSEC benchmarks are generally very easy to build and run, given their super awesome parsecmgmt script. For recent 64 bit systems (with higher versions of gcc and binutils) though, 'dedup' creates a problem. When I try to compile the 'dedup' kernel it fails with "md5-x86_64.s:41: Error: 0xd76aa478 out range of signed 32bit displacement" and similar other errors in the same file at other locations.

If you just want a quick fix do the following:
1) download the latest openssl library. It has been fixed in the recent versions of the ssl library.
http://www.openssl.org/source/openssl-1.0.1c.tar.gz worked for me.
2) replace the source in {PARSECDIR}/pkgs/libs/ssl/src.
3) cd to {PARSECDIR}/pkgs/libs/ssl/src
4) ./config threads -D_REENTRANT --openssldir={PARSECDIR}/pkgs/libs/ssl/inst/amd64-linux.gcc-pthreads (this is for the pthreads config. change accordingly for your needs)
5) Now build dedup.

This should work without any problems. Enjoy :)
