#griid
##The greedy grid that tries to do it all with LESS

griid is a grid system with automatic rows. You can use the processed griid.css file on its own, but to take advantage its full usefulness you'll need LESS.

Supports IE > 8

griid supports three grid types: single full-width single-row grids  with cells of equal width; multi-row grids with a specified number of equal-width columns; and multi-row grids with fraction-of-the-grid-width cell widths specified per-cell. In the latter two cases, you can control the horizontal alignment of orphan cells (cells in non-full last rows)

Demos at [http://olets.github.io/griid/](http://olets.github.io/griid/)

###Markup

1. Three types of rows are supported

  A.	Automatic equal-width cells, filling one entire row.

		<div class="griid">
			<div class="cell">1</div>
			<div class="cell">2</div>
			<div class="cell">3</div>
		</div>
	
		|     1     |     2     |     3     |


	B. Automatic equal-width cells, with a specified number of columns per row.

		<div class="griid-COLUMNCOUNT">
			<div class="cell">...</div>
			<div class="cell">...</div>
			...
		</div>

	where COLUMNCOUNT is an integer between `@griid--min-cols` and `@griid--max-cols` (inclusive). All cells will be the same width, 1/COLUMNCOUNT the width of the row.

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
			<div class="cell-N-D">...</div>
			...
		</div>

	where N is an integer less than D,
	and D is an integer between `@griid--min-cols` and `@griid--max-cols` (inclusive).
	Cells will be N/D (numerator/denominator) the width of the row. Cells' widths are independent of each other.

	**! Important**: Because the styles don't know what cell widths you've used, you must add `.row-end` to the last cell of each row

		<div class="griid">
			<div class="cell-1-4">1</div>
			<div class="cell-1-2">2</div>
			<div class="cell-1-4 row-end">3</div>
			<div class="cell-1-3">2</div>
		</div>
		|	 1	 |		  2		  |	 3	 |
   		            |      4     |

	Full-width cells are `.cell-1-1` or `.cell-full`, and do not require `.row-end`

###Configuration

- For multi-row grids (B and C), columns are separated by `@griid-gutter` and rows are separated by `@griid-row-spacing`, and orphan cells are horizontally aligned following `@griid--orphan-h-align`


- In all cases, cells are vertically aligned by `@griid--item-v-align`.
	- Add `.top`, `.middle`, or `.bottom` to a cell to control its vertical alignment
	- Add `.top`, `.middle`, or `.bottom` to a grid to control the default for its child cells

- The base font size inside cells is `@griid--font-size`


###Acknowledgements:
This started as a modification of a project by Joel Sutherland's "grid-items" grid system