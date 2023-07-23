# Feedreader

This is my second go at creating an rss/atom feedreader web application.

The first attempt, [rss_r](https://github.com/Wcubed/rss_r), used egui on the frontend. However, this wasn't very web-friendly, and didn't work all that well on mobile.
So this version uses [leptos](https://github.com/leptos-rs/leptos/tree/main), both to improve upon the previous version, and as an excuse to get familiar with that library.

Run `cargo leptos watch` in this directory to start the web server. If you don't have cargo-leptos: `cargo install cargo-leptos`.

## Compiling for Release
```bash
cargo leptos build --release
```

Will generate your server binary in target/server/release and your site package in target/site

## Testing
```bash
cargo leptos end-to-end
```

```bash
cargo leptos end-to-end --release
```

Cargo-leptos uses Playwright as the end-to-end test tool.  
Tests are located in end2end/tests directory.

## Executing a Server on a Remote Machine Without the Toolchain
After running a `cargo leptos build --release` the minimum files needed are:

1. The server binary located in `target/server/release`
2. The `site` directory and all files within located in `target/site`

Copy these files to your remote server. The directory structure should be:
```text
start-axum
site/
```
Set the following environment variables (updating for your project as needed):
```text
LEPTOS_OUTPUT_NAME="start-axum"
LEPTOS_SITE_ROOT="site"
LEPTOS_SITE_PKG_DIR="pkg"
LEPTOS_SITE_ADDR="127.0.0.1:3000"
LEPTOS_RELOAD_PORT="3001"
```
Finally, run the server binary.
