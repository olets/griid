## 2.5.2

2016-12-21

Bugfix in compiled css

## 2.5.2

2016-06-15

Bugfix: gutters when transforming between single- and multi-row grids

##2.5.1

2016-06-09

Move the install to the config file. All configuration is now in griid-config

## 2.5

2016-06-09

Renames griid--fz to griid--font-size

## 2.4

2016-06-09

Moves configuration to griid-config.less


## 2.3

2016-06-09

Font size changes: now supports customizing the units. Practical importance: adds rem support

## 2.2.5

2016-06-06

Bugfix in cell width calculation


## 2.2.4

2016-06-03

Bugfix: remove gutters from `.griid-x > .cell` cells when turned into full-width cells


# 2.2.3

2016-06-02

Bugfix: remove gutters from `.griid-x > .cell` cells turned into full-width cells


## 2.2.2

2016-05-24

Bugfix: Removes gutters from full-width cells

## 2.2.1

2016-05-09

- Fixes a bug in griid--resize-unequal-cells (`calc` doesn't support subtracting 0 from another value)
- Fixes a bug in the griid--fraction loop


## 2.2

2016-05-07

Adds support for overriding the default gutter during re/installation

Test suite updates

## 2.1.8

2016-05-07

Nested grid bugfixes


## 2.1.7

2016-03-07

Bugfixes to

- drop
- resize-one-unequal
- resize-unequal

Updates to the test suite

## 2.1.6

2016-03-03

Fixes a LESS bug

## 2.1.5

2016-03-03

- Adds test suite
- Significantly weight reduction

## 2.1

2016-03-02

Adds

- griid--base
- griid--install
- griid--single-row
- griid--inline-alignment

## 2

2016-03-02

- Major refactor of griid to rely on LESS mixins and functions
- Addition of griid-functions for on-the-fly adjustments to grids
