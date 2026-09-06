# PhysioSentinel Gait · Iteración 67

## Corrección principal · Pacientes / Evolución longitudinal

- El histórico ya no usa únicamente la primera fila física de `gait_patients` para un código clínico.
- Se agregan todas las filas de Supabase que compartan el mismo código de paciente, evitando la reaparición aparente de registros cuando existen duplicados históricos de `patient_id`.
- La lista de pacientes se deduplica por `code` en la interfaz.
- El borrado de uno o varios registros mantiene la eliminación por `session_id` exacto y añade una verificación final de lote contra una lectura nueva de todo el paciente lógico.
- Si alguno de los `session_id` seleccionados sigue presente tras el DELETE, la app no muestra éxito y enumera los IDs no eliminados.
- Los registros sin métricas permanecen visibles en el histórico para que también puedan seleccionarse y borrarse.
- Se conserva la opción de borrar el paciente completo y todo su histórico.

No se modifican los cálculos biomecánicos, IC/TO, sincronización, calibración, reconstrucción 3D ni métricas.
