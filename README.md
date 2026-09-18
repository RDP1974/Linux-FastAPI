# Linux-FastApi
D13.2 on Linux: Excellent Performance

Hi everyone, how are you doing?
I wanted to test the capabilities of the new next-generation Linux compiler, and I have to say I was impressed by its code optimization and parallel compilation speed.

Here are some results from a poker library benchmark, running single-threaded on an i9-9900KF (8 cores / 16 threads):
Windows 64-bit → 2.7M ops/s
FPC 3.2.2, Linux 64-bit → 1.3M ops/s
D13.2, Linux 64-bit → 5M ops/s

I also ran some server benchmarks in FastAPI mode using TMS Sparkle (https://www.tmssoftware.com/site/sparkle.asp) and Dext (https://github.com/dotpas/dext).
Both use the epoll() API and deliver similar results. The tests ran with 125 concurrent users on Linux kernel 7.0 using JsonDataObjects (https://github.com/ahausladen/jsondataObjects).

Database queries with connection pooling:
D13.2, PostgreSQL query against the cities database → 562 req/s, 205.87 MB/s
D13.2, PostgreSQL query against the cities database using my TLS model → 752.55 req/s, 272.14 MB/s
D13.2, PostgreSQL using my TLS model and rpmalloc → 889.75 req/s, 322.27 MB/s
Same test with Python FastAPI → 3.92 req/s and many timeouts
Same test with Node.js → 125.73 req/s and some timeouts

Hello World GET request with a simple JSON response:
205,174.80 req/s, 606.34 µs, 41.68 MB/s

POST request with JSON deserialization and serialization of 10 records:
94481.05 req/s, 1.32ms,   624.76MB/s

Congratulations to Embarcadero Labs on this exceptional achievement!
 
Roberto Della Pasqua
https://www.dellapasqua.com
 
By the way, feel free to contact me for the test files or to learn more about the enhanced zero-copy overlapped interfaces or TLS dataset for building scalable server applications.
