## Rust

#### Istalar rust
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Añadir el PATH o actualizar `.profile` y `.cargo/env`. Las path ya deberían estar añadidas en los archivos.
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
