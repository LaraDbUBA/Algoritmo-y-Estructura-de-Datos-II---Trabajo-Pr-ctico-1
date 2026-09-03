### Dudas
- Como expresamos el historial
- Que pasa si tienen igual cantidad de millas (elQueTieneMasMillas)
- Como se registran las 500 millas por Referidor? 
- Promocion con Tope, como registramos el dato
- Hay que agregar la condicion de que las disponibles no sean mayores a las totales
- Preguntar por cambios de consignas
- Que consideran ellos como eliminar del sistema en tope? Se puede volver a activar despues o ya fue para siempre?
- Si se elimina se puede volver a crear otra prommo con el mismo nombre? Tiene que empezar desde 0 el contador?
- Si existe un promo con tope que esta apagada, puede existir una promo sin tope con ese nombre?
- Puede haber una promocion con tope y otra sin tope con el mismo nombre?


### Ideas de predicados extras
- tienenMismasMillasDisponibles
- tienenMismasMillasTotales
- tieneSaldoSuficiente
- NoSuperaMillasTotales
- esPromocionDelSistema
- tienenMismoId
- tienenMismaCategoria
- tienenMismoHistorial

### Ideas de auxiliares extras
- sumaDeMillasAcumuladas
- sumaDeMillasCanjeadas
- sumaDeMillasEnviadas
- sumaDeMillasRecibidas

Para el de acumular millas habria que crear un auxiliar/predicado que chequee que la promocion con tope se elimine si se paso del tope y la deje sino.