`Este es el que escribiste vos Lara`
proc registrarUsuario(inout a : AirMiles, in id : Z) {
requiere { !esU suarioRegistrado(id, a) ∧a = A0 }
asegura { #a.usuarios = #A0.usuarios + 1 }
asegura {(∀u : Usuario) (esU suarioRegistrado(u.id, A0) →esU suarioRegistrado(u.id, a))
}
asegura {(∃u : Usuario) (!esU suarioRegistrado(u.id, A0)∧esU suarioRegistrado(u.id, a)∧
u.id = id ∧ u.millasDisponibles = 0 ∧ u.millasT otales = 0 ∧ u.historial = [] ∧
u.categoria =′Bronce′) }
asegura { a.promociones = A0.promociones }
}


`No es mejor modificarlo asi:`
proc registrarUsuario(inout a : AirMiles, in id : Z) {
requiere { !esU suarioRegistrado(id, a0) ∧a = A0 } <NO SE SI ES A0 O a dentro de uruarioRegistrado>
asegura { #a.usuarios = #A0.usuarios + 1 }
asegura {(∀u : Usuario)(u ∈ A0.usuarios → u ∈ a.usuarios)
}
}
asegura { (∃u : Usuario)(u ∉ A0.usuarios ∧ u ∈ a.usuarios ∧
          u.id = id ∧ u.millasDisponibles = 0 ∧ u.millasTotales = 0 ∧
          u.historial = ⟨⟩ ∧ u.categoria = 'Bronce') }
asegura { a.promociones = A0.promociones }



- Asi como esta actualmente solo nos estaráimos fijando que el ID este pero no que este o no todo lo que represente a usuarios, como sus millas o su historial. Yo lo pense asi porque asi al "objeto" si se le puede llamar asi en su conjunto se sigue manteniendo 

- No habría que modificar lo de Promociones y Promociones con Tope? Claude me contesto con estas preguntas para orientarme y un poco de razón creo que tiene:

Una promoción con tope, ¿está en promociones además de en promocionesConTopeActivas? Si está en las dos y se elimina, ¿se elimina de las dos?
Si se eliminó por tope, ¿iniciarPromocion con ese nombre la puede volver a crear? ¿Y el acumulado arranca de cero otra vez?
Si está en promociones con estado = True pero ya fue eliminada de promocionesConTopeActivas, ¿está activa o no?


--------------------------------------------------------------------------------------------------------

<OLVIDATE DE LO TODO LO SIGUIENTE, DEPENDE DE LAS DUDAS>


<PROMOCION>
Creo que se me ocurrio y se puede juntar modificando la estructura de promociones y agregandole a lo último una lista
La lista vacia representa para los que no tienen tope y cuando la lista se abre ejemplo [A,B]: A sería el tope y B las millas que se van acumlando o eso que piden para que tenga como contador

`Dejo la estructura mas o menos escrita de que es lo que pienso pero creo que se podría hacer algo asi:`


`proc iniciarPromocion`(in nombre : String, in factor : Z, inout a : AirMiles) {
`requiere` { factor ≥1 ∧ a = A0 }

`asegura` {(existe un p : promocion) y luego (p no pertenece a promociones y p.nombre = nombre ∧
p.factor = factor ∧p.estado = True ^ p.tope = [])}

- O sea en este de arriba quiero decir que si no esta, entonces se crea uno nuevo con la lista vacia

`asegura` {Y aca iria uno mismo que indica que existe pero que lo unico que hace es cambiar el false por un true}
`asegura` {elRestoDeP romocionesSeM antienenIgual(nombre, A0, a)∧elRestoDeP romocionesSeM antienenIgual(nombre, a, A0)
}
`asegura` {a.usuarios = a0.usuarios}



proc iniciarPromocionConTope(in nombre : char, in f actor : Z, in tope : Z, inout a :
AirMiles) : AirMiles {
requiere { a = A0 ∧f actor ≥0 ∧tope ≥0 }
asegura {elRestoDeP romocionesSeM antienenIgual(nombre, A0, a)∧elRestoDeP romocionesSeM antienenIgual(nombre, a, A0)
}
}

