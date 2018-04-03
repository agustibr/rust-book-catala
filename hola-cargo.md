## Sobre Cargo i crates.io

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
  




