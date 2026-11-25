# Backlog — dependency ordered
Todos NECESSARY abaixo, execução sequencial após bootstrap aprovado. IDs estáveis.
| WO | Entrega | Dependência | Aceite |
|---|---|---|---|
| NMO-BOOTSTRAP-001 | Source Pack, governança, CI docs | repo inicial | pacote auditado, bloqueios registrados |
| NMO-CORE-WO-001 | scaffold, toolchain, CI, Compose, DB, auth/RBAC | bootstrap | AC01 login/isolamento, tests/build, sem dados reais |
| NMO-DOM-WO-001 | workforce, contratos, casos e policy versionada | CORE | AC02 matriz aplicada e histórico |
| NMO-DOC-WO-001 | storage, upload, quarantine/scan e evidência | DOM | AC03 arquivos privados, maliciosos bloqueados |
| NMO-AI-WO-001 | OCR/classificação/extrator e regras | DOC | AC04 origem/confiança/abstenção, zero falso READY crítico |
| NMO-OPS-WO-001 | fila humana, pendências, vencimentos, transições | AI | AC05 review obrigatório, expiração e rejeição |
| NMO-DEL-WO-001 | dossiê, submissão manual, decisão externa | OPS | AC06 manifesto e prova externa |
| NMO-UI-WO-001 | dashboard, resultados, relatório, UX/accessibility | DEL | AC07 métricas dedup e E2E |
| NMO-REL-WO-001 | hardening, benchmark, backup/restore, deploy autorizado | UI | AC08 DoD, segurança e smoke |
| NMO-PILOT-WO-001 | validação comercial e gate dados reais | REL + LGPD/SST + cliente | aceite explícito e métricas reais |
IMPORTANT/FUTURE: ver scope, não iniciar antes do MVP. Comercial pode entrevistar em paralelo sem dados reais ou compromissos não autorizados. Cada WO terá Context Lock, preflight, riscos, acceptance, tests e Evidence Bundle específico. Não emitir próximo WO com correção pendente.
