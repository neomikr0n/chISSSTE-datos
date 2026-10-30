# chISSSTE-datos

Paquete de datos de **CoordiPedia** — Coordinación de Pediatría, Hospital Regional Morelia,
ISSSTE. Lo escribe `herramientas/publicar/` del repositorio `neomikr0n/chISSSTE`; **no se edita
a mano**.

## Qué hay aquí

| Archivo | Qué es |
| --- | --- |
| `v.json` | 73 bytes: huella del paquete, fecha de generación, número de incidencias y tamaño. En claro. |
| `d/<huella>.bin` | El paquete cifrado (AES-GCM, clave derivada con Argon2id). |

El nombre del `.bin` cambia con el contenido, así que se puede servir con caché larga: una URL
nueva es un contenido nuevo. `v.json` es lo único que la app pregunta de forma periódica.

## Por qué es público

GitHub Pages en una cuenta gratuita exige un repositorio público. Por eso el paquete va **cifrado**:
descargarlo no sirve de nada sin la frase, que no está aquí, ni en el repositorio del código, ni en
OneDrive.

Lo que **no** hay aquí: nombres completos de pacientes, RFC, CURP, teléfonos, domicilios, correos ni
datos clínicos. El paquete lleva lo que la rejilla de guardias necesita para calcular un total —
número de empleado, nombre, turno, tipo de contratación, cargo— y las incidencias con su motivo y
sus fechas. Es el mismo contenido que ya viajaba cifrado en Vercel Blob.

## Cómo lo usa la app

En *Ajustes* se pega la carpeta, sin `v.json` y sin barra final:

```
https://neomikr0n.github.io/chISSSTE-datos
```

Y la frase, que se entrega por otro canal y no se escribe aquí.

## Si algo va mal

El repositorio es desechable por diseño: no tiene código, ni compilación, ni dependencias. Si se
ensucia, se borra y se vuelve a crear; el publicador escribe el paquete entero en cada ejecución.
