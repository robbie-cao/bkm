# Shell Tips

## Integer & Float Calculations in shell

```
$ echo "$((20.0/7))"
$ awk "BEGIN {print (20+5)/2}"
$ zcalc
$ bc <<< 20+5/2
$ bc <<< "scale=4; (20+5)/2"
$ dc <<< "4 k 20 5 + 2 / p"
$ expr 20 + 5
$ calc 2 + 4
$ node -pe 20+5/2  # Uses the power of JavaScript, e.g. : node -pe 20+5/Math.PI
$ echo 20 5 2 / + p | dc
$ echo 4 k 20 5 2 / + p | dc
$ perl -E "say 20+5/2"
$ python -c "print 20+5/2"
$ python -c "print 20+5/2.0"
$ clisp -x "(+ 2 2)"
$ lua -e "print(20+5/2)"
$ php -r 'echo 20+5/2;'
$ ruby -e 'p 20+5/2'
$ ruby -e 'p 20+5/2.0'
$ guile -c '(display (+ 20 (/ 5 2)))'
$ guile -c '(display (+ 20 (/ 5 2.0)))'
$ slsh -e 'printf("%f",20+5/2)'
$ slsh -e 'printf("%f",20+5/2.0)'
$ tclsh <<< 'puts [expr 20+5/2]'
$ tclsh <<< 'puts [expr 20+5/2.0]'
$ sqlite3 <<< 'select 20+5/2;'
$ sqlite3 <<< 'select 20+5/2.0;'
$ echo 'select 1 + 1;' | sqlite3
$ psql -tAc 'select 1+1'
$ R -q -e 'print(sd(rnorm(1000)))'
$ r -e 'cat(pi^2, "\n")'
$ r -e 'print(sum(1:100))'
$ smjs
$ jspl>>>>>>>>>>>>>>>>>>>>>
```

> http://unix.stackexchange.com/questions/40786/how-to-do-integer-float-calculations-in-bash-or-other-languages-frameworks

```
$ echo 20+5/2 | bc
22
$ echo 'scale=4;20+5/2' | bc
22.5000
```

```
$ perl -E "say 20+5/2"
22.5
```

```
$ python -c "print(20+5/2)"
22 # 22.5 with python3
$ python -c "print(20+5/2.0)"
22.5


# Also supports arbitrary precision numbers:
$ python -c 'print(2**1234)'
295811224608098629060044695716103590786339687135372992239556207050657350796238924261053837248378050186443647759070955993120820899330381760937027212482840944941362110665443775183495726811929203861182015218323892077355983393191208928867652655993602487903113708549402668624521100611794270340232766099317098048887493809023127398253860618772619035009883272941129544640111837184
```

```
$ lua -e "print(20+5/2)"
22.5
```

```
$ php -r 'echo 20+5/2;'
22.5
```

```
$ ruby -e 'p 20+5/2'
22
$ ruby -e 'p 20+5/2.0'
22.5
```

## Decimal to Hexadecimal in Shell

```
$ echo "obase=16; 34" | bc
# If you want to filter a whole file of integers, one per line:
$ (echo "obase=16" ; cat file_of_integers) | bc

$ printf "%x\n" 34
```

> http://stackoverflow.com/questions/378829/convert-decimal-to-hexadecimal-in-unix-shell-script

## Hexadecimal to Decimal in Shell

```
# with bash:
$ echo $((16#FF))
255

# with bc:
$ echo "ibase=16; FF" | bc
255

# with perl:
$ perl -le 'print hex("FF");'
255

# with printf :
$ printf "%d\n" 0xFF
255

# with python:
$ python -c 'print(int("FF", 16))'
255

# with ruby:
$ ruby<<EOF
p "FF".to_i(16).to_s(10)
EOF
"255"
```

> http://stackoverflow.com/questions/13280131/hexadecimal-to-decimal-in-shell-script

## Reference

