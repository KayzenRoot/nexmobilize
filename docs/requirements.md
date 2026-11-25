# Requirements
R01 identidade e sessão segura, convites revogáveis, MFA para operadores privilegiados antes de piloto; autorização por tenant e função em toda ação.
R02 cadastro mínimo; vínculo trabalhador-contrato-unidade-função; prevenir duplicidade e exposição cruzada.
R03 matriz de requisitos com fonte, vigência, versão, aprovador humano, aplicabilidade e exceções justificadas; cada caso fixa versão.
R04 upload limitado, hash, tipo real, quarentena, scan, storage privado; downloads autorizados; rejeitar conteúdo executável.
R05 extração estruturada opcional, referências à página/campo, confiança, abstenção; conteúdo de arquivo não é instrução; nenhum envio de dados reais a LLM externo sem aprovação.
R06 avaliação determinística de presença, datas e regras explícitas; ausência, divergência ou incerteza bloqueia prontidão.
R07 revisor humano autoriza cada dossiê; trilha de revisão e rejeição; reabrir se documento expirar ou política mudar.
R08 pendências atribuíveis, alertas deduplicados, prazos configuráveis, estados de falha visíveis.
R09 exportação privada com manifesto hashes, versões, revisão e conteúdo estritamente autorizado.
R10 registrar submissão e resposta externa com fonte/evidência, nunca inferir aprovação; cancelamento, rejeição e reabertura.
R11 dashboard por tenant, SLA controlável, contagem de resultados sem duplicidade, custo por caso, relatório exportável.
R12 retenção, exclusão, exportação e incidentes; logs sem PII; backups e restore testados.
NFR01 isolamento verificável; TLS e criptografia em repouso; mínimos privilégios.
NFR02 acessibilidade teclado/WCAG 2.2 AA como meta; pt-BR, datas localizadas, UTC no banco.
NFR03 operações assíncronas idempotentes, retries limitados, timeouts, DLQ/reprocessamento autorizado.
NFR04 baseline sintético proposto: 100 casos, 1.000 documentos, 5 operadores concorrentes; p95 endpoints de metadados <= 500ms em ambiente declarado, fora upload/OCR; medir custo e tempo de fila.
