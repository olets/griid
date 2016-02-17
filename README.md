# griid
Griid is an easy-to-use grid system which supports three grid types: single full-width single-row grids  with cells of equal width; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, if the last row of the grid isn't filled its cells will be center aligned

Usage:

1. Three types of rows are supported

  A.	Automatic equal-width cells, filling one entire row.

		<div class="griid">
			<div class="cell">1-</div>
			<div class="cell">2-</div>
			<div class="cell">3-</div>
		</div>
	
		|	  1-	  |	  2-	  |	  3-	  |


	B. Automatic equal-width cells, with a specified number of columns per row.

		<div class="griid-COUNT">
			<div class="cell">...</div>
			<div class="cell">...</div>
			...
		</div>

	where COUNT is an integer between 2 and @griid-max_equal_columns (inclusive). All cells will be the same width, 1/COUNT the width of the row.

	For example:

		<div class="griid-2">
			<div class="cell">1</div>
			<div class="cell">2</div>
			<div class="cell">3</div>
		</div>
	
		|		  1		  |		  2		  |
				|		  3		  |


	C. Cell fractional width specified on a per-column basis, with under-full rows aligned centered.

		<div class="griid">
			<div class="cell-X-N">...</div>
			...
		</div>

	where X is an integer less than N,
	and N is an integer between 2 and `@griid-min_fractional_width` (inclusive).
	Cells will be X/N the width of the row. Cells' widths are independent of each other.

	!Important: Because the styles don't know what cell widths you've used, you must add `.row-end` to the last cell of each row

		<div class="griid">
			<div class="cell-1-4">1</div>
			<div class="cell-1-2">2</div>
			<div class="cell-1-4 row-end">3</div>
			<div class="cell-1-3">2</div>
		</div>
		|	 1	 |		  2		  |	 3	 |
   		            |      4     |

	Full-width cells are cell-N-N or `.cell-full`, and do not require `.row-end`


2. For multi-row grids (B and C), columns are separated by `@griid-cell_spacing`


3. In all cases,
	
	Cells are separated by the griid-cell_spacing value,
	
	Cells are vertically centered.
	- Add `.top` or `.bottom` to a column to customize its vertical alignment
	- Add `.top` or `.bottom` to a row or row group to customize the default for its child columns
	- Override upstream up customizations by adding `.top`, `.middle`, or `.bottom` to a row or column



###Acknowledgements:
This started as a modification of Joel Sutherland's "grid-items" grid system
