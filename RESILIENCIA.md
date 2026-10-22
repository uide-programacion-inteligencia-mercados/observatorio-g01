# Resiliencia · G01 · El bolsillo del ecuatoriano

![Estado del robot](https://github.com/uide-programacion-inteligencia-mercados/observatorio-g01/actions/workflows/orquestador_diario.yml/badge.svg)

La insignia de arriba dice si la última corrida del robot terminó bien (verde) o mal (rojo).

## Las reglas de calidad del robot
| Indicador | Mínimo creíble | Máximo creíble |
|---|---|---|
| Inflación anual (%) | -5.0 | 30.0 |
| Consumo de los hogares por persona, crecimiento (%) | -20.0 | 20.0 |

- Filas mínimas: 10 · Antigüedad máxima del último dato: 4 años
- Reintentos: 2, con espera inicial de 6 s que se duplica en cada intento
- Reloj: `0 12 * * 1-5`

## Qué es una falla para nosotros
Si se registran filas en 0 es una falla debido a que no indica una advertencia, se podría tomar como productos inexistentes y afecta el proceso de análisis

## Nuestro plan B
Bajar manualmente la información, medida que demanda tiempo

## Quién atiende la alerta
Un elemento del equipo designado

## Qué vigilamos cada lunes
Que cada fila sea rellenada y no venga información fantasma o vacía
