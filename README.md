# hiebra/data

Datos personales compartidos, organizados por directorios base XDG. Es un repo XDG como [`hiebra/config`](https://github.com/hiebra/config): el setup del entorno (`env-setup`, en `hiebra/config`) enlaza el contenido de `xdg/data/` en `~/.local/share/`. La configuración va en `hiebra/config` y los datos aquí, así que este repo solo trae `xdg/data/`.

En la raíz solo debe haber `xdg/` como directorio: el setup reconoce así los repos XDG. Los ficheros sueltos, como este README, no cuentan.

## Schemas de OpenSpec

Los schemas de flujo de OpenSpec que se comparten entre proyectos van en [`xdg/data/openspec/schemas/<nombre>/`](xdg/data/openspec/schemas). Se enlazan en `~/.local/share/openspec/schemas/`, la carpeta de schemas de usuario de OpenSpec, así que cualquier proyecto puede usarlos con `schema: <nombre>` en su `openspec/config.yaml` o con `openspec new change <cambio> --schema <nombre>`. Si un proyecto tiene una copia propia en su `openspec/schemas/<nombre>/`, gana la suya.

| Schema          | Origen | Flujo |
| --------------- | ------ | ----- |
| `intent-driven` | [`intent-driven-dev/openspec-schemas`](https://github.com/intent-driven-dev/openspec-schemas), commit `4bb6de2f57`, copia íntegra (MIT, con su `LICENSE`) | `proposal → (specs, design) → adr → tasks`, specs en Gherkin y ADR en `<repo>/adr/` |

- **Se enlazan por carpeta, no por fichero.** OpenSpec no admite un `schema.yaml` enlazado suelto. `env-setup` enlaza enteras las carpetas de `openspec/schemas/` (ver «Carpetas enlazadas enteras» en el README de `hiebra/config`).
- **Un proyecto que use uno de estos schemas no lo lleva en su git.** Quien lo clone sin este repo verá `Unknown schema`. Si el proyecto se comparte, copia el schema a su `openspec/schemas/`.
- **En Windows**, copia la carpeta a `%LOCALAPPDATA%\openspec\schemas\<nombre>` (sin probar en Windows).
- Las skills que sugiere el `skills.txt` de `intent-driven` no se instalan: OpenSpec no lee ese fichero.
- Comprobar desde cualquier proyecto: `openspec schema which <nombre>` (debe decir `Source: user`) y `openspec schema validate <nombre>`.
