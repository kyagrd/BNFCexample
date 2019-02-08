# BNFCexample

https://bnfc.digitalgrammars.com/tutorial/bnfc-tutorial.html

```
BNFCexample$ cd calc
BNFCexample/calc$ bnfc --haskell Calc.cf

8 rules accepted

Use Alex 3.0 to compile LexCalc.x.
ParCalc.y Tested with Happy 1.15
writing new file ./AbsCalc.hs
writing new file ./LexCalc.x
writing new file ./ParCalc.y
writing new file ./TestCalc.hs
writing new file ./DocCalc.txt
writing new file ./SkelCalc.hs
writing new file ./PrintCalc.hs
writing new file ./ErrM.hs
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
BNFCexample/calc$ diff Main.hs TestCalc.hs 
29c29
< runFile :: Verbosity -> ParseFun Exp -> FilePath -> IO ()
---
> runFile :: (Print a, Show a) => Verbosity -> ParseFun a -> FilePath -> IO ()
32c32
< run :: Verbosity -> ParseFun Exp -> String -> IO ()
---
> run :: (Print a, Show a) => Verbosity -> ParseFun a -> String -> IO ()
41d40
<                           showValue tree
45,58d43
< showValue :: Exp -> IO ()
< showValue e = do putStr "\n[Evaluated tree]\n\n" 
<                  print (evalExp e)
< 
< evalExp :: Exp -> Maybe Integer
< evalExp (EAdd x y) = do { v1 <- evalExp x; v2 <- evalExp y; return (v1 + v2) }
< evalExp (ESub x y) = do { v1 <- evalExp x; v2 <- evalExp y; return (v1 - v2) }
< evalExp (EMul x y) = do { v1 <- evalExp x; v2 <- evalExp y; return (v1 * v2) }
< evalExp (EDiv x y) = do v1 <- evalExp x
<                         v2 <- evalExp y
<                         case v2 of
<                           0 -> Nothing
<                           _ -> return (v1 `div` v2)
< evalExp (EInt n) = return n
```
