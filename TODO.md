## TODO list:

#### Bugs:

- [ ] fix macro substitution with nested definitions (ShangHongzhang)
- [ ] FPU st(0) is left unclean (kwisatz haderach). Incompatible with optimized gcc/msc code

- [ ] constructors
- [ ] cast bug (Peter Wang)
- [ ] define incomplete type if defined several times (Peter Wang).
- [ ] configure --cc=tcc (still one bug in libtcc1.c)
- [ ] test binutils/gcc compile
- [ ] tci patch + argument.
- [ ] see -lxxx bug (Michael Charity).
- [ ] see transparent union pb in /urs/include/sys/socket.h
- [ ] precise behaviour of typeof with arrays ? (__put_user macro) but should suffice for most cases)
- [ ] handle '? x, y : z' in unsized variable initialization (',' is considered incorrectly as separator in preparser)
- [ ] transform functions to function pointers in function parameters (net/ipv4/ip_output.c)
- [ ] fix function pointer type display
- [ ] check lcc test suite -> fix bitfield binary operations
- [ ] check section alignment in C
- [ ] fix invalid cast in comparison 'if (v == (int8_t)v)'
- [ ] finish varargs.h support (gcc 3.2 testsuite issue)
- [ ] fix static functions declared inside block
- [ ] fix multiple unions init
- [ ] sizeof, alignof, typeof can still generate code in some cases.
- [ ] Fix the remaining libtcc memory leaks.
- [ ] make libtcc fully reentrant (except for the compilation stage itself).

#### Bound checking:

- [ ] '-b' bug.
- [ ] fix bound exit on RedHat 7.3
- [ ] setjmp is not supported properly in bound checking.
- [ ] fix bound check code with '&' on local variables (currently done only for local arrays).
- [ ] bound checking and float/long long/struct copy code. bound checking and symbol + offset optimization

#### Missing features:

- [ ] disable-asm and disable-bcheck options
- [ ] __builtin_expect()
- [ ] improve '-E' option.
- [ ] add '-MD' option
- [ ] atexit (Nigel Horne)
- [ ] packed attribute
- [ ] C99: add variable size arrays (gcc 3.2 testsuite issue)
- [ ] C99: add complex types (gcc 3.2 testsuite issue)
- [ ] postfix compound literals (see 20010124-1.c)

#### Optimizations:

- [ ] suppress specific anonymous symbol handling
- [ ] more parse optimizations (=even faster compilation)
- [ ] memory alloc optimizations (=even faster compilation)
- [ ] optimize VT_LOCAL + const
- [ ] better local variables handling (needed for other targets)

#### Not critical:

- [ ] C99: fix multiple compound literals inits in blocks (ISOC99 normative example - only relevant when using gotos! -> must add boolean variable to tell if compound literal was already initialized).
- [ ] add PowerPC or ARM code generator and improve codegen for RISC (need to suppress VT_LOCAL and use a base register instead).
- [ ] interactive mode / integrated debugger
- [ ] fix preprocessor symbol redefinition
- [ ] better constant opt (&&, ||, ?:)
- [ ]add portable byte code generator and interpreter for other unsupported architectures.
- [ ] C++: variable declaration in for, minimal 'class' support.
- [ ] win32: __intxx. use resolve for bchecked malloc et al. check exception code (exception filter func).
- [ ] handle void (__attribute__() *ptr)()

#### Fixed (probably):

- [ ] bug with defines:
```c
    #define spin_lock(lock) do { } while (0)
    #define wq_spin_lock spin_lock
    #define TEST() wq_spin_lock(a)
```
- [ ] typedefs can be structure fields
- [ ] see bugfixes.diff + improvement.diff from Daniel Glockner
- [ ] long long constant evaluation
- [ ] add alloca()
- [ ] gcc '-E' option.
- [ ] #include_next support for /usr/include/limits ?
- [ ] function pointers/lvalues in ? : (linux kernel net/core/dev.c)
- [ ] win32: add __stdcall, check GetModuleHandle for dlls.
