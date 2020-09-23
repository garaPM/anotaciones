# Tributaria

## 1. Sistema Integrado

El **sistema integrado** consiste en que dos participante en el ciclo del pago de impuesto de las utilidades que reciba este ya sea por generación de servicios o productos que ofrezca en periodo anual, en este caso el impuesto generado por la empresa de Nivel 1 pasa a ser un crédito para el contribuyente final(*socios o dueños*) de nivel 2 que consumira este saldo a favor suyo para el pago del los **Impuesto Global Complementario** y en el caso de tener nacionalidad extranjera sera **Impuesto adicional**.

```mermaid
graph TD
A(Sistema Integrado)-->B[Participantes];
     B-->C[Nivel 1 - Sociedad];
     B-->D[Nivel 2 - Contribuyente Final];
     C-->E[Generadora de Renta];
     D-->F[Contribuyente Final - Recibe Crédito];
     E-->G[Paga Impuestos Renta];
     G-->D;
     F-->H[Impuesto Global Complementario o Impuesto adicional]
```

### 1.1. Regímenes Tributarios

A partir de Enero 2020 hacia delante existen 4 tipos de regimenes tributarios

```mermaid
graph TD
A(Primera Categoria)-->B(Renta Efectiva);
     B-->C[14 A - Semi Integrado];
     B-->D[14 D Nº3 - ProPyme General];
     B-->E[14 D Nº8 - ProPyme Transparente];
     A-->F[Renta Presunta Art 34];
     F-->G[14 B Nº2 Sin Contabilidad];
     A-->H[14 B Nº1 Contabilidad Simplificada];
```