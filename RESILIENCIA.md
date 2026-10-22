# Resiliencia · G01 · El bolsillo del ecuatoriano

![Estado del robot](https://github.com/uide-programacion-inteligencia-mercados/observatorio-g01/actions/workflows/orquestador_diario.yml/badge.svg)

La insignia de arriba dice si la última corrida del robot terminó bien (verde) o mal (rojo).

## Las reglas de calidad del robot
| Indicador | Mínimo creíble | Máximo creíble |
|---|---|---|
| Inflación anual (%) | -5.0 | 30.0 |
| Consumo de los hogares por persona, crecimiento (%) | -20.0 | 20.0 |

- Filas mínimas: 10 · Antigüedad máxima del último dato: 4 años
- Reintentos: 5, con espera inicial de 2 s que se duplica en cada intento
- Reloj: `15 11 * * *`

## Qué es una falla para nosotros
Consideramos que existe una falla cuando los indicadores presentan valores fuera de los rangos creíbles definidos o cuando el robot no logra obtener datos confiables. Estos límites permiten detectar errores sin confundirlos con variaciones económicas reales.

## Nuestro plan B
Si el Banco Mundial no responde, el robot vuelve a intentarlo y espera un tiempo entre cada intento. Si continúa sin funcionar, registra el error y genera una alerta, evitando presentar datos nuevos como si fueran confiables.

## Quién atiende la alerta
La persona responsable de revisar el repositorio del equipo atenderá las alertas y comprobará primero el registro de la corrida y la bitácora para identificar el error. Después verificará si el problema está en la conexión, los datos o las reglas de calidad.

## Qué vigilamos cada lunes
Cada lunes revisaremos el archivo de salud para comprobar que las corridas terminen correctamente, que no existan errores repetidos y que los datos se actualicen. Si encontramos una falla o varios días sin información, revisaremos la bitácora y tomaremos medidas para solucionarla.
