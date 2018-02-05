If you see it configure fine but fail on make with:

```
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh /nfs/dust/cms/user/aggleton/UHH_Dev/94X_3/fj2/missing aclocal-1.15 -I m4
/nfs/dust/cms/user/aggleton/UHH_Dev/94X_3/fj2/missing: line 81: aclocal-1.15: command not found
WARNING: 'aclocal-1.15' is missing on your system.
         You should only need it if you modified 'acinclude.m4' or
         'configure.ac' or m4 files included by 'configure.ac'.
         The 'aclocal' program is part of the GNU Automake package:
         <http://www.gnu.org/software/automake>
         It also requires GNU Autoconf, GNU m4 and Perl in order to run:
         <http://www.gnu.org/software/autoconf>
         <http://www.gnu.org/software/m4/>
         <http://www.perl.org/>
Makefile:615: recipe for target 'aclocal.m4' failed
```

then you need to run `autoreconf -if`. I don't know why. It even works fine straight untarred.

NB you can also try

```
touch aclocal.m4
find . -name 'Makefile.in' -print -exec touch '{}' ';'
touch configure
```

But this caused the same error halfway through `make`.

