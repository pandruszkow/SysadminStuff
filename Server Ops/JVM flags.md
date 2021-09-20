# Memory

## Memory (heap) size
Sizes can be specified with `k`, `m`, and `g`. The letters can be upper-case or lower-case.

* Lower bound: `-Xms100g` 
* Upper bound: `-Xmx999g`

(Source: https://www.baeldung.com/jvm-parameters)

## Memory (metaspace) size
I haven't had time to look into this, but leaving a link for future research:
https://blogs.oracle.com/poonam/about-g1-garbage-collector,-permanent-generation-and-metaspace

## Handling out of memory conditions:
Apparently the server can be rebooted, or some other emergency command can be executed, if the JVM runs out of memory.

> OnOutOfMemoryError is used to issue emergency commands to be executed in case of out of memory error; proper command should be used in the space of cmd args. 
> 
> For example, if we want to restart the server as soon as out of memory occur, we can set the parameter:
> 
> -XX:OnOutOfMemoryError="shutdown -r"

(Source: https://www.baeldung.com/jvm-parameters#handling-out-of-memory)

# Verification
It's possible (BUT NOT RECOMMENDED) to disable class verification in the JVM. Supposedly that's meant to make things faster, but I haven't timed the performance difference myself yet.

It's probably safe to enable on the local dev IDE, but I wouldn't dream of enabling this absolutely anywhere else (including dev environments) due to potential security and stability implications. 

To do this, run with the parameter: `-Xverify:none`

**IN THE STRONGEST POSSIBLE TERMS, THIS IS NOT APPROPRIATE FOR A PRODUCTION SYSTEM**

> If you disable bytecode verification, you are saying that not only do you trust all of the code you are running to not be malicious, you are also saying you trust every single class you load to be bug-free (at the bytecode level). This is a much higher standard than simply trusting code to not be overtly malicious.

(Source: https://docs.oracle.com/javase/8/docs/technotes/tools/unix/java.html)
