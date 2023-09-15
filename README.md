# case
a case conversion and detection library in zig

cases supported: camelCase, PascalCase, snake_case, CONSTANT_CASE, kebab-case, Header-Case, lower case, UPPER CASE, Capital Case

## [lib.zig](src/lib.zig)

uses readers and writers throughout. supports non-allocating and comptime use. 

* `to(case, reader, writer, opts)` - converts to case from reader into writer
* `of(text)` - return `Case` of text. may be 'unknown'.
* `bufTo(buf, case, text, opts)` - writes converted text to buf in specified case
* `allocTo(allocator, case, text, opts)` - allocates a buffer and writes converted text to buffer in specified case
* `allocZTo()` - same as allocTo() but null terminated
* `comptimeTo(case, text, opts)` - allocates buffer at comptime
* `comptimeToLen(case, text, opts, len)` - same as comptimeTo() but allows user to specify buffer len
* `length(case, text, opts)` - returns length needed to convert text to case
* `upper(reader, writer, opts), camel(reader, writer)` - conversion functions for each case. upper(), lower() and capital() have an additional opts param.
* `isCamel(text)` - true if text case is camel. similar methods for each case
* `opts`
  * fill - string used to replace non alpha numeric characters.  default empty.  when empty, don't replace non alpha numeric characters.
  * apostrophe - keep / remove.  default keep.

## c api

* [c_api.zig](src/c_api.zig) - exports methods similar to all public zig methods above
* [case.h](src/case.h)
  * `Case` enum guaranteed to be in sync with `Case` enum in lib.zig

## tests

`$ zig build test` runs the following
  * [tests.zig](src/tests.zig) - pretty thorough zig tests which also test the c api methods
  * [test.c](src/test.c) - a small demo program which exercises the c api


## build 
`$ zig build`

creates `zig-out/lib/libcase.a` and `zig-out/include/case.h`

* zig package manager support

## related
[nbubna/Case](https://github.com/nbubna/Case)

## inspiration
thanks to [cmgriffing](https://github.com/cmgriffing) for suggesting this
