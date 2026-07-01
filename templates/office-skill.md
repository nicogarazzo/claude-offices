---
name: {{OFFICE_NAME}}
description: "{{OFFICE_DESCRIPTION}}"
user-invocable: true
allowed-tools: Agent()
model: opus
---

# {{OFFICE_DISPLAY_NAME}}

{{OFFICE_DESCRIPTION}}

## Equipo disponible

<!-- ROSTER_START -->
{{AGENT_ROSTER}}
<!-- ROSTER_END -->

## Protocolo de activacion

Cuando esta oficina se active, sigue el pipeline estandar de 2 rondas. Toda oficina opera con este sistema de calidad. Ningun entregable sale sin pasar por al menos 2 rondas de produccion + critica.

### Ronda 1: Produccion

1. Analiza la tarea del usuario y determina el orden de ejecucion de los agentes.
2. Ejecuta cada agente en su **modo produccion** segun corresponda:
   - Si la tarea es secuencial (pipeline), ejecutalos en orden. Cada agente recibe el output del anterior.
   - Si la tarea permite trabajo paralelo, lanzalos simultaneamente.
3. Al final de la Ronda 1, tienes un primer entregable completo.

### Mesa de critica cruzada

4. TODOS los agentes del roster reciben el entregable de la Ronda 1 y lo evaluan en **modo critica**, cada uno desde su especialidad. Ejecutalos en PARALELO.
5. Cada agente entrega su critica con puntuaciones, problemas detectados e instrucciones concretas para el rewrite.

### Ronda 2: Rewrite con feedback consolidado

6. Consolida las criticas de todos los agentes en un brief de mejora.
7. Ejecuta de nuevo el pipeline completo en **modo produccion**, pero esta vez el agente que inicia la cadena recibe: el entregable de la Ronda 1 + todas las criticas consolidadas. No vuelve al brief original, mejora lo existente.
8. El ultimo agente en la cadena da veredicto final vinculante: APROBADO o REQUIERE REWRITE.
9. Si APROBADO, entrega al usuario la version final con un resumen de las transformaciones clave de ambas rondas.

## Reglas

- SIEMPRE corre las 2 rondas. El minimo obligatorio es: Ronda 1 (produccion) + Mesa de critica + Ronda 2 (rewrite).
- La mesa de critica cruzada se ejecuta en PARALELO para eficiencia.
- En la Ronda 2, los agentes reciben el entregable de la Ronda 1 + las criticas. No vuelven al brief original del usuario.
- No intentes hacer el trabajo directamente: delega a los agentes.
- Si ningun agente del roster aplica para la tarea, informa al usuario que esta oficina no cubre esa necesidad.
- Si el usuario pide "revision" de un trabajo existente, el trabajo del usuario entra directo a la mesa de critica (paso 4), y luego se corre la Ronda 2 completa.
- Al final, entrega solo la version final (Ronda 2) al usuario.
