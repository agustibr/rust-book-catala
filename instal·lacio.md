## Instal·lació

Lo primer que necessitaràs per instal·lar Rust es tenir connexió a internet per poder descarregar-lo.

Instal·lacio a Linux o al Mac  
Si tu estàs utilitzant Linux o Mac tot el que necessites es obrir la consola i escriure això:

```
curl https://sh.rustup.rs -sSf | sh
```

#### Exemple del procediment:

```
josep@rs:~# curl https://sh.rustup.rs -sSf | sh
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust programming 
language, and its package manager, Cargo.

It will add the cargo, rustc, rustup and other commands to Cargo's bin 
directory, located at:

  /josep/.cargo/bin

This path will then be added to your PATH environment variable by modifying the
profile file located at:

  /josep/.profile

You can uninstall at any time with rustup self uninstall and these changes will
be reverted.

Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Es confirma que es vol prosseguir la instal·lació. En el meu cas les rutes que proposa em semblen correctes així que polsaré 1.

```
info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
info: latest update on 2017-11-23, rust version 1.22.1 (05e2e1c41 2017-11-22)
info: downloading component 'rustc'
 38.5 MiB /  38.5 MiB (100 %)   5.2 MiB/s ETA:   0 s                
info: downloading component 'rust-std'
 54.2 MiB /  54.2 MiB (100 %)  11.9 MiB/s ETA:   0 s                
info: downloading component 'cargo'
info: downloading component 'rust-docs'
info: installing component 'rustc'
info: installing component 'rust-std'
info: installing component 'cargo'
info: installing component 'rust-docs'
info: default toolchain set to 'stable'

  stable installed - rustc 1.22.1 (05e2e1c41 2017-11-22)


Rust is installed now. Great!

To get started you need Cargo's bin directory ($HOME/.cargo/bin) in your PATH 
environment variable. Next time you log in this will be done automatically.

To configure your current shell run source $HOME/.cargo/env
josep@rs:~$
```

Ja ha acabat! Alerta t’informa que s’ha de configurar el PATH. Nomes has d’executar la comanda que et diu el missatge de confirmació:

```sh
source $HOME/.cargo/env
```

Aquest s’encarregara d’agregar al teu document “~/.profile” el PATH que correspon a la carpeta dels binaris on s’ha insta-lat.  
Per comprovar els resultats:

```
josep@rs:~$ cargo --version
cargo 0.23.0 (61fa02415 2017-11-22)
josep@rs:~$
```

### Instal·lació des-de sistemes de paquets

Per descomptat també hi ha paquets per Debian i altres distribucions. En aquest sentit jo sempre intento escollir les eines que et dona la teva distribució.  
 
La elecció es basa en la dependència de versions que pugui tenir i en el coneixement de les versions. Solc confiar en el Cargo, que es sistema de versions que utilitza rust per actualitzar i gestionar el seu compilador i paquets.  

També dependrà del tipus d’entorn on s’instal·li ja que a vegades certes distribucions poden donar un suport mes elevat de seguretat i estabilitat per sobre de les novetats del llenguatge.

Si ets un programador altament actiu amb curiositat per rust segur que estaràs alerta de les novetats que incorpora cada versió del compilador i sempre usaràs mes actual.
Prova diferents versions. Tot es una experiència.

