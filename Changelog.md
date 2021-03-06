> Legend:
  - feat: A new feature
  - fix: A bug fix
  - docs: Documentation only changes
  - style: White-space, formatting, missing semi-colons, etc
  - refactor: A code change that neither fixes a bug nor adds a feature
  - perf: A code change that improves performance
  - test: Adding missing tests
  - chore: Changes to the build process or auxiliary tools/libraries/documentation

## 0.8.0
- fix: make the reader borrow the namespace buffer so it can be used repetitively
- refactor: bump dependencies

## 0.7.3
- fix: fix Event::Text slice always starting at the beginning of the buffer

## 0.7.2
- perf: faster unescape method
- docs: update readme
- refactor bump encoding_rs to 0.6.6

## 0.7.1
- style: rustfmt
- refactor: remove from_ascii crate dependency

## 0.7.0
- style: rustfmt
- fix: {with,extend}_attributes usage
- feat: add naive `local_name` function

## 0.6.2
- fix: another overflow bug found with cargo-fuzz
- refactor: update dependencies

## 0.6.1
- fix: fix an overflow found with cargo-fuzz

## 0.6.0
Major refactoring. Breaks most of existing functionalities
- refactor: replace `XmlReader` with a non allocating `Reader` (uses an external buffer)
- refactor: replace `XmlnsReader` iterator by a simpler `Reader::read_namespaced_event` function
- refactor: replace `UnescapedAttribute` with a new `Attribute` struct with `unescape` functions
- feat: support xml decodings
- refactor: remove the `AsStr` trait: user must use `unescape_and_decode` fns when necessary
  (alternatively, run `unescape` and/or `Reader::decode`)
- refactor: module hierarchies
- refactor: replace `Element`s with several per event structs `BytesStart`
- perf: unescape: use from-ascii crate instead to get ascii codes without string validation
- refactor: rename `XmlWriter` to `Writer` and provide a way to write `&[u8]` directly
- refactor: adds @vandenoever changes to save some namespaces allocations
- refactor: adds error-chain and remove `ResultPos` (user can still use `Reader::buffer_position` if needed)

## 0.5.0
- feat: apply default namespaces (`xmlns="..."`) to unqualified elements
- fix: scope for namespace resolution on empty elements
- fix: parsing of `>` in attribute values

## 0.4.2
- feat: add `into_unescaped_string`
- refactor: remove RustyXML benches
- docs: redirect to docs.rs for documentation
- docs: add examples in lib.rs

## 0.4.1
- feat: add `read_text_unescaped`
- fix: fix tests

## 0.4.0
- fix: fix attributes with `=` character in their value
- perf: inline some local functions

## 0.3.1
- feat: set default to `expand_empty_elements = true`
- fix: fix all broken tests because of `Empty` events

## 0.2.5 - 0.3.0 (yanked)
- feat: Add support for `Empty` event

## 0.2.4
- test: add most tests from xml-rs crate

## 0.2.3
- fix: do not write attributes on `Event::End`
 
## 0.2.2
- refactor: code refactoring, split largest functions into smaller ones
- refactor: use `Range` instead of `usize`s in `Element` definition
- docs: fix typo

## 0.2.1
- feat: add `Clone` to more structs
- style: apply rustfmt

## 0.2.0
- refactor: change `from_str` into impl `From<&str>`
- feat: support `Event::DocType`
- feat: add `.check_comments` to check for invalid double dashes (`--`) in comments
- fix: check that all attributes are distincts

## v0.1.9
- feat: return more precise index when erroring
- feat: have `Attributes` iterate ResultPos instead of `Result`
- feat: provide functions to unescape `&...;` characters (`.escaped_content` and `.escaped_attributes`)
- fix: have namespace resolution start one level higher

## v0.1.8
- feat: add `XmlnsReader` to iterate event and resolve namespaces!
- docs: better documentation (in particular regarding `Element` structure and design)
- test: add benchmarks, with xml-rs for a reference

## 0.1.7
- feat/fix: add `Event::PI` to manage processing instructions (`<?...?>`)
- test: add test with a sample file

## 0.1.6
- feat: parse `Event::Decl` for xml declaration so we can have `version`, `encoding` ...
- refactor: rename `position` into `buffer_position` because it sometimes conflicted with `Iterator::position`
- test: add test for buffer_position

## 0.1.5
- feat: add buffer position when erroring to help debuging (return `ResultPos` instead of `Result`)
- test: add travis CI
- docs: add merrit badge and travis status

## 0.1.4
- feat: improve Element API with new, with_attributes, push_attribute
- feat: always return raw `&[u8]` and add a `AsStr` trait for conversion

## 0.1.3
- feat: add helper functions
- feat: add `XmlWriter` to write/modify xmls
- feat: use `AsRef<[u8]>` when possible

## 0.1.2 - 0.1.1
- test: add tests
- feat: add `with_check`
