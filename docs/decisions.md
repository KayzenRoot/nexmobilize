# Decisions Ledger
Somente autorização explícita/ratificação e auditoria promovem PROPOSED para APPROVED.
| ID | Estado | Decisão proposta | Motivo / alternativas |
|---|---|---|---|
| ADR-001 | PROPOSED | OaaS de prestadoras industriais, dossiê revisado como resultado controlável | Aprovação externa não garantida; alternativa SaaS puro |
| ADR-002 | PROPOSED | Modular monolith + PostgreSQL + worker | Simplicidade; microsserviços futuros |
| ADR-003 | PROPOSED | IA assistiva, regras determinísticas, revisão humana | Evita decisões ocupacionais autônomas; alternativa manual |
| ADR-004 | PROPOSED | Dados sintéticos até gate LGPD/SST; storage privado | Dados sensíveis e isolamento; sem LLM externo real |
| ADR-005 | PROPOSED | Docker local, CI gratuito se comprovado; hosting a qualificar | Sem custos autorizados; avaliar VPS/serviço gerenciado |
| ADR-006 | PROPOSED | Modelo híbrido comercial e piloto assistido | Validar margem, demanda e SLA antes de escalar |
| ADR-007 | PROPOSED | Submissão manual autorizada no MVP | Evitar conectores frágeis/credenciais compartilhadas |
| ADR-008 | PROPOSED | Git público somente código/docs sintéticos; verificar privacidade antes de piloto | Proteger dados, segredos e propriedade intelectual |
