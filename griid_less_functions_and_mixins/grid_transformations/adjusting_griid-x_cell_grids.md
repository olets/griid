# Adjusting `.griid-x .cell` grids

#####i. Resizing from one column count to any other arbitrary column count
1. `.griid--resize-one-equal((@treatAs:1,) @target)`
    Resize one equal width
    `.griid--resize-one-equal(@target)` will turn cells in an `.griid-@target` into blocks

1. `.griid--resize-equal(@treatAs:1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))`
    Change the column count of `.griid-x .cell` griids - optionally only targeting grids with a certain column count or targeting only grids with a column count within a certain range
    Default turns cells in *all* `.griid-x` grids into blocks
  -    `.griid--resize-equal(@treatAs)` turns all `.griid-x` grids into `.griid-@target` grids
  -    `.griid--resize-equal(@treatAs, @minColCount)` turns all `.griid-x` grids with at least **@minColCount** columns into `.griid-@treatAs`
  -    `.griid--resize-equal(@treatAs, @minColCount, @maxColCount)` turns all `.griid-x` grids with at least **@minColCount** and at most **@maxColCount** columns into `.griid-@treatAs`

  The resize functions can add or remove columns from a grid.

#####ii. Dropping the column count by one or more

1. `.griid--drop-one((@dropBy:1,) @target)`
    Drops one or more columns from "one" specified grid type.
  -    `.griid--drop-one(@target)` will turn `.griid-@target` into `.griid-(@target-1)`
  -    `.griid--drop-one(@dropBy, @target)` will turn `.griid-@target` into `.griid-(@target-@dropBy)`

1. `griid--drop(@dropBy: 1(, @minColCount: @griid--min-cols(, @maxColCount: @griid--max-cols)))` 
    Default drops one column from all `.griid-x` grids
  - `griid--drop(@dropBy)` drops **@dropBy** columns from all `.griid-x` grids
  - `griid--drop(@dropBy, @minColCount)` drops  **@dropBy** columns `.griid-x` grids that have at least **@minColCount** columns
  - `griid--drop(@dropBy, @minColCount, @maxColCount)` drops **@dropBy** columns from grids with between **@minColCount** and **@maxColCount** columns (inclusive)