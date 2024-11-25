# Primes Benchmark

This is my own personal benchmark, created in 2016 to compare Arm SBCs with each
other and with x86 PCs. I have since run it on a variety of machines, from a
16 MHz AVR to recent PCs and Macs and cloud servers.

It uses only 8k of RAM and a few hundred bytes of program code, and
tests simple arithmetic, loads and stores in L1 cache, and tight
if/then/else and looping logic, including some fairly hard to predict
branches since the distribution of prime numbers is somewhat
random.

The results correlate well with other small in-cache benchmarks such as
Dhrystone and Coremark, but it's smaller and easier to build.

A typical use looks like this:

    user@starfive:~$ wget http://hoult.org/primes.txt
    --2024-11-25 17:01:17--  https://hoult.org/primes.txt
    Resolving hoult.org (hoult.org)... 104.218.12.10
    Connecting to hoult.org (hoult.org)|104.218.12.10|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 8805 (8.6K) [text/plain]
    Saving to: 'primes.txt'
    
    primes.txt                       100%[=========================================================>]   8.60K  --.-KB/s    in 0.001s  
    
    2024-11-25 17:01:19 (11.0 MB/s) - 'primes.txt' saved [8805/8805]
    
    user@starfive:~$ mv primes.txt primes.c
    user@starfive:~$ gcc -O primes.c -o primes
    user@starfive:~$ ./primes
    Starting run
    3713160 primes found in 15140 ms
    216 bytes of code in countPrimes()
    user@starfive:~$ 


[Source Code](http://hoult.org/primes.txt)
