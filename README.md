# BNFCexample

https://bnfc.digitalgrammars.com/tutorial/bnfc-tutorial.html

```
BNFCexample$ cd calc
BNFCexample/calc$ bnfc --haskell Calc.cf

8 rules accepted

Use Alex 3.0 to compile LexCalc.x.
ParCalc.y Tested with Happy 1.15
no change to file ./AbsCalc.hs
no change to file ./LexCalc.x
no change to file ./ParCalc.y
writing file ./TestCalc.hs (saving old file as ./TestCalc.hs.bak)
no change to file ./DocCalc.txt
no change to file ./SkelCalc.hs
no change to file ./PrintCalc.hs
no change to file ./ErrM.hs
BNFCexample/calc$ alex LexCalc.x
BNFCexample/calc$ happy ParCalc.y
BNFCexample/calc$ runhaskell TestCalc.hs
1 + 2 * (4 - 1) - 4 / 2

Parse Successful!

[Abstract Syntax]

ESub (EAdd (EInt 1) (EMul (EInt 2) (ESub (EInt 4) (EInt 1)))) (EDiv (EInt 4) (EInt 2))

[Linearized tree]

1 + 2 * (4 - 1)- 4 / 2
BNFCexample/calc$ runhaskell Main.hs
1 + 2 * (4 - 1) - 4 / 2

Parse Successful!

[Abstract Syntax]

ESub (EAdd (EInt 1) (EMul (EInt 2) (ESub (EInt 4) (EInt 1)))) (EDiv (EInt 4) (EInt 2))

[Linearized tree]

1 + 2 * (4 - 1)- 4 / 2

[Linearized tree]

Just 5
```
