# AYUDA-PORFA
es hecho por ursina en visual code en lenguaje python
Nesecito ayuda con un codigo quiero hacer que el personaje no pase el limite de la pantalla en python3 pero lo pasa como si nada e intentado de todo y nose que mas hacer agradeseria una ayuda este es el codigo:

from ursina import *

app = Ursina(size=(1920, 1080))  # Establece el tamaño de la ventana

Jugador = Entity(model="cube", color=color.red, scale_y=2, x=0, y=0, z=0)
velocidad_x = 5  # Velocidad horizontal del jugador

def update():
    global velocidad_x

    # Movimiento horizontal
    Jugador.x += held_keys["d"] * time.dt * velocidad_x
    Jugador.x -= held_keys["a"] * time.dt * velocidad_x

    # Rebote en los bordes de la pantalla
    mitad_ancho_jugador = Jugador.scale_x / 2
    limite_izquierdo = -960 + mitad_ancho_jugador  # Mitad del ancho de la pantalla
    limite_derecho = 960 - mitad_ancho_jugador

    if Jugador.x < limite_izquierdo:
        Jugador.x = limite_izquierdo
        velocidad_x *= -1  # Cambia la dirección de la velocidad
    elif Jugador.x > limite_derecho:
        Jugador.x = limite_derecho
        velocidad_x *= -1  # Cambia la dirección de la velocidad

def input(key):
    if key == 'space':
        Jugador.y += 1
        invoke(setattr, Jugador, 'y', Jugador.y - 1, delay=.25)

app.run()
