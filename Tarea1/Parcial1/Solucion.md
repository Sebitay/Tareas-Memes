# Tarea 1 | Entrega Parcial 1

Identificar los traits y clases necesarias para recrear las unidades y el tablero de 99.7% Citric Liquid

## 1. Traits

### Unidades

Todas las unidades tienen:

- Una cantidad de "Hit Points" maximos.
- Una cantidad de "Hit Points" actuales.
- Una cantidad de puntos de daño (ATK).
- Una cantidad de puntos de defensa (DEF).
- Una cantidad de puntos de evasion (EVA).
- Un panel actual.
- Una cantidad de estrellas.
- Una funcion para agregar estrellas.
- Una funcion para eliminar estrellas.
- Una funcion para eliminar Hit Points
- Una funcion para atacar a otra Unidad

Entonces quedaria un trait como el siguiente..

### Trait Unidad

- `val maxHitPoints: Double`
- `val atkPoints: Double`
- `val defPoints: Double`
- `val evaPoints: Double`
- `var hitPoints: Double`
- `var curPanel: Panel`
- `var starCount: Double`
- `def addStars(stars: Int): Unit`
- `def delStars(stars: Int): Unit`
- `def delHitPoints(hitpoints: Double): Unit`
- `def Atack(roll: Int, unit: Unidad): Unit`

---

### Paneles

Todos los paneles tienen:

- Un tipo.
- Jugadores dentro de el.
- Paneles siguientes.
- Una funcion para insertar jugadores a el.
- Una funcion para extraer jugadores de el.

Entonces quedaria un trair como el siguiente.

### Trait Panel

- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
---
## 2. Clases
#### Hay 2 clases que extienden del trait Unidad, *Personaje* y *Wild Unit*.
---
### Personajes

Cosas extras que necesitan los personajes:

- Un estado que determina si esta K.O o no.
- Una funcion que decide si cambiar el estado de K.O a verdadero.
- Una funcion que decide si cambiar el estado de K.O a falso.
- Un contador de victorias.
- Una funcion para agregar victorias.
- Un contador de la norma actual.
- Una funcion para aumentar su norma.
- Una variable que determina que camino de norma esta siguiendo.
- Una funcion para agregar Hit Points.
- Una variable con la cantidad de paneles que tiene por recorrer
- Una funcion Roll para tirar el dado
- Una funcion para moverse a el siguiente panel
- Una funcion para iniciar el panel

Entonces quedaria una clase de esta forma:

### Class Personaje extends Unidad

- `val maxHitPoints: Double`
- `val atkPoints: Double`
- `val defPoints: Double`
- `val evaPoints: Double`
- `var hitPoints: Double`
- `var curPanel: Panel`
- `var starCount: Double`
- `def addStars(stars: Int): Unit`
- `def delStars(stars: Int): Unit`
- `def delHitPoints(hitpoints: Double): Unit`
- `def Atack(roll: Int, unit: Unidad): Unit`
- `var KO: Boolean`
- `def enterKO(hitPoints: Double): Unit`
- `def leaveKO(Roll: Int): Unit`
- `var Victories: Int`
- `def addVictories(victories: Int): Unit`
- `var Norma: Int`
- `def addNorma(): Unit`
- `val typeNorma: String`
- `def addHitPoints(hitpoints: Double): Unit`
- `var porMover: Int`
- `def Roll(): Int`
- `def Move(casillas: ArrayBuffer[Panel]): Unit`
- `def Initialize(): Unit`

---
### Wild Units
Cosas extra que necesita un Wild Unit:

- Una variable que indica su tipo

### Class WildUnit extends Unidad
- `val maxHitPoints: Double`
- `val atkPoints: Double`
- `val defPoints: Double`
- `val evaPoints: Double`
- `var hitPoints: Double`
- `var curPanel: Panel`
- `var starCount: Double`
- `def addStars(stars: Int): Unit`
- `def delStars(stars: Int): Unit`
- `def delHitPoints(hitpoints: Double): Unit`
- `def Atack(roll: Int, unit: Unidad): Unit`
- `val Type: String`
---

#### Hay 5 clases que se extienden de el trait Panel, *Neutral Panel*, *Home Panel*, *Bonus Panel*, *Drop Panel* y *Encounter Panel*.
---
### Neutral Panel
Cosas extra que necesita un Neutral Panel:
- Nada :/

Entonces quedaria una clase de esta forma:

### Class NeutralPanel extends Panel
- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
---
### Home Panel

Cosas extra que necesita un Home Panel

- Una variable que indica su dueño
- Una variable que indica que jugador activo el panel
- Una funcion que deicde si activar el panel o no.
- La funcion Norma Check

Entonces quedaria una clase de esta forma:
- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
- `val Owner: Player`
- `var Activated: Player`
- `def canActivate(): Unit`
- `def normaCheck(player: Player): Unit`

---
### Bonus Panel

Cosas extra que necesita un Bonus Panel:
- Una funcion para agregarle estrellas al jugador que cae en este panel.

Entonces quedaria una clase de esta forma:

### Class BonusPanel extends Panel

- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
- `def Bonus(player: Player): Unit`
---
### Drop Panel

Cosas extra que necesita un Drop Panel:
- Una funcion para quitarle estrellas al jugador que cae en este panel.

Entonces quedaria una clase de esta forma:

### Class DropPanel extends Panel

- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
- `def Drop(player: Player): Unit`
---
### Encounter Panel

Cosas extra que necesita un Encounter Panel:
- Una variable que indique que Wild Unit se encuentra en este panel.
- Una funcion para generar un Wild Unit.

Entonces quedaria una clase de esta forma:

- `val Type: String`
- `var Players: ArrayBuffer[Player]`
- `var nextPanels: ArrayBuffer[Panel]`
- `def insPlayer(player: Player): Unit`
- `def extPlayer(player: Player): Unit`
- `var wildUnit: WildUnit`
- `def genUnit(): Unit`