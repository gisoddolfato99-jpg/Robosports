```shell
##imports
from hub import light_matrix, motion_sensor, port
import runloop
import motor
import motor_pair
import color
import color_sensor
import force_sensor
import time


#puertos
puerto_b = port.B
puerto_f = port.F
choque = port.D
tira = port.A
llantas = motor_pair.PAIR_1

########
motor_pair.pair(llantas, port.C, port.E)

#velocidad
velm = 1100
pro = 832
pron = -832

# ID
COLOR_OBJETIVO = 1

# Estados
lol = 0
brasil = 0
puffis = 0


# Sensor presionado
def sensor_presionado():
    return force_sensor.pressed(choque) or force_sensor.force(choque) > 0


# motor A
async def mover_tira_seguro(grados, velocidad=1100):
    vel_abs = abs(velocidad)
    await motor.run_for_degrees(tira, grados, vel_abs)


## Giro con Giroscopio 
async def girar_giroscopio(grados, velocidad=350):
    angulo_inicial = motion_sensor.tilt_angles()[0]
    meta_decimas = abs(grados * 10)

    direccion = 100 if grados > 0 else -100
    motor_pair.move(llantas, direccion, velocity=velocidad)

    await runloop.until(
        lambda: abs(motion_sensor.tilt_angles()[0] - angulo_inicial) >= meta_decimas
    )

    motor_pair.stop(llantas, stop=motor.BRAKE)
    await runloop.sleep_ms(100)


# escape
async def avanzar_con_escape(velocidad=832):
    motor_pair.move_tank(llantas, velocidad, velocidad)
    await runloop.sleep_ms(250) 

    # Lee ruedas
    pos_c_previa = motor.relative_position(port.C)
    pos_e_previa = motor.relative_position(port.E)

    while not sensor_presionado():
        await runloop.sleep_ms(120) 

        if sensor_presionado():
            break

        pos_c_actual = motor.relative_position(port.C)
        pos_e_actual = motor.relative_position(port.E)

        #Grados rueda
        avance_c = abs(pos_c_actual - pos_c_previa)
        avance_e = abs(pos_e_actual - pos_e_previa)

        # Si ruedas no
        if avance_c < 8 or avance_e < 8:
            motor_pair.stop(llantas, stop=motor.BRAKE)
            await runloop.sleep_ms(100)

            # Reversa 
            await motor_pair.move_for_degrees(llantas, 100, 0, velocity=pron)
            await runloop.sleep_ms(100)

            # seguir
            motor_pair.move_tank(llantas, velocidad, velocidad)
            await runloop.sleep_ms(250) # Tiempo de re-arranque

            # Actualiza
            pos_c_actual = motor.relative_position(port.C)
            pos_e_actual = motor.relative_position(port.E)

        pos_c_previa = pos_c_actual
        pos_e_previa = pos_e_actual

    motor_pair.stop(llantas, stop=motor.BRAKE)


## Funciones 
async def mela():
    global lol
    lol = lol + 1

    # Avanza 
    await avanzar_con_escape(pro)
    await runloop.sleep_ms(100)

    # Mecanismo A 
    await mover_tira_seguro(-160, velm)
    await runloop.sleep_ms(100)
    await mover_tira_seguro(160, velm)
    await runloop.sleep_ms(100)

    # Retroceso 
    await motor_pair.move_for_degrees(llantas, 180, 0, velocity=pron)

    # Giro de 90
    await girar_giroscopio(90, 350)
    motor_pair.move_tank(llantas, velm, velm)


async def pega2s():
    # Giro de 90
    await girar_giroscopio(90, 350)

    # Avanza 
    await avanzar_con_escape(pro)


async def juegue():
    await mover_tira_seguro(-160, velm)
    await runloop.sleep_ms(100)
    await mover_tira_seguro(160, velm)
    await runloop.sleep_ms(200)
    await mover_tira_seguro(-160, velm)
    await runloop.sleep_ms(100)
    await mover_tira_seguro(160, velm)

    
    await girar_giroscopio(90, 350)
    await motor_pair.move_for_degrees(llantas, 180, 0, velocity=832)


async def chav2():
    global brasil, lol

    # Avanza 
    await avanzar_con_escape(pro)
    await motor_pair.move_for_degrees(llantas, 145, 0, velocity=pron)
    await runloop.sleep_ms(200)

    await pega2s()
    brasil = brasil + 1

    if brasil == 3:
        lol = lol + 1
        motor_pair.stop(llantas, stop=motor.BRAKE)
        await juegue()
        brasil = 0
        await runloop.until(lambda: not sensor_presionado())
        motor_pair.move_tank(llantas, pro, pro)


async def cavernicola():
    global puffis, lol

    # Avanza 
    await avanzar_con_escape(pro)
    await motor_pair.move_for_degrees(llantas, 170, 0, velocity=pron)
    await runloop.sleep_ms(200)

    await pega2s()
    puffis = puffis + 1

    if puffis == 3:
        lol = lol - 1
        motor_pair.stop(llantas, stop=motor.BRAKE)
        await juegue()
        puffis = 0
        await runloop.until(lambda: not sensor_presionado())
        motor_pair.move_tank(llantas, pro, pro)


## Más acciones 
async def manos():
    global lol
    while True:
        if lol == 0:
            await mela()
        elif lol == 1:
            await chav2()
        elif lol == 2:
            await cavernicola()

        await runloop.sleep_ms(50)


## Bucle de color
async def rosa():
    while True:
        # Detecta el color
        if (
            color_sensor.color(puerto_b) == COLOR_OBJETIVO
            or color_sensor.color(puerto_f) == COLOR_OBJETIVO
        ):
            # Detiene los motores 
            motor_pair.stop(llantas, stop=motor.BRAKE)

            # Retrocede 
            await motor_pair.move_for_degrees(llantas, 30, 0, velocity=pron)

            # motor a
            await mover_tira_seguro(-160, velm)

            # Espera 
            await runloop.until(
                lambda: color_sensor.color(puerto_b) != COLOR_OBJETIVO
                and color_sensor.color(puerto_f) != COLOR_OBJETIVO
            )

            # Reanuda 
            motor_pair.move_tank(llantas, pro, pro)

            # Guarda el tiempo
            tiempo_inicio = time.ticks_ms()

            # Espera 
            await runloop.until(
                lambda: (
                    color_sensor.color(puerto_b) == COLOR_OBJETIVO
                    or color_sensor.color(puerto_f) == COLOR_OBJETIVO
                )
                or time.ticks_diff(time.ticks_ms(), tiempo_inicio) >= 3000
            )

            # Regresa el motor A 
            await mover_tira_seguro(160, velm)

            # Pausa 
            await runloop.sleep_ms(500)

        await runloop.sleep_ms(50)

```


## Main 
runloop.run(manos(), rosa())
