# Adjusting `.griid .cell-n-d` grids

1. `.griid--resize-one-unequal((@treatAsNumerator:1, @treatAsDenominator:2,) @targetNumerator, @targetDenominator)`
Resize one fractional-width cell type
  - `.griid--resize-one-unequal(@targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` cells into `.cell-1-2`    
  - `.griid--resize-one-unequal(@treatAsNumerator, @treatAsDenominator, @targetNumerator, @targetDenominator)` turns `.cell-@targetNumerator-@targetDenominator` into `.cell-@treatAsNumerator-@treatAsDenominator`


1. `.griid--resize-unequal(@treatAsNumerator:1, @treatAsDenominator:2(, @numeratorOfLargest, @denominatorOfLargest))`
  -    Resize all fractional smaller than or equal to target
  -    Default turns all fractional widths into `.cell-1-2`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator)` turns all fractional widths into `cell-@treatAsNumerator-@treatAsDenominator`
  -    `.griid--resize-unequal(@treatAsNumerator, @treatAsDenominator, @numeratorOfLargest, @denominatorOfLargest)` turns all fractions equal to or smaller than **@numeratorOfLargest**/**@denominatorOfLargest** into `cell-@treatAsNumerator-@treatAsDenominator`

