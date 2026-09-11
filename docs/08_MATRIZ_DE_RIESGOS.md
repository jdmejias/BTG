# Matriz de Riesgos & Estrategia Integral de Mitigación
**Enfoque de Supervisión:** Comité de Riesgos & Auditoría BTG Nexus  
**Reserva de Contingencia Asignada:** $3,000,000 USD (12% del presupuesto)  
**Marco de Referencia:** Basilea III, COSO ERM, GAFI / SBP Panamá  

---

## 1. Matriz de Riesgo Multidimensional

Identificamos los 5 riesgos críticos que enfrenta una expansión bancaria digital en Centroamérica y definimos controles preventivos, detectivos y correctivos para cada uno:

```
PROBABILIDAD
   Alta   │                   [R4: Ciberseguridad]   [R1: Regulatorio/AML]
          │
  Media   │  [R5: Cambio/Macro]                      [R2: Crédito & Default]
          │
   Baja   │                   [R3: Sesgo IA/Model Drift]
          └─────────────────────────────────────────────────────────────
                Bajo                  Medio                     Alto
                                     IMPACTO
```

---

## 2. Detalle y Planes de Mitigación

### R1. Riesgo Regulatorio & Prevención de Blanqueo de Capitales (AML / CFT)
- **Descripción:** Riesgo de sanciones, multas o cierre de operaciones por incumplimiento de normativas de la Superintendencia de Bancos de Panamá (SBP) o inclusión de la región en listas grises del GAFI.
- **Impacto Potencial:** Muy Alto (Pérdida de la licencia bancaria y daño reputacional a la marca global BTG).
- **Estrategia de Mitigación:**
  - Sistema automatizado de **Graph Neural Networks (GNN)** para monitoreo de patrones de estructuración transaccional en tiempo real.
  - Validación biométrica facial contra bases de datos de identificación nacional (e-cédula) y cruce instantáneo con listas de PEPs (Personas Políticamente Expuestas), OFAC y sanciones internacionales (Dow Jones Risk & Compliance).
  - Oficial de Cumplimiento residente con reporte directo e independiente a la Junta Directiva de BTG Pactual Brasil.

---

### R2. Riesgo de Crédito & Aumento Imprevisto de la Cartera Vencida (NPL)
- **Descripción:** Deterioro de la capacidad de pago de los deudores jóvenes o PyMEs frente a shocks macroeconómicos o errores en el modelo de scoring alternativo.
- **Impacto Potencial:** Alto (Erosión del capital de trabajo y necesidad de provisiones extraordinarias).
- **Estrategia de Mitigación:**
  - **Límites de Exposición Escalonados:** Los usuarios inician con líneas de micro-crédito pequeñas ($150 - $500 USD para jóvenes, $2,500 para PyMEs); los cupos solo crecen tras 3 ciclos de pago cumplidos satisfactoriamente.
  - **Explicabilidad SHAP & Reglas Duras:** El modelo de Machine Learning no puede contradecir políticas prudenciales duras (ej. Ratio de Cobertura de Servicio de Deuda - DSCR < 1.25x es rechazo automático, sin importar el score alternativo).
  - **Fondo de Reserva Específico de $1.0M USD** dentro del presupuesto para absorber contingencias de aprendizaje del modelo durante los primeros 6 meses.

---

### R3. Riesgo de Modelo (Model Drift & Sesgo Algorítmico)
- **Descripción:** Degradación del rendimiento de los modelos predictivos debido a cambios en el entorno macroeconómico (inflación, desempleo), o discriminación indirecta hacia ciertos grupos demográficos.
- **Impacto Potencial:** Medio-Alto (Pérdidas operativas y contingencias legales por discriminación crediticia).
- **Estrategia de Mitigación:**
  - Plataforma de monitoreo continuo de **Evidently AI** para detectar desviaciones estadísticas entre los datos de entrenamiento y los datos en vivo en producción.
  - Auditoría semestral independiente del equipo de Riesgo Cuantitativo Central de BTG Pactual São Paulo.
  - Marco de **Fair Lending**: Pruebas automáticas de paridad de impacto adverso (Disparate Impact Ratio > 0.80) en todas las variables demográficas.

---

### R4. Riesgo de Ciberseguridad & Fuga de Datos
- **Descripción:** Ataques de ransomware, inyección SQL, robo de credenciales mediante phishing masivo o ataques DDoS a los servicios bancarios.
- **Impacto Potencial:** Muy Alto (Interrupción de servicio, multas de protección de datos de Panamá/Costa Rica y pérdida de confianza del cliente).
- **Estrategia de Mitigación:**
  - Arquitectura **Zero Trust** en nube (AWS/Azure) con segmentación de microredes y autenticación obligatoria vía Passkeys / WebAuthn biométrico (eliminando contraseñas estáticas vulnerables).
  - Módulos de Seguridad de Hardware (HSM) dedicados para la custodia de llaves criptográficas y procesamiento de tarjetas (PCI-DSS Nivel 1).
  - Simulacros mensuales de intrusión (Red Team vs Blue Team) y programa público de recompensas por hallazgo de vulnerabilidades (Bug Bounty).

---

### R5. Riesgo Cambiario & Macroeconómico
- **Descripción:** Devaluación súbita de monedas locales en países donde no circule el USD (Colón costarricense, Quetzal guatemalteco) que afecte la rentabilidad de las inversiones locales.
- **Impacto Potencial:** Medio.
- **Estrategia de Mitigación:**
  - La operación central y la mayor parte del portafolio se estructuran en **Dólares de los Estados Unidos (USD)**, aprovechando la dolarización total de Panamá y El Salvador.
  - Para operaciones en Costa Rica y Guatemala, se implementa una política de **cobertura cambiaria automática (FX Forwards / Swaps)** gestionada por la Mesa de Dinero de BTG Pactual para neutralizar el riesgo de tipo de cambio en el balance.

---

## 3. Matriz de Contingencias y Triggers de Intervención

| Indicador Clave (KPI) | Rango Normal | Alerta Amarilla (Intervención) | Alerta Roja (Acción Inmediata) |
|---|---|---|---|
| **Índice de Cartera Vencida (NPL >90d)** | < 2.0% | 2.0% - 3.5% *(Ajuste de corte de score)* | > 3.5% *(Congelar expansión de cupos)* |
| **Tiempo de Inactividad (Downtime mensual)** | < 15 min | 15 - 45 min *(Revisión de infraestructura)* | > 45 min *(Failover automático a backup)* |
| **Quema Mensual de Presupuesto (Burn Rate)** | < $450K/mes | $450K - $600K/mes *(Revisar CAC)* | > $600K/mes *(Recortar marketing no orgánico)* |
| **Falsos Positivos de Fraude** | < 0.15% | 0.15% - 0.40% *(Re-entrenar modelo GNN)* | > 0.40% *(Switch a pipeline de reglas base)* |
