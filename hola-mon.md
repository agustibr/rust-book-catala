## Hola Món

Ara que tens instal·lat el compilador i les eines necessàries es el moment de confirmar que tot ha funcionat be i crear el teu primer programa. Si no ets nou en el mon de la informàtica sabràs que existeix la tradició de escriure un programa que llenci un missatge en pantalla saludant.

Creem un document de rust que es dirà ‘hola.rs’ mitjançant el nostre editor de codi preferit.\(Ja publicare una petita llista

Agafem l’editor de codi que preferim i editarem el document ‘hola.rs’

Al seu interior afegim:

```rust
fn main() {
    println!("Hello, world!");
}
```

Per compilar el nostre primer programa:

```sh
josep@rs:~$ rustc hola.rs
```

Obtindrem el binari que podrem executar:

```sh
josep@rs:~$ ./hola
```



