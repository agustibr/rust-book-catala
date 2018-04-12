# El Joc d'endevinar

###Aprenem alguna cosa de Rust!
En el nostre primer projecte implementarem un clàssic problema de programació per a principiants: el joc d'endevinar un nombre. Funciona així: el nostre programa generarà un nombre enter a l'atzar entre 1 i 100. Després ens demanarà que entrem una suposició i ens dirà si és massa gran o massa petit. Un cop haguem encertat ens felicitarà. Sona bé, no? Al llarg de l'exercici aprendrem una mica de Rust. Al capítol següent, "Sintaxi i semàntica", ens sumergirem en les profunditats de cada part.


###Preparant l'entorn
Preparem un projecte nou. Anem al directori dels nostres projectes. Recorda com hem creat l'structura del nostre directori i un cargo.toml per al hello_world? Cargo té un comandament que ho fa per nosaltres. Donem- li una ullada:

```sh
$ cd ~/projectes
$ cd ~/projectes
$ cd ~/projectes
$ cargo new guessing_game --bin $ cd guessing_game
```

Donem el nom del nostre projecte al nou cargo i després la flag --bin, ja que estem fent més un binary que una llibreria.
Revisem el Cargo.toml general:

```toml
[package]
name = "guessing:_game
version = "0.1.0"
authors = ["el teu nom <you@example.com>"]
```

Cargo pren aquesta informació del teu entorn. Si no és correcta aleshores canvia-ho. Finalment, Cargo ha general un 'hello_world' fer a nosaltres. Revisa src/main.rs:

```rust
fn main() {
  println!("Hello, world!");
}
```

Veiem què ens ha compilat Cargo:
```sh
$ cargo build
  compiling guessing_ (file:///home/you/projects/guessing_game)
```

Excel·lent! Torna a obrir src/main.rs. escriurem tot el codi en aquest firxer. abans de moure'ns, deixa que t'ensenyi un comandament de Cargo més: run. Cargo run és com cargo build, però també engega l'executable produit.
Proba:

```sh
$ cargo run
  compiling quessing_ (file///home/you/projects/guessing_game)
    Running 'target/debug/guessing_game' Hello, world!
```

Bona aquesta! El comandament run va molt bé quan necessites iterar ràpidament en un projecte. El nostre joc és com un projecte. Necessitem probar ràpidament cada iteració abans de moure'ns a la següent.
Processant un intent
El primer que hem de fer pel nostre jos d'endevinar és permetre que el nostre jugador faci un intent. Posem-ho en el src/main.rs.

```rust
use std::io;
fn main() {
  println!("Endevina el nombre!");
  println!("Entra un nombre.");
  let mut guess = String::new();
  io::stdin().read_line(&mut guess) .expect("Ha llegit la línia malament");
  println!("Has probat: {}", guess);
 }
```

Aquí hi ha moltes coses! Anem pas a pas.

```rust
use std::io
```

Necessitem agafar el que entri l'usuari i mostrar el resultat com una sortida. Així, necessitem la llibreria io de la llibreria standard. Rust només importa algunes coses per defecte en cada programa, el "preludi". Si no està en el preludi, aleshores ho hauràs d'utilitzar directament. També hi ha un segon preludi, la io prelude, el qual dóna una funció similar: importa-la i ella importa un nombre de coses útils relacionades amb io.

```rust
fn main() {
```

Com has vist abans, la funció main() és un punt d'entrada al teu programa. La sintaxi fn declara una funció nova, els () indiquen que no hi ha arguments, i { comença el cos de la funció. Com no hem inclòs un tipus de retorn, se suposa que () és una tupla buida.

```rust
println!("Endevina el nombre!");
println!("Entra un nombre.");
```

Abans hem après que println! és una macro que imprimeix una cadena a la pantalla.

```rust
let mut guess = String::new();
```

Això s'està posant interessant! Hi ha moltes coses en aquesta petita línia. Del primer que ens adonem és que es tracta d'una sentència let (secció 4, pàgina 43), la qual s'utilitza per a crear 'fixador de variables'. Prenen aquesta forma:

```rust
let foo = bar;
```

Això crea un nou fixador anomenat foo i el fixa al valor var. En molts llenguatges, això s'anomena 'variables', però els fixadors de variables de Rust tenen alguns [have a few tricks up their sleeves]. Per exemple, per defecte són immutables (secció 4, pàgina 85). Per això el nostre exemple utilitza mut: converteix un fixador en mutable, més que en immutable. Let no pren un nom en el seu costat esquerre de l'assignament, actualment accepta un patró (secció 4, pàgina 96). Utilitzarem els patrons més tard. Per ara n'hi ha prou amb això.

```rust
 let foo = 5; //immutable
 let mut bar = 5; // mutable
```

Notem que // comença un comentari fins al final de línia. Rust ignora tot el que està en els comentaris. Ara sabem que let mut guess introdueix un fixador mutable anomenat guess, però hem de veure a l'altre costat de l'assignament = per veure què hi ha inclòs: String::new().
String és un tipus de cadena proporciionada per la llibraria standard. Una String és un bit de text extensible [growable?] codificat en UTF-8.
La sintaxi **::new()** utilitza :: perquè és una "funció associada" d'un tipus particular. És a dir, és més quelcom associalt amb l'String mateixa que no pas una instància particular de String. Alguns llenguatges ho anomenen "mètode estatic". Aquesta funció s'anomena new() peruqè crea una String nova i buida. Trobaràs una funció new() de molts tipus perquè és un nom molt comú per a fer un valor nou d'algun tipus.
continuem:

```rust
io::stdin().read_line(&mut guess) .expect("Error al llegir la linia");
```

Aquí hi ha molt més! Anem pas a pas. La primera línia té dues parts. Veiem la primera:

```rust
io::stdin()
``