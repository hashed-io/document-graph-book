# document-graph-book

Information of the DGE

## Setup

How to setup localy the project.

### Before all

Make sure you have [Rust](https://www.rust-lang.org/tools/install) intalled

Install PlantUML
```bash
sudo apt-get install -y plantuml
```

Setup mdBook
```bash
cargo install mdbook-plantuml
```
## Build

To build the project run the following line
```bash
mdbook build
```


## Deploy

To deploy the project run the following line
```bash
mdbook serve
```