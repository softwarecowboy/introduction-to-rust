# Introduction to Rust Programming Language

A comprehensive presentation about Rust programming language created with [presenterm](https://github.com/mfontanini/presenterm). This presentation covers Rust fundamentals, its history, key features, and practical examples.



## Learning Resources

### Official Rust Documentation

- **[The Rust Programming Language Book](https://doc.rust-lang.org/book/)** - The official Rust book, perfect for beginners
- **[Rustlings](https://github.com/rust-lang/rustlings)** - Small exercises to get you used to reading and writing Rust code
- **[Rust Standard Library Documentation](https://doc.rust-lang.org/std/)** - Complete reference for the Rust standard library
- **[Rust by Example](https://doc.rust-lang.org/rust-by-example/)** - Learn Rust through practical examples

## About This Presentation

This presentation is designed to introduce developers to the Rust programming language. It includes:
- Brief history of Rust
- Core language features and concepts
- Practical examples and demonstrations
- Resources for further learning

The presentation is written in Markdown format and can be presented directly in the terminal using `presenterm`.

## Prerequisites

### Installing Kitty Terminal

For the best presentation experience with image support, we recommend using [Kitty terminal](https://sw.kovidgoyal.net/kitty/).

#### macOS

```bash
# Using Homebrew
brew install --cask kitty

# Or using curl
curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin
```

#### Linux

```bash
# Using curl (recommended)
curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin

# Ubuntu/Debian
sudo apt install kitty

# Fedora
sudo dnf install kitty

# Arch Linux
sudo pacman -S kitty
```

### Enabling Image Views in Presenterm

To enable image rendering in the presentation:

1. **Use Kitty Terminal** - Kitty has the best support for the Kitty graphics protocol
2. **Run presenterm** - Simply execute:
   ```bash
   presenterm content.md
   ```

Images will automatically display inline when using a compatible terminal like Kitty.

## Running the Presentation

```bash
# Install presenterm
cargo install presenterm

# Run the presentation
presenterm content.md

# Or with custom settings
presenterm content.md --theme dark
```

### Community

- **[Rust Poland LinkedIn Group](https://www.linkedin.com/company/rust-poland)** - Connect with the Polish Rust community

## Additional Resources

- [Rust Playground](https://play.rust-lang.org/) - Try Rust online
- [Crates.io](https://crates.io/) - The Rust package registry
- [This Week in Rust](https://this-week-in-rust.org/) - Weekly newsletter
- [Awesome Rust](https://github.com/rust-unofficial/awesome-rust) - Curated list of Rust resources

## Contributing

Feel free to fork this repository and adapt the presentation for your own needs!

## License

See [LICENSE](LICENSE) file for details.
