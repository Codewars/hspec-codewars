# Test.Hspec.Codewars

Utility functions for testing on Codewars with Hspec.

### Blacklisting

#### `Hidden`

```haskell
data Hidden
  -- | Module to be hidden
  = Module {moduleName :: String}
  -- | Symbol from a module to be hidden
  | FromModule {moduleName :: String, symbolName :: String}
```

#### `solutionShouldHide`

```haskell
solutionShouldHide :: Hidden -> Expectation
```

Check that solution hides a module or a symbol from a module.

```haskell
solutionShouldHide $ FromModule "Prelude" "head"
```

#### `solutionShouldHideAll`

```haskell
solutionShouldHideAll :: [Hidden] -> Expectation
```

Check that solution hides all of given modules and symbols.

```haskell
solutionShouldHideAll [FromModule "Prelude" "head", Module "Data.Set"]
```

### Approximate Equality

#### `shouldBeApprox`

```haskell
shouldBeApprox :: (Fractional a, Ord a, Show a) => a -> a -> Expectation
```

Predefined approximately equal expectation with error margin `1e-6`.

```haskell
sqrt 2.0 `shouldBeApprox` (1.4142135 :: Double)
```

#### `shouldBeApproxPrec`

```haskell
shouldBeApproxPrec :: (Fractional a, Ord a, Show a) => a -> a -> a -> Expectation
```

Create approximately equal expectation with margin.

```haskell
shouldBeApprox' = shouldBeApproxPrec 1e-9
```
