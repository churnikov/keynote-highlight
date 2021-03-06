# Keynote highlighter

*Code highlighter with preset, but customizable settings*

## Install and run

Requires python 3.9

1. `pip install keynote-highlight`;
2. Copy code to clipboard;
3. Run `keyhi`;
4. Paste code to keynote;
5. That's it!

## Motivation

Have you ever wanted to highlight your code for presentation with just one command from cli? Then this tool is for you!

Let's say, you want to make a presentation on Riemann sum and you want to add this code to your slides.

```python
from typing import Callable, Iterator


def linspace(a: float, b: float, n=100) -> Iterator[tuple[float, float]]:
    """Linspace in pure python"""
    delta = abs((b - a) / n)
    x_i_min_1 = a
    x_i = a + delta
    yield x_i_min_1, x_i
    for _ in range(n):
        x_i_min_1 = x_i
        x_i += delta
        yield x_i_min_1, x_i
    yield x_i, b


def riemann_sum(f: Callable[[float], float], range_: tuple[float, float]) -> float:
    """
    Calculate Riemann sum
    
    :param f: function of a single argument
    :param range_: range of values this function is defined on
    :return: Riemann sum
    """
    res = 0
    for x_i_min_1, x_i in linspace(*range_):
        res += f((x_i+x_i_min_1)/2) * (x_i - x_i_min_1)
    return res

if __name__ == "__main__":
    print(riemann_sum(lambda x: x, (-4, 3)))
```

This is how it's going to work:

[![keyhi_demo.gif](images/keyhi_demo.gif)](https://yadi.sk/i/Cy2s4W1BV5kVsA)

## Features
- Select any language and styles to highlight code available in pygments;
- Change font size of your code;
- Load and save code straight to clipboard;
    - You can also your default cli code editor as a source of code instead of clipboard.
- For python you can change width of your code and apply black code formatter.

```
➜ keyhi --help 
Usage: keyhi [OPTIONS]

  Highlight code for keynote.app from clipboard and save result to
  clipboard.

  STYLE Style for code

  FONTSIZE Font size to use

  LANGUAGE Programming language of source code

  INP What is the source of code

  LINE-WIDTH python only. Format code to fit width

Options:
  -l, --language [abap|apl|abnf|as3|as|ada|adl|agda|aheui|alloy|at|ampl|html+ng2|ng2|antlr-as|antlr-csharp|antlr-cpp|antlr-java|antlr|antlr-objc|antlr-perl|antlr-python|antlr-ruby|apacheconf|applescript|arduino|arrow|aspectj|asy|augeas|autoit|ahk|awk|bbcbasic|bbcode|bc|bst|bare|basemake|bash|console|bat|befunge|bib|blitzbasic|blitzmax|bnf|boa|boo|boogie|brainfuck|bugs|camkes|c|cmake|c-objdump|cpsa|aspx-cs|csharp|ca65|cadl|capdl|capnp|cbmbas|ceylon|cfengine3|chai|chapel|charmci|html+cheetah|js+cheetah|cheetah|xml+cheetah|cirru|clay|clean|clojure|clojurescript|cobolfree|cobol|coffee-script|cfc|cfm|cfs|common-lisp|componentpascal|coq|cpp|cpp-objdump|crmsh|croc|cryptol|cr|csound-document|csound|csound-score|css+django|css+erb|css+genshitext|css|css+php|css+smarty|cuda|cypher|cython|d|d-objdump|dpatch|dart|dasm16|control|delphi|devicetree|dg|diff|django|docker|dtd|duel|dylan-console|dylan|dylan-lid|ecl|ec|earl-grey|easytrieve|ebnf|eiffel|iex|elixir|elm|emacs|email|erb|erlang|erl|html+evoque|evoque|xml+evoque|execline|ezhil|fsharp|fstar|factor|fancy|fan|felix|fennel|fish|flatline|floscript|forth|fortranfixed|fortran|foxpro|freefem|gap|gdscript|glsl|gas|genshi|genshitext|pot|cucumber|gnuplot|go|golo|gooddata-cl|gosu|gst|groff|groovy|hlsl|haml|html+handlebars|handlebars|haskell|hx|hexdump|hsail|hspec|html+django|html+genshi|html|html+php|html+smarty|http|haxeml|hylang|hybris|idl|icon|idris|igor|inform6|i6t|inform7|ini|io|ioke|irc|isabelle|j|jags|jasmin|java|js+django|js+erb|js+genshitext|js|js+php|js+smarty|jcl|jsgf|jsonld|json|jsp|jlcon|julia|juttle|kal|kconfig|kmsg|koka|kotlin|lsl|css+lasso|html+lasso|js+lasso|lasso|xml+lasso|lean|less|lighty|limbo|liquid|lagda|lcry|lhs|lidr|live-script|llvm|llvm-mir-body|llvm-mir|logos|logtalk|lua|mime|moocode|doscon|make|css+mako|html+mako|js+mako|mako|xml+mako|maql|md|mask|mason|mathematica|matlab|matlabsession|minid|ms|modelica|modula2|trac-wiki|monkey|monte|moon|mosel|css+mozpreproc|mozhashpreproc|javascript+mozpreproc|mozpercentpreproc|xul+mozpreproc|mql|mscgen|mupad|mxml|mysql|css+myghty|html+myghty|js+myghty|myghty|xml+myghty|ncl|nsis|nasm|objdump-nasm|nemerle|nesc|newlisp|newspeak|nginx|nim|nit|nixos|notmuch|nusmv|numpy|objdump|objective-c|objective-c++|objective-j|ocaml|octave|odin|ooc|opa|openedge|pacmanconf|pan|parasail|pawn|peg|perl6|perl|php|pig|pike|pkgconfig|plpgsql|pointless|pony|postscript|psql|postgresql|pov|powershell|ps1con|praat|prolog|promql|properties|protobuf|psysh|pug|puppet|pypylog|python2|py2tb|pycon|python|pytb|qbasic|qvto|qml|rconsole|rnc|spec|racket|ragel-c|ragel-cpp|ragel-d|ragel-em|ragel-java|ragel|ragel-objc|ragel-ruby|raw|rd|reason|rebol|red|redcode|registry|resource|rexx|rhtml|ride|roboconf-graph|roboconf-instances|robotframework|rql|rsl|rst|rts|rbcon|rb|rust|sas|splus|sml|sarl|sass|scala|scaml|scdoc|scheme|scilab|scss|shexc|shen|sieve|silver|singularity|slash|slim|slurm|smali|smalltalk|sgf|smarty|snobol|snowball|solidity|sp|sourceslist|sparql|sql|sqlite3|squidconf|ssp|stan|stata|sc|swift|swig|systemverilog|tap|tnt|toml|tads3|tasm|tcl|tcsh|tcshcon|tea|ttl|termcap|terminfo|terraform|tex|text|thrift|tid|todotxt|tsql|treetop|turtle|html+twig|twig|ts|typoscriptcssdata|typoscripthtmldata|typoscript|ucode|unicon|urbiscript|usd|vbscript|vcl|vclsnippets|vctreestatus|vgl|vala|aspx-vb|vb.net|html+velocity|velocity|xml+velocity|verilog|vhdl|vim|wdiff|webidl|whiley|x10|xquery|xml+django|xml+erb|xml|xml+php|xml+smarty|xorg.conf|xslt|xtend|extempore|yaml+jinja|yaml|yang|zeek|zephir|zig|auto]
                                  Programming language to highlight
  -f, --fontsize INTEGER          Fontsize of resulting text
  -s, --style [default|emacs|friendly|colorful|autumn|murphy|manni|monokai|perldoc|pastie|borland|trac|native|fruity|bw|vim|vs|tango|rrt|xcode|igor|paraiso-light|paraiso-dark|lovelace|algol|algol_nu|arduino|rainbow_dash|abap|solarized-dark|solarized-light|sas|stata|stata-light|stata-dark|inkpot]
                                  Theme of resulting text
  -i, --inp [clipboard|editor]    What is the source of code
  -w, --line-width INTEGER        python only. Format code to fit width
  --help                          Show this message and exit.
```
