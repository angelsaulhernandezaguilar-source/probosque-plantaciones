# PROBOSQUE · Ingreso y seguimiento de convocatorias 2026

Prototipo en React (Vite) del sistema de ingreso a la convocatoria de PROBOSQUE,
con foco en **Plantaciones Sustentables**. Proyecto de Formulación de Proyectos
Informáticos (ESCOM-IPN).

## Cómo correrlo

```
npm install
npm run dev      # abre http://localhost:5173
npm test         # pruebas de las reglas (CLABE, montos, días hábiles)
npm run build    # genera dist/ para publicar
```

## Pantallas y quién las usa

| Ruta | Vista | Instancia |
|------|-------|-----------|
| `#/` | Lista de convocatorias | Público |
| `#/publicar` | `PublicacionConvocatorias` | Dirección General |
| `#/registro/:id` | `RegistroConvocatoria` | Beneficiario |
| `#/estatus` | Consulta de estatus por folio | Beneficiario |
| `#/recepcion` | `RecepcionSolicitudes` | Delegación regional |
| `#/dictamenes` | `EmisionDictamenes` | Unidad jurídica |

## Flujo que cubre

1. La Dirección General publica la convocatoria.
2. El beneficiario se registra y recibe un folio.
3. La delegación coteja: si acepta, pasa a dictamen jurídico; si rechaza, se abren
   5 días hábiles para subsanar y el beneficiario puede reenviar su documentación.
4. La Unidad jurídica emite dictamen favorable o desfavorable (no factible).

## Estructura

- `src/vistas/` — las cuatro vistas originales; solo dibujan y avisan por props.
- `src/paginas/` — pantallas nuevas (convocatorias y estatus).
- `src/estado/Almacen.jsx` — estado global y acciones; guarda en `localStorage`.
- `src/utilidades/reglas.js` — reglas de negocio: CLABE, superficie, montos y plazos.
- `src/datos/catalogos.js` — programas, delegaciones, conceptos de apoyo y estados.

## Límites del prototipo

- No hay backend ni inicio de sesión: los datos viven en el navegador y de los
  archivos solo se conserva el nombre.
- Los días hábiles saltan sábados y domingos, pero no días festivos.
- Faltan el dictamen técnico (SIG), el Comité, el vivero, el contrato y los pagos.
