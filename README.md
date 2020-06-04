# qmp5
![alternative text](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/ivojawer/qmp5/master/diagrama.txt)


### Guardarropas compartidos
No pude encontrar una clase signifcativa que tenga esta responsabilidad, ya que una clase usario no tendria mucho sentido. La manera de crear un guardarropa compartido con este diseño seria en algun lugar tener:
```
crearGuardarropaCompartido(descripcion, otrosUsuarios){
  otrosUsuarios.add(this)
  otrosUsuarios.foreach(usuario=>usuario.agregarGuardarropa(new Guardarropa(descripcion, [])
}
```
o algo por el estilo.


Sobre los cambios/sugerencias, fui por el lado de tener objetos inmutables por todos sus beneficios. Para deshacerlos cada uno produce un cambio opuesto.
Por ejemplo, 
En AgregarPrenda:
`opuesto() = new SacarPrenda(this.prenda)`

En guardarropa:
`deshacerSugerencia(sugerencia) = sugerencia.opuesto().aplicarCambio(this)` (previamente ya se saco la sugerencia de la lista)
