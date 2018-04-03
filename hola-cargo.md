## Que és Cargo?

La pagina web de Crates es el repositori que es publicaran els paquets/llibreries/projectes de Rust. Cargo es una eina per gestionar els teus projectes i els paquets de crates.io

Les principals feines que gestionara Cargo son:

* La compilació de codi i les dependències.

* La descarrega de dependències i control de les seves versions.

* Creació de paquets per a crates.io

* Recopilació de informació bàsica del projecte.



### Instalació:

El cargo s’instal·la automaticament al instal·lar les eines bàsiques de Rust.



### Creant un nou projecte:

Per iniciar un nou projecte de Rust amb Cargo pots usar:

```sh

cargo new hola_mon --bin

```

He agregat el valor --bin perquè estem creant un programa binari. Si creem una biblioteca podem no agregar-ho o usar “--lib”. Això també inicialitza el repositori git per defecte. Si no vol que s’executi sol pot usar la comanda “--vcs none”



### Veiem que ha generat Cargo:

```sh
cd hola_mon

tree .

.
├── Cargo.toml
└── src
    └── main.rs


1 directory, 2 files
```

### Veiem el document "Cargo.toml":
```toml
[package]
name = "hola_mon"
version = "0.1.0"
authors = ["Josep Subils <js@js.gl>"]

[dependencies]
```

Els programadors solen referise a aquest document com el "**manifest**" i sol contenir tota la informació necessària per compilar el projecte.


### El codi
Aquest es el contingut del document "src/main.rs":

```rust
fn main() {
    println!("Hello, world!");
}
```

### Compilar i crear un binari executable
El Cargo ha generat un "Hello, world!" mínim per tu. Anem a compilar-lo:

```sh
cargo build
```

### Executar el binari
Un cop rebuda la confirmació de compilació podem executar el binari resultant que actualment estarà localitzat al directori :

```sh
./target/debug/hola_mon
```

### Compilar i executar en un sol pas
Nosaltres també podem usar "cargo run" per compilar i executar el programa en un sol pas. Si el programa ja estava compilat i no s'ha realitzat cap canvi, el llençara sense tornar a compilar-lo.

```sh
cargo run
```

### Estem preparats!

Si tu estàs preparat per la primera versió de llançament projecte pots usar la següent comanda per poder compilar el projecte amb les funcions de optimitzacio al màxim:

```sh
cargo build --release
```

Aquest cop podrem localitzar el codi al directori al directori de llançament:

```sh
./target/release/hola_mon
```

```sh
Hello, world!
``
