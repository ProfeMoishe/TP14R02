# TP14 - Goku (cambios sobre el juego original)

## Personajes
- **Ken -> Goku** (`public/images/Ken.png` recoloreado: gi naranja, pelo negro, cinturon azul). Misma hoja de frames, el codigo de animaciones no cambia.
- Ryu se mantiene igual.
- Cartel de nombre GOKU en `public/images/hud.png` (+ `StatusBar.js`).

## Interfaz y escenario
- `kenstage.png` (cielo y mar verdes), `logo.png`, `winnerText.png` (RYU WINS / GOKU WINS) y `Controls.png` nuevos.

## Sonido
- Musica nueva: `kens-theme.ogg`.
- 11 efectos reemplazados (mismo nombre de archivo): golpes de puno y patada, ataques, aterrizaje y `hadouken.ogg`.
- Sonido nuevo de victoria de Goku: `goku-win.ogg` (+ `<audio id="sound-goku-win">` en `index.html`).
- Goku dice "Mondongo!" con la voz del navegador: funcion `speak()` en `SoundHandler.js`.
  - Se usa en `Ken.js` (al lanzar el especial) y en `Fighter.js` (cuando un golpe conecta, via `hitSpeech`).

## Rebalanceo (cada cambio tiene el valor anterior en un comentario)
- Dano: `src/constants/fighter.js` (ligero 12->10, medio 20->18, fuerte 28->32).
- Velocidad de caminar: Goku 3->3.5 (`Ken.js`), Ryu 3->2.8 (`Ryu.js`).
- Velocidad de proyectiles: `src/constants/fireball.js` (150/220/300 -> 180/260/340).
- Teclas del jugador 1: Q<->R (punos) y F<->G (patadas) en `src/config/controls.js` (la imagen `Controls.png` esta actualizada).

## Mecanica nueva: tiempo de recarga del ataque especial
- `SPECIAL_COOLDOWN = 3000` ms en `src/constants/battle.js`.
- `Fighter.js` -> `changeState`: si el especial todavia no esta listo (`specialReadyAt`), no se ejecuta.
- `StatusBar.js` -> `drawSpecialCooldown`: barra bajo el nombre de cada jugador (celeste = listo).

## Controles
- Especial: abajo, abajo-adelante, adelante + puno.
