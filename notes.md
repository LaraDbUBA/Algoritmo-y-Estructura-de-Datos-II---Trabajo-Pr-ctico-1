### Dudas
- Como expresamos el historial
- Que pasa si tienen igual cantidad de millas (elQueTieneMasMillas)
- Como se registran las 500 millas por Referidor? 
- Promocion con Tope, como registramos el dato
- Hay que agregar la condicion de que las disponibles no sean mayores a las totales
- Preguntar por cambios de consignas
- 

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