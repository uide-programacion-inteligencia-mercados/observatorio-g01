# Informe automático · G01 · El bolsillo del ecuatoriano

![Estado del robot](https://github.com/uide-programacion-inteligencia-mercados/observatorio-g01/actions/workflows/orquestador_diario.yml/badge.svg)

El robot escribe todos los días su propio informe en PDF: **`reports/informe_g01.pdf`**.
La insignia de arriba dice si la última corrida terminó bien (verde) o mal (rojo).

## Para quién es y qué decisión ayuda a tomar
**Lector:** Gerencia comercial de una cadena de supermercados

Ayuda a identificar cómo cambian los precios y el consumo de los hogares ecuatorianos para tomar mejores decisiones sobre compras, promociones y precios.

## Qué dejamos fuera y por qué
Dejamos fuera datos que no están directamente relacionados con el costo de vida y el consumo de los hogares, porque podrían distraer al lector del objetivo principal del informe.

## Cuándo se lee
El informe se genera todos los días a las 06:15 y está disponible en formato PDF para que el equipo pueda revisar la información antes de tomar decisiones.

## Cómo sabemos que es confiable
El robot revisa que los datos estén dentro de los valores establecidos por el equipo. También verifica que el PDF se haya generado correctamente y, si encuentra un error, conserva el informe anterior y envía una alerta.

## Cómo se arma el informe
1. `robot_banco_mundial.py` trae los datos, los revisa con las reglas del equipo y los guarda.
2. `config_informe.json` tiene los textos del equipo (titular, lectura de negocio y recomendación).
3. `plantillas/informe.html.j2` es el molde con huecos que rellena Jinja2.
4. WeasyPrint imprime el PDF. Si el PDF sale roto, el portero lo rechaza y queda el informe anterior.
5. Reloj del robot: `15 11 * * *`
