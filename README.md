# sicac

Prototipos navegables de la ONP (Recaudación). Cada página es un archivo HTML único, sin compilación: basta abrirlo en el navegador o publicarlo con GitHub Pages.

Datos y usuarios ficticios, sin valor oficial.

| Página | Qué es |
| --- | --- |
| [`index.html`](index.html) | Cuentas por consumo: control e intercambio con la SBS (padrón PUA, envíos, EAF y aporte del 1 %). |
| [`past-cic/`](past-cic/index.html) | PAST · Transferencia de la CIC (v1): traslados SPP → SNP desde la Constancia de Traslado hasta la Constancia de Transferencia. |
| [`past-cic-v2/`](past-cic-v2/index.html) | PAST · Transferencia de la CIC (v2), con guía, glosario y línea de vida por solicitud. |
| [`ley-32123/`](ley-32123/index.html) | Mapa de interoperabilidad de la Ley 32123: procesos, intercambios entre entidades y citas de la norma. |

## Uso local

```sh
python3 -m http.server 8000
# luego abre http://localhost:8000/
```

## Simulación guardada

Cuentas por consumo y PAST (v1 y v2) guardan el avance de la simulación en el `localStorage` del navegador. Si recargas la página o la cierras, al volver a entrar la opción **Continuar la simulación guardada** aparece seleccionada en *Datos*; elige *Desde cero* o *Historial de ejemplo* para empezar de nuevo. Cada navegador guarda su propia simulación.

Las preferencias de vista (menú lateral, formato de montos) también se guardan ahí.
