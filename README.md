This is my original 'multitest' perl script, FIO wrapper. It's quite long in the tooth, but I'm keeping it around because it provides consistent comparisons with other runs.

This was originally written long ago as a way for people who don't understand FIO output or really know how to configure it to be able to run a script and compare storage performance on various systems. It was easier to just give this to customers and let them run it, than to work through how to parse FIO output.

Multiiotester runs six simple FIO tests, invalidating cache and using directio. It runs parallel jobs in order to stress the storage, which is particularly important with low latency storage types that might not get pushed to their fullest if they're sitting idle waiting to serve requests most of the time.

```
Multiple IO Tester

  This application emulates a busy server in several states by launching multiple
threads that do various types of IO. This allows us to see what the consequences
are of running in a multitasking environment. This test uses direct IO and
invalidates caches between tests, testing the disk, not the memory.

NOTE: You need at least 4GB of free space in your current working directory.

The following tests currently consist of:

  16 sequential readers
  16 sequential writers
  16 mixed seqential readers/writers (random choice per IO)
  16 random readers
  16 random writers
  16 mixed random readers/writers (random choice per IO)

Feel free to modify the script to meet your needs. Enjoy!

The test should take less than 2 minutes. Press <ENTER> to begin...

 running IO "sequential read" test...
	result is 1.86GB per second

 running IO "sequential write" test...
	result is 1.56GB per second

 running IO "seq read/seq write" test...
	result is 837.54MB/871.63MB per second

 running IO "random read" test...
	result is 74.43MB per second
	equals 19055.2 IOs per second

 running IO "random write" test...
	result is 88.42MB per second
	equals 22636.0 IOs per second

 running IO "rand read/rand write" test...
	result is 40.62MB/40.66MB per second
	equals 10399.5/10407.8 IOs per second
```
