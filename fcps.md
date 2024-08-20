## FCPs

Here we track all the FCPs of the team. These reflect consensus decisions and
are thus a useful starting point for figuring out what is (and is not)
guaranteed.

- Stack-allocated 8-aligned objects are insufficiently aligned by MSCV on x86-32.
  [That is indeed UB when such pointers flow to Rust.](https://github.com/rust-lang/rust/issues/112480#issuecomment-1606326864)
- The validity invariant of integers, floats, bool, thin raw pointers, and char is [as documented here](https://github.com/rust-lang/unsafe-code-guidelines/issues/439).
- The validity invariant of function pointers is [as documented here](https://github.com/rust-lang/unsafe-code-guidelines/issues/440).
- Typed copies [reset all padding bytes to uninitialized memory](https://github.com/rust-lang/unsafe-code-guidelines/issues/301#issuecomment-1661617803).
- Layout [cannot change at runtime](https://github.com/rust-lang/unsafe-code-guidelines/issues/97).
- Unsafe code gets to [assume that `size == stride` in arrays](https://github.com/rust-lang/unsafe-code-guidelines/issues/176).
- The `*` projection (value-to-place conversion) itself is never UB;
  instead, inbounds/alignment checks get [deferred to later during place evaluation](https://github.com/rust-lang/reference/pull/1387).
- `_` patterns in `match` [do not read from the place, they only require place construction itself to succeed without UB](https://github.com/rust-lang/rust/pull/103208#issuecomment-1735947916).
- Atomic loads [can work on read-only memory, but only under some conditions](https://github.com/rust-lang/rust/pull/115577#issuecomment-1731284113).
- Zero-sized memory accesses and offsets [are NOPs](https://github.com/rust-lang/unsafe-code-guidelines/issues/472)
- The validity invariant of [slice wide pointer metadata are defined here](https://github.com/rust-lang/unsafe-code-guidelines/issues/510).
- [Int-to-pointer transmutation is questionable.](https://github.com/rust-lang/rust/pull/122379#issuecomment-1994699439)
- [Redundant StorageDead/StorageLive are legal.](https://github.com/rust-lang/rust/issues/99160#issuecomment-2155924538)
- [`size_of_val` is safe to call on slice-tailed unsized types with a dynamic slice length of 0.](https://github.com/rust-lang/rust/pull/126152#issuecomment-2220159220)
