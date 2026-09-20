# lm-kubernetes

## Propósito

Puente de operador de Kubernetes sin estado: aplica intenciones de automatización de la plataforma a recursos del clúster (implementaciones, trabajos) mediante un cliente dedicado. Sin estado persistente; los secretos se resuelven mediante lm-secrets.

## Límite de responsabilidad

Responsable de la traducción de la API del clúster y lecturas de aplicación/estado; no responsable de la orquestación de flujos de trabajo, la programación ni el almacenamiento de secretos.

## Dependencias directas de módulos

- Ninguna

## Pertenencia a la solución

- No incluido en una solución predefinida

## Fuente

`modules/lambdas/automation/lm-kubernetes`