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
requiere { !esU suarioRegistrado(id, a) ∧a = A0 }
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

