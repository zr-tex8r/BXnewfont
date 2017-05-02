BXnewfont Package
=================

LaTeX: Enhanced `\newfont` command

This package provides a new command `\newfontx`. It is similar to
the old (and deprecated) command `\newfont` in function, but is more
compatible with NFSS. In particular, one can safely change font size
after invoking a font command defined by `\newfontx`. The new command
will be useful to users who know much of the old '\newfont` command
but are unfamiliar with the detail of NFSS.

### System requirement

  * TeX format: LaTeX.
  * TeX engine: Anything.
  * Dependent packages: None.

### Installation

  - `*.sty` → $TEXMF/tex/latex/BXnewfont

### License

This package is distributed under the MIT License.

The bxnewfont Package
---------------------

### Package Loading

    \usepackage[<option>]{bxdvidriver}

Available options:

  * `newfont`: Makes `\newfont` an alias of `newfontx`.

### Usage

  * `\newfontx\CMD[<encoding>]{<tfm-name><at-clause>}`: Defines `\CMD`
    to be a “font command” (pseudo-fontdef token). Here the format
    of the mandatory argument is exactly same as that of `\newfont`
    (`<at-clause>` can be empty). The optional argument specifies the
    NFSS encoding name (such as `T1`) of the TFM to be used, and
    defaults to the current font encoding. (If you don’t know what
    it means, then you probably need not care about this argument.)

    When the defined `\CMD` command is invoked, the current font will
    changes to what is specified by the argument, just as the original
    `\newfont`. But unlike `\newfont`, it does not break consistency
    of LaTeX NFSS. Specifically, NFSS is set at the following state:

      - The family is what was auto-generated for `\CMD`.
      - The series is `m` and the shape is `n`.
      - The encoding and size are what was specified by the arguments
        of `\newfontx`.

    It means that further use of “LaTeX’s font commands” will
    probably result in what you will expect. In particular, font size
    can be safely changed. The use of `\itshape` has no effect ---
    of course, because LaTeX does not know the TFM name of the italic
    counterpart --- and no unfavorable effect either.

  * `\newfontx*\CMD[<encoding>]{<tfm-name>}`: Same as the `\newfontx`,
    except that “font commands” defined by `\newfontx*` does not
    fix font size (note the absence of `<at-clause>`). Namely, invoking
    `\CMD` does not change the current font size. This variant surely
    diverges from the original `\newfont`, but will be more useful.

Revision History
----------------

  * Version 0.2a ‹2016/08/08›
      - Now “TFM” names can contain spaces with suitable quoting.
        This enables one to specify OpenType fonts on Unicode engines.
      - An experimental command `\newfontjascale` is added.
  * Version 0.2  ‹2016/03/27›
      - The first public version.

--------------------
Takayuki YATO (aka. "ZR")  
http://zrbabbler.sp.land.to/
