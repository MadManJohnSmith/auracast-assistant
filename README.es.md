# auracast-assistant

Un **asistente Auracast** open source para Linux: descubrir, listar y unirse
a transmisiones de audio Bluetooth LE Audio (Auracast) desde la línea de
comandos — con GUI más adelante.

## Por qué

El stack de LE Audio en Linux (sockets ISO del kernel, BlueZ BAP/BASS,
PipeWire) madura rápido — pero la capa superior está sin terminar: el
asistente que escanea fuentes de broadcast cercanas, las presenta con nombre
y calidad, maneja códigos de broadcast y se une al stream. El propio reporte
de ingeniería de Collabora marca la UX de asistente/scan delegator como
trabajo futuro de alta prioridad, y bugs abiertos recientes de BASS confirman
que nadie lo tiene resuelto. Hoy no existe una CLI o GUI pulida para esto en
Linux.

## Estado

**Planeación.** Siguientes pasos:

1. Survey de hardware: verificar las capacidades LE Audio del adaptador local
   (ISO/BAP).
2. Reproducir el estado actual del stack en esta máquina (versión de BlueZ,
   flags experimentales, roles de PipeWire).
3. Borrador y estabilización del contrato de la CLI.

## CLI planeada (borrador, puede cambiar)

```text
auracast scan [--timeout SEG]              # listar fuentes de broadcast cercanas
auracast info <source-id>                  # nombre, calidad, estado de cifrado
auracast join <source-id> [--code CODE]    # sincronizar BIG, entregar stream a PipeWire
auracast leave
```

## Referencias

- Collabora — Implementing Bluetooth LE Audio and Auracast on Linux systems
  (reporte de ingeniería, 2025-11-24)
- Notas de release de BlueZ 5.86–5.88 (Enhanced BAP, VCP, MCP, TMAS)
- Bluetooth SIG — programa Auracast

## Licencia

[Apache-2.0](LICENSE)
