# Hspec Codewars

Utility functions for testing on Codewars with Hspec.

## Functions

### Blacklisting

```haskell
solutionShouldHide :: Hidden -> Expectation

-- solutionShouldHide $ FromModule "Prelude" "head"
```
Check that solution hides a module or a symbol from a module.

```haskell
solutionShouldHideAll :: [Hidden] -> Expectation

-- solutionShouldHideAll [FromModule "Prelude" "head", Module "Data.Set"]
```
Check that solution hides all of given modules and symbols.

### Approximate Equality

```haskell
shouldBeApprox :: (Fractional a, Ord a, Show a) => a -> a -> Expectation

-- sqrt 2.0 `shouldBeApprox` (1.4142135 :: Double)
```
Predefined approximately equal expectation with error margin `1e-6`.

```haskell
shouldBeApproxPrec :: (Fractional a, Ord a, Show a) => a -> a -> a -> Expectation

-- shouldBeApprox' = shouldBeApproxPrec 1e-9
```
Create approximately equal expectation with margin.
