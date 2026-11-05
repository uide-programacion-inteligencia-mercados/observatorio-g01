# Distribución del informe · Equipo G01
## 1. ¿A quién le llega el informe y por qué?
(Al gerente comercial, destinatario que figura en el informe. El contenido es de interés general para quien decide sobre precios y ventas en Ecuador.)
## 2. ¿Por qué ese canal y no otro?
(Se eligió el canal #informes-g01 en Slack porque centraliza la comunicación del observatorio, evita saturar el correo electrónico y permite revisar el resumen y la tarjeta de salud del robot antes de comenzar la jornada.)
## 3. ¿Cuándo llega?
(Hora local de Quito: todos los días a las 07:00 (UTC-5).
Conversión a UTC: 07:00 + 5 horas = 12:00 UTC.
Expresión cron: 0 12 * * *.
Se programa 30 minutos después del robot de recolección (06:30 en Quito, 11:30 UTC), para garantizar que el PDF ya esté compilado y validado en la carpeta reports/.
Aunque los datos del Banco Mundial son anuales, el envío es diario para que la tarjeta “Salud del robot” confirme cada mañana que la corrida fue exitosa..)
## 4. ¿Qué pasa si el envío falla?
(Si el envío falla por corte de red o error de API, el script no sobrescribe ni daña el informe PDF. El evento se registra como fallido en logs/envios_g01.jsonl y se genera una alerta automática en GitHub Issues para que el equipo intervenga. El último informe válido permanece intacto en reports/.)
## 5. Privacidad y secretos
(La URL del webhook da permisos de publicación en Slack, por lo que se guarda únicamente en GitHub Secrets bajo la variable SLACK_WEBHOOK_URL. No se expone en el código fuente ni en commits públicos. Además, el informe contiene solo indicadores agregados de Ecuador provenientes del Banco Mundial, sin datos personales.)
