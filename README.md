# 🎮 QuestLang

> Un lenguaje de programación esotérico basado en videojuegos. Las variables se "invocan", las funciones son "misiones", y los bucles son "grindeo".

**[▶ Prueba QuestLang en vivo](https://nestor6942.github.io/questlang/)** — sin instalar nada, corre en el navegador.

---

## ¿Qué es esto?

QuestLang transpila (compila) a JavaScript en el navegador. Es un lenguaje "esolang" — hecho por diversión y para aprender, no para producción — pero es 100% funcional: escribe código, presiona ejecutar, y verás resultados reales.

```
equip maxHealth = 100
spawn health = maxHealth

quest attack(damage) {
  health = health - damage
  shout("¡Recibiste " + damage + " de daño! HP: " + health)
  respawn health
}

raid turn from 1 to 5 {
  attack(10)
  check (health <= 50) {
    shout("⚠️ HP bajo, ¡usa una poción!")
  }
}

check (health > 0) {
  shout("🏆 ¡Sobreviviste a la raid!")
} retreat {
  shout("💀 Game over.")
}
```

## Referencia rápida

| QuestLang | Significado | Equivale a |
|---|---|---|
| `spawn` | invocar un objeto (variable) | `let` |
| `equip` | equipar algo permanente | `const` |
| `quest name(...) {}` | definir una misión | `function name(...) {}` |
| `respawn` | entregar recompensa y salir | `return` |
| `check (...) {}` | chequear condición | `if (...) {}` |
| `retreat {}` | retirada táctica | `else {}` |
| `grind (...) {}` | grindear mientras dure | `while (...) {}` |
| `raid i from a to b {}` | incursión de rondas fijas | `for (let i=a; i<b; i++) {}` |
| `shout(...)` | gritar en el chat | `console.log(...)` |
| `rageQuit` | abandonar la partida | `break` |
| `retry` | volver a intentar | `continue` |
| `win` / `lose` | victoria / derrota | `true` / `false` |
| `character Name {}` | definir un personaje (clase) | `class Name {}` |
| `Name evolvesFrom Base` | evolucionar de otro personaje | `class Name extends Base` |
| `ability name(...) {}` | habilidad de un personaje | método de clase |
| `.loot(x)` | meter algo al inventario | `.push(x)` |
| `.drop()` | soltar el último objeto | `.pop()` |
| `dungeon {} catch (boss) {}` | zona riesgosa con jefe final | `try {} catch (boss) {}` |

### Ejemplo con clases

```
character Hero {
  ability constructor(name) {
    this.name = name
    this.hp = 100
  }
  ability attack(damage) {
    this.hp = this.hp - damage
    shout(this.name + " bajó a " + this.hp + " HP")
  }
}

character Mage evolvesFrom Hero {
  ability castSpell() {
    shout(this.name + " lanza una bola de fuego 🔥")
  }
}

spawn gandalf = new Mage("Gandalf")
gandalf.attack(30)
gandalf.castSpell()
```

## Correr localmente

No necesitas instalar nada — es un solo archivo HTML.

```bash
git clone https://github.com/nestor6942/questlang.git
cd questlang
open docs/index.html   # o simplemente ábrelo en tu navegador
```

## Roadmap

- [x] Clases y herencia (`character` / `evolvesFrom` / `ability` → `class`)
- [x] Arrays como "inventario" (`.loot()` / `.drop()`)
- [x] Manejo de errores (`dungeon { } catch(boss) { }`)
- [ ] Extensión de VS Code con resaltado de sintaxis
- [ ] Modo "multijugador": comparte y ejecuta snippets con un link
- [ ] Módulos / imports temáticos (`loadout "archivo"`)

Ideas y PRs bienvenidos — abre un issue si quieres proponer una palabra clave nueva.

## Apoya el proyecto

Si QuestLang te sacó una sonrisa o lo usaste para enseñar a alguien a programar:

- ⭐ Déjale una estrella al repo — ayuda muchísimo a que más gente lo encuentre
- ☕ [Invítame un café en Ko-fi](https://ko-fi.com/nestor6942)
- 💜 [GitHub Sponsors](https://github.com/sponsors/nestor6942)

## Licencia

MIT — usa, modifica y comparte libremente. Ver [LICENSE](LICENSE).
