# Informe automático · G01 · El bolsillo del ecuatoriano

![Estado del robot](https://github.com/uide-programacion-inteligencia-mercados/observatorio-g01/actions/workflows/orquestador_diario.yml/badge.svg)

El robot escribe todos los días su propio informe en PDF: **`reports/informe_g01.pdf`**.
La insignia de arriba dice si la última corrida terminó bien (verde) o mal (rojo).

## Para quién es y qué decisión ayuda a tomar
**Lector:** Gerente comercial

El gerente comercial decide si mantiene o ajusta precios en Ecuador. Con inflación en 0,71% y consumo creciendo, la decisión por defecto es mantener precios y enfocarse en volumen.

## Qué dejamos fuera y por qué
PIB, desempleo, tipo de cambio y proyecciones. Con inflación y consumo de los hogares basta para responder si los precios suben y los clientes siguen comprando; más indicadores alargan el informe sin cambiar la decisión.

## Cuándo se lee
Llega automáticamente al correo del gerente comercial a las 7 a.m. Son dos páginas y se leen en menos de cinco minutos.

## Cómo sabemos que es confiable
Los datos vienen de la API del Banco Mundial y el informe indica fuente y número de corrida. Antes de generarlo, el robot revisa que no haya datos vacíos ni años faltantes, que el último año no sea más viejo de lo esperado y que los valores estén en rangos razonables; si algo falla, avisa en vez de enviar el informe normal

## Cómo se arma el informe
1. `robot_banco_mundial.py` trae los datos, los revisa con las reglas del equipo y los guarda.
2. `config_informe.json` tiene los textos del equipo (titular, lectura de negocio y recomendación).
3. `plantillas/informe.html.j2` es el molde con huecos que rellena Jinja2.
4. WeasyPrint imprime el PDF. Si el PDF sale roto, el portero lo rechaza y queda el informe anterior.
5. Reloj del robot: `0 12 * * *`
