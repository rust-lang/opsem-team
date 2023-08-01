## FCPs

Here we track all the FCPs of the team. These reflect consensus decisions and
are thus a useful starting point for figuring out what is (and is not)
guaranteed.

- Stack-allocated 8-aligned objects are insufficiently aligned by MSCV on x86-32.
  [That is indeed UB when such pointers flow to Rust.](https://github.com/rust-lang/rust/issues/112480#issuecomment-1606326864)
