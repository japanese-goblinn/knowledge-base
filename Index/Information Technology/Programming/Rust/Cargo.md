- **Notes**
	> By convention, cargo will look for integration tests in the `tests/` directory. Similarly, it will look for benchmarks in `benches/`, and examples in `examples/`. These conventions also extend to your main source code: libraries have a `src/lib.rs` file, the main binary is `src/main.rs`, or, if there are multiple binaries, cargo expects them to be in `src/bin/<name>.rs`. 
	- `cargo` - build tool (like [Swift Package Manager](../Apple%20Technologies/Apple%20Platform%20Specifics/Apple%20Developer%20Tools/Dependencies/Swift%20Package%20Manager.md))
		```bash
		cargo new <project_name>
		cargo build
		cargo run
		cargo check # check for errors, faster then compiling whole app
		cargo update
		```
	- [libraries should ignore `Cargo.lock` but binaries/applications should check-in `Cargo.lock`](https://doc.rust-lang.org/cargo/faq.html#why-do-binaries-have-cargolock-in-version-control-but-not-libraries)
- **Links**
	- [The Manifest Format - The Cargo Book](https://doc.rust-lang.org/cargo/reference/manifest.html)

