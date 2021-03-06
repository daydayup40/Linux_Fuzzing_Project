Linux_Fuzzing_Project
=====================

Linux Kernel System Calls Fuzzing 

How to use this tool:

1) First of all run makefile.sh to create the log folder, pid folder and compile fuzzer.c.

2) run ./gentree.sh script to create victim files under ./sandbox subdir

3) ./fuzzer

4) ./stop_clean.sh to delete all zombie processes, pid-files and logs

Note: this tool may harm your Computer. Please make sure that you use on a testing machine that does not have important information to avoid loosing these information.

Changelog
=========

0.5
---------
- Bug fixes
- SYS_execve fuzz algorithm update
- All warnings have been fixed
- Code has been cleaned up


0.4
---------
- bug fixes
- ./build.sh updated
- worker process recreation after crash


0.3
---------
+ Implemented all 15 syscals
+ Cleanup script ./stop_clean.sh to kill all zombie processes, remove pids & logs
+ directory subtree './sandbox' generation script
+ advanced fuzzing techniques different per worker process


0.2 alpha
---------

- Per-process logging
- PID-files basic support
- Multiprocess architecture implemented (main process spawns watchdog and 4(hardcoded)
  worker process each fuzzying call and writes each own log)

0.1 Proof Of Concept(POC)
---------
Basic draft. 

Here we are calling `sys_chdir()` syscall 20 times in a loop 
with not just a random binary data as input, but kind of highly poisoned
variable length, variable tree depth path string with some nonASCII \
symbols (which in log substituted with '_' char to not break text output).
We can see here no hangs no crashes. Instead syscall returns '-1'
as designed by smart Linux devs for any incorrect path input.
