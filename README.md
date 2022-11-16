## Rust

#### Instalar rust
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Añadir el PATH o actualizar `.profile` y `.cargo/env`. Los PATH ya deberían estar añadidas en los archivos.
```bash
source ~/.profile
source ~/.cargo/env

# validar
rustc --version
# salida
ustc 1.65.0 (897e37553 2022-11-02)
```
Actualizar rust con `rustup update`. Para desinstalar `rustup self unistall`.

Herramientas de compilación y gestión de paquetes.
- Contruir un proyecto con `cargo build`
- Ejecutar un proyecto `cargo run`
- Ejecutar los test de un proyecto `cargo test`
- Generar documentación de un proyecto `cargo doc`
- publicar biblioteca en _crates.io_ con `cargo publish`
- Ver la versión de rust y cargo `cargo --version`

#### Probrar rust creando un proyecto simple con `cargo new hello-rust`.
```bash
tree hello-rust

# resultado
hello-rust
├── Cargo.toml
└── src
    └── main.rs
```
`Cargo.toml` es el archivo de manifestación de rust. Es donde se mantienen los metadatos del proyecto, así como la declaración de dependencias.

`src/main.rs` donde se escribe el código.

Ejecutar el proyecto:
```bash
cd hello-rust
cargo run

# resultado
Compiling hello-rust v0.1.0 (/home/bender/Documentos/bending/git/rust/hello-rust)
    Finished dev [unoptimized + debuginfo] target(s) in 8.51s
     Running `target/debug/hello-rust`
Hello, world!
```

#### Añadir dependencias
[crates.io](https://crates.io/)

Se usa la herramienta de copiado de la página para luego añadirla a `Cargo.toml`.
```toml
[package]
name = "hello-rust"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/         manifest.html

[dependencies]
ferris-says = "0.3.1"
```
Ejecutar `cargo build` para instalar las dependencias. Este comando creá un archivo `Cargo.lock`, contiene una lista de las versiones exactas de todas las dependencias usadas en local. Para usar la dependencia se añade al archivo `main.rs`: 
```rs
use ferris_say::say;
```
Usa la función `say` que exporta de `ferris_says`.

#### Pequeña aplicación en rust
Expandir el archivo `src/main.rs`:
```rs
use ferris_says::say; // from the previous step
use std::io::{stdout, BufWriter};

fn main() {
    let stdout = stdout();
    let message = String::from("Hello fellow Rustaceans!");
    let width = message.chars().count();

    let mut writer = BufWriter::new(stdout.lock());
    say(message.as_bytes(), width, &mut writer).unwrap();
}
```
Ejecutar `cargo run`. Marco error, resolver más adelante.

#### test
