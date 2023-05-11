# Primeros pasos

Cuando tengas el docker corriendo `make start`

1 - Levanta el canister `dfx start --clean --background`

# Multiples proyectos en el mismo canister

Estructura de carpeta

```bash
/app
├── day0
│   └── main.mo
├── day1
│   └── main.mo
│   ...
├── canister_ids.json
└── dfx.json
```

En canister_ids.json tenes algo similar a esto
Indica el  nombre del canister y su internet-computer

```bash
{
  "day1": {
    "ic": "ffff-iisss-aaaaa-zzzz-cai"
  }
}
```

En dfx.json tendras algo similar a esto
Indica donde esta el punto de entrada del programa
```bash
{
    "canisters": {
        "day0": {
            "main": "day0/main.mo",
            "type": "motoko"
        },
        "day1": {
            "main": "day1/main.mo",
            "type": "motoko"
        }
        //...
    }
}
```

Para correr el proyecto del dia0 en el canister ejecutas `dfx deploy day1`
day1 es el nombre del canister (el que esta en dfx.json)  asegurate que en el canister_ids.json tengas el mismo nombre de canister (es el que lo identifica).


# probar llamadas a los actores del canister

en el canister del dia, suponiendo que tenes un actor greet que recibe un parametro podes probarlo con el siguiente comando

`dfx canister call day1 greet '(" world")'`

# apagar canister
Al final apaga el canister con `dfx stop`


# Deployar canister en IC

build arriba
` dfx build --network ic day1`

install arriba
`dfx canister --network ic install day1`

si usas el mismo canister y tiro error forza la reinstalacion
`dfx canister --network ic install day1 --mode reinstall`