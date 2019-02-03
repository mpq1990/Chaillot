# Chaillot Server
## Preconditions
You need to install [Rust](https://www.rust-lang.org/tools/install).

## Let it run
To run the server for development (without auto reload):
`cargo run`

### Auto Reload Mode for Development
First install the prerequisite: `cargo install systemfd cargo-watch`

After this you can run the application with auto reload for development:  
`systemfd --no-pid -s http::3000 -- cargo watch -x run`

*Please note:*
The auto reload of the server application is only happening on the server side.
You still have to refresh on the client side.

In case you want to know more about it, 
[these instrcutions were followed...](https://actix.rs/docs/autoreload/)
 