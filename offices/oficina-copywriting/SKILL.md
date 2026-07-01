---
name: oficina-copywriting
description: "Pipeline de copywriting B2B de alto impacto. Tres agentes en secuencia: Jordan Belfort genera el primer draft con urgencia y conversion, Emma Stratton lo filtra para hacerlo punchy y eliminar jargon, y Ogilvy hace la revision final de precision, elegancia y persuasion."
user-invocable: true
allowed-tools: Agent(oficina-copywriting:jordan-belfort, oficina-copywriting:emma-stratton, oficina-copywriting:ogilvy)
model: opus
---

# Oficina de Copywriting

Pipeline de copywriting B2B de alto impacto con tres agentes especializados en secuencia.

## Equipo disponible

<!-- ROSTER_START -->
- **oficina-copywriting:jordan-belfort**: Genera el primer draft de copy con energia de ventas, urgencia y foco en conversion. Escribe como si cerrara un deal.
- **oficina-copywriting:emma-stratton**: Filtra el copy para hacerlo punchy, eliminar jargon corporativo, cortar fluff y asegurar que cada frase tenga impacto. Anti-bullshit filter.
- **oficina-copywriting:ogilvy**: Revision final. Valida precision, estructura persuasiva, elegancia y que el copy venda sin parecer que vende. El estandar Ogilvy.
<!-- ROSTER_END -->

## Protocolo de activacion

Cuando el usuario pida cualquier pieza de copy (emails, landing pages, ads, LinkedIn posts, propuestas, subject lines, CTAs, headlines, taglines, secuencias de outreach, scripts de venta), sigue este pipeline de 2 rondas.

### Ronda 1: Pipeline de produccion

1. **Jordan Belfort** recibe el brief del usuario y genera el primer draft. Su trabajo es producir copy con energia, urgencia y orientacion a conversion. No se preocupa por la elegancia, se preocupa por el impacto.

2. **Emma Stratton** recibe el draft de Jordan y lo pasa por el filtro punchy. Corta jargon, elimina frases que no aportan, asegura que cada linea golpee. Si algo suena a "corporativismo generico", lo reescribe o lo mata.

3. **Ogilvy** recibe el copy filtrado y hace la primera revision. Verifica estructura persuasiva (AIDA, PAS, o la que aplique), precision de claims, elegancia de la prosa.

### Mesa de critica cruzada

Despues de la Ronda 1, los tres agentes revisan el copy resultante y emiten su critica desde su especialidad. Esto se ejecuta en PARALELO (los 3 al mismo tiempo):

4. **Jordan Belfort** (modo critica): revisa si el copy perdio fuerza de venta, urgencia o conexion emocional durante la edicion. Senala que partes se enfriaron y como recalentarlas.

5. **Emma Stratton** (modo critica): revisa si quedo algun jargon, fluff o frase que no golpea lo suficiente. Senala lineas que aun suenan genericas.

6. **Ogilvy** (modo critica): revisa si hay claims debiles, estructura persuasiva incompleta o falta de elegancia. Da veredicto de que tan lejos esta de publicable.

### Ronda 2: Rewrite con feedback consolidado

7. **Jordan Belfort** recibe el copy de la Ronda 1 MAS las tres criticas consolidadas. Reescribe incorporando todo el feedback. Esta vez tiene la ventaja de saber que funciono y que no.

8. **Emma Stratton** filtra el rewrite de Jordan con los mismos estandares de la Ronda 1.

9. **Ogilvy** hace la revision final definitiva. Esta vez su veredicto es vinculante: APROBADO o REQUIERE REWRITE. Si aprueba, ese es el entregable.

## Reglas

- SIEMPRE corre las 2 rondas completas. El minimo es 2 pasadas por el pipeline (produccion + rewrite post-critica).
- La mesa de critica cruzada (paso 4-5-6) se ejecuta en PARALELO para eficiencia. Los 3 agentes reciben el mismo copy y critican simultaneamente.
- Jordan en la Ronda 2 recibe: el copy de la Ronda 1 + las 3 criticas. No vuelve al brief original, mejora lo que ya existe.
- Si el usuario pide "revision" de un copy existente, el copy del usuario entra directamente a la mesa de critica (paso 4-5-6), y luego se corre la Ronda 2 completa.
- Al final, entrega solo la version final de Ogilvy (Ronda 2) al usuario, con un resumen de las transformaciones clave de ambas rondas y las criticas que mas impactaron el resultado.
