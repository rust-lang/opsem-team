## FCPs

Here we track all the FCPs of the team. These reflect consensus decisions and
are thus a useful starting point for figuring out what is (and is not)
guaranteed.

- Stack-allocated 8-aligned objects are insufficiently aligned by MSCV on x86-32.
  [That is indeed UB when such pointers flow to Rust.](https://github.com/rust-lang/rust/issues/112480#issuecomment-1606326864)
- The validity invariant of integers, floats, bool, thin raw pointers, and char is [as documented here](https://github.com/rust-lang/unsafe-code-guidelines/issues/439).
- The validity invariant of function pointers is [as documented here](https://github.com/rust-lang/unsafe-code-guidelines/issues/440).
- Typed copies [reset all padding bytes to uninitialized memory](https://github.com/rust-lang/unsafe-code-guidelines/issues/301#issuecomment-1661617803).
