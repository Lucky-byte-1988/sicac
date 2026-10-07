# sicac

Prototipos navegables de la ONP (Recaudación). Cada página es un archivo HTML único, sin compilación: basta abrirlo en el navegador o publicarlo con GitHub Pages.

Datos y usuarios ficticios, sin valor oficial.

| Página | Qué es |
| --- | --- |
| [`index.html`](index.html) | Cuentas por consumo: control e intercambio con la SBS (padrón PUA, envíos, EAF y aporte del 1 %). |
| [`past-cic/`](past-cic/index.html) | PAST · Transferencia de la CIC (v1): traslados SPP → SNP desde la Constancia de Traslado hasta la Constancia de Transferencia. |
| [`past-cic-v2/`](past-cic-v2/index.html) | PAST · Transferencia de la CIC (v2), con guía, glosario y línea de vida por solicitud. |
| [`ley-32123/`](ley-32123/index.html) | Mapa de interoperabilidad de la Ley 32123: procesos, intercambios entre entidades y citas de la norma. |

## Reglas del requerimiento

En Cuentas por consumo, la pantalla **Administración → Reglas del requerimiento** explica cada una de las 38 reglas (RN-APC-01 a 38) en palabras simples: qué hace el sistema, cuándo, con qué datos y qué resultado deja, con su base en el reglamento (D.S. 189-2025-EF) y el texto del artículo. Cada regla tiene una revisión contra el reglamento (*Conforme*, *Por precisar* u *Observada*). El botón **Descargar para la OTI** baja todo en un CSV que se abre en Excel.

## Uso local

```sh
python3 -m http.server 8000
# luego abre http://localhost:8000/
```

## Simulación guardada

Cuentas por consumo y PAST (v1 y v2) guardan el avance de la simulación en el `localStorage` del navegador. Si recargas la página o la cierras, al volver a entrar la opción **Continuar la simulación guardada** aparece seleccionada en *Datos*; elige *Desde cero* o *Historial de ejemplo* para empezar de nuevo. Cada navegador guarda su propia simulación.

Las preferencias de vista (menú lateral, formato de montos) también se guardan ahí.

## Vistas simplificadas

En Cuentas por consumo cada pantalla empieza con una línea que dice para qué sirve. En el menú lateral todos los grupos están abiertos; cada uno se puede cerrar tocando su título, y el de la pantalla actual siempre se ve. Procesos se ordena por frecuencia: cada mes, cada año, pago del 1 %, cuando ocurre y una sola vez. Las pantallas largas (Cálculo del aporte, Abonos y pendientes, Cese y saldo, Avisos, Reportes, Parámetros y Modelo de datos) se dividen en pestañas, y los bloques que todavía no tienen datos muestran una sola línea en vez de una grilla de guiones. Las capturas de antes y después están en [`docs/ux/`](docs/ux).

## Inicio, Tablero y Reportes

Al entrar al sistema se abre **Inicio**, sin cifras: solo el saludo y el menú. El **Tablero** tiene tres pestañas: *Afiliados y cuentas* (las etapas del proceso, del padrón del PUA al aporte, y los envíos recientes), *Aporte a las EAF* (pagado y pendiente por año fiscal, con el detalle por EAF) y *Pendientes* (lo que requiere atención y los procesos en curso). En **Análisis** cada reporte es un módulo propio, con su filtro y su descarga: *Reporte del mes*, *Envíos por mes*, *Respuestas por envío*, *Cumplimiento de plazos*, *Aporte por ejercicio* y *Reporte por afiliado*.

**Envío automático a la SBS** (antes «Ejecutar envío»): sin textos explicativos; los botones dicen «Simular» porque solo sirven para la prueba. Las pantallas no muestran párrafos de propósito (siguen en el buscador ⌘K).

**Padrón de cuentas** muestra solo el resumen del padrón: al tocar una cifra (personas informadas, envíos realizados, con cuenta, pendientes, observados, cese…) aparece debajo su detalle, que se descarga en Excel. Para buscar a una persona está el módulo aparte **Buscar afiliado** (⌘K). En todo el sistema «log» se reemplaza por «lista de errores» o «registro».

**Actualización de EAF**: no tiene módulos propios. Es otro universo, aparte del padrón del PUA: las personas del Sistema (SNP y SPP) que la SUNAT informa al MEF y el MEF traslada a la ONP (77.1, 77.2 y 78.2), cuyos DNI la ONP envía a la SBS para conocer su EAF vigente (78.3). Por eso *Envío automático a la SBS*, *Envíos a la SBS* y *Respuestas de la SBS* tienen dos pestañas, **Padrón mensual** y **Actualización de EAF**, con el mismo detalle (resumen, errores de estructura y archivo). Los enlaces antiguos (`eaf`, `eafx`, `eafResp`) abren la pestaña correspondiente.

## Buscador (⌘K)

La lupa de la barra superior (o ⌘K) abre un buscador flotante, como Spotlight. Busca módulos, preguntas del reglamento, reglas del requerimiento, artículos, palabras clave y afiliados (por nombre o DNI). Si se escribe una pregunta («¿Qué pasa si el presupuesto no alcanza?»), arriba aparece una respuesta armada con la Ayuda y el reglamento ya cargados en la página, con el artículo o la regla en que se basa. Es una simulación: no usa ningún servicio externo de IA.

Los colores principales usan la paleta de la ONP (azul `#141B4D`).
