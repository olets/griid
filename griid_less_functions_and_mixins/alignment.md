# Alignment

1. `.griid--vertical-align(@args:@griid--item-v-align)`

    Change the vertical alignment of cell contents
    Default re-initializes
	
	There are also shorthand mixins:
	`.griid--top` (shorthand mixin for `.griid--vertical-align(top)`)
	`.griid--middle` (shorthand mixin for `.griid--vertical-align(middle)`)
	`.griid--bottom` (shorthand mixin for `.griid--vertical-align(bottom)`)
	
1. `.griid--orphan-align(@alignment:@griid--orphan-h-align)`

    Change how orphan cells in multi-row grids are aligned
    Default re-initializes
    
    And shorthand mixins:
	`.griid--left` (shorthand mixin from `.griid--orphan-align(left)`)
	`.griid--center` (shorthand mixin from `.griid--orphan-align(center)`)
	`.griid--right` (shorthand mixin from `.griid--orphan-align(right)`)