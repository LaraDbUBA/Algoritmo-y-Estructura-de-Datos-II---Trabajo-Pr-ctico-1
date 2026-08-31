<ACLARACION><IMPORTANTE>: Esto se hizo rápido y faltan muchas modificaciones, en base a los Tad y Observadores disponibles. 

Algunas cosas no se entendieron y se hicieron en base a lo que se entendia y **Seguramente** se tienen que modificar.

**IMPORTANTE**: Usar conjuntos es la mejor opcion? No es mejor {usuarioId: [INTEGER, INTEGER, STRING, BOOL, INTEGER,TUPLA, ETC]} o
[[usuarioID, Integer, Integer, BOOL, (tupla)]]

A que quiero llegar es que no es mejor usas un observador o varios entre diccionarios y listas en lugar de usar un conjunto? 



### Acumular Millas:

`proc acumularMillas`(in usuario : Usuario, in distancia : Z, in nombrePromo : char, inout a :AirMiles) {
`requiere` {usuario ∈a.usuarios∧a = A0∧distancia ≥0∧esP romoActiva(nombreP romo, a) }
`asegura` {  }
`asegura` { `Millas` incrementa las Millas Totales del Usuario }
`asegura` { `Millas` incrementa las Millas disponibles } 
`asegura` { `Millas` hace incrementar la  `categoriaUsuario` si se cummplen las condiciones}
`asegura` { La transaccion se registra en el `historialUsuario` ^ distanciaVolada ^ millasGanadas }

//La transacción se registra en el historial del usuario, incluyendo la distancia volada, las millas ganadas, el nombre de
la promoci´on aplicada y el factor de promoci´on que se aplic´o// => <REVISAR ESTO>

}

`aux millas`(in ) : Z =  `distancia` * `factorCategoria`(usuario) * `factorPromocion`(nombrePromo)

`aux factorCaterotia`(usuario) : Z = ...

`aux factorPrommocion`(nombrePromo) : Z = ...


### CanjearMillas

`proc canjearMillas`(in usuario: Usuario, in millas: Z) : AirMiles {
`requiere` { usaurio.millasDisponibles >= millas }
`asegura` { algo }
`asegura`{usuario.millasTotales}
}

### TransferirMillas

`proc transferirMillas`(usuarioUno: Usuario, usuarioDos, millas: Z) : AirMiles {
requiere { UsuarioUno.id /= UsuarioDos.id ^ usuarioUno.millasDisponibles >= millas}
asegura { algo }
}

***CONSULTA***: Se debe registrar la transaccion en el historial del usuario, incluyendo la cantidad de millas transferidas, el usuario destino, y el usuario origen

### ConsultarSaldo

`proc consultarSaldo`(in usuario: Usuario) : Z {
    `requiere` { que el usuario exista }
    `asegura` {Mostrar la tantidad de millasDel Usuario}  => <res = usuario.millasDIsponibles>
}


### ConsultarCategoria

`proc consultarCatogoria` (in usuario: Usuario, in millas: Z, in millasTotales: Z) : Char {
    `requiere` {//}
    `asegura` {}
    `asegura` {}
    `asegura` {}

}

### IniciarPromocion
No falta la entonces luego despues del cuantificador universal?
NO falta un y luego despues del cuatificador existencial?

### General
En muchos lados es correcto que lo que OUT sea AirMiles? Habría que revisar cada caso por si acaso.