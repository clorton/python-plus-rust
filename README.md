# python-plus-rust

Rust backing Python package experiment ([reference](https://www.youtube.com/watch?v=jlWhnrk8go0))

* `python3 --version` » "Python 3.10.8"
* `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh` (courtesy of [https://www.rust-lang.org/tools/install])
* create `python3 -m venv .venv` and activate `source .venv/bin/activate` a Python virtual environment
* update `.gitignore` to ignore the virtual environment
* Naïve implementation of fibonacci in Python
* install `maturin` Python package, `python3 -m pip install maturin`
* directory for Rust package, `fibbers`
* in the `fibbers` directory run `maturin init` ... select "pyo3"
* in the `fibbers` directory run `maturin develop`
    * `Cargo.toml`, `pyproject.toml`, and `.github/CI.yml` would be useful if we decide to publish our package.
* take a look at `fibbers/src/lib.rs`
* add in the Rust implementation of fib[onacci]
* run `maturin develop` in the `fibbers` directory (make sure your virtual environment is activated to ensure that the Rust package is installed in the correct environment)

```shell
(.venv) @clorton ➜ /workspaces/python-plus-rust (main) $ ./rustfib.py 30
fibonacci(n)=832040
fibbers.fib(n)=832040

Python μs per call: 256010.23 μs
Python ms per call: 256.01 ms

Rust μs per call: 7571.05 μs
Rust ms per call: 7.57 ms
```

* 256/7.57 = ~34x faster
* build a release version of the code with `maturin develop --release` in the `fibbers` directory

```shell
(.venv) @clorton ➜ /workspaces/python-plus-rust (main) $ ./rustfib.py 30
fibonacci(n)=832040
fibbers.fib(n)=832040

Python μs per call: 256504.47 μs
Python ms per call: 256.50 ms

Rust μs per call: 2527.09 μs
Rust ms per call: 2.53 ms
```

* 256.5/2.53 = ~100x faster

----

## Additional Resources

* [How to Write Python Extensions in Rust with pyo3](https://www.infoworld.com/article/3687744/how-to-write-python-extensions-in-rust-with-pyo3.html)
* [The PyO3 user guide](https://pyo3.rs/v0.19.0/)
* [Rust bindings for the NumPy C-API](https://github.com/PyO3/rust-numpy)

