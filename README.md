# DMA — Diagnóstico de Maturidade Administrativa

Planilha de diagnóstico do **backoffice** de clínicas: **106 verificações** em 5 módulos, que geram um índice de maturidade de 0 a 100.

Arquivo: `DMA_Integrado_106_Verificacoes_Sem_Contratos.xlsx` (versão **sem gestão de contratos**).

## Para que serve

O objetivo é saber, antes de assumir a administração de uma clínica, **como está a organização administrativa dela**. O diagnóstico responde:

- O que a clínica já faz bem e o que não faz?
- Onde estão os riscos (financeiro, folha, acessos, dados)?
- A clínica está pronta para uma **operação híbrida**, em que uma administradora compartilhada assume rotinas administrativas junto com a equipe local?
- Quantas horas de trabalho por mês a administradora vai assumir (aba *Carga operacional*)?

As 106 perguntas **não são enviadas inteiras ao dono da clínica**. Boa parte das respostas vem de conversa com o proprietário, observação das rotinas e análise de documentos. A planilha é o **roteiro e o registro** do avaliador, não um formulário para o cliente preencher.

## Escopo

**Dentro:** administração financeira, pessoal administrativo, processos, tecnologia e governança.

**Fora:** gestão de contratos de fornecedores, renovações, reajustes, compras e estoque. O módulo CON e seus 12 itens foram removidos. Contratos de trabalho, contratos de prestação de serviços e documentos comprobatórios continuam existindo. Só a atividade de administrar contratos de fornecedores das clínicas ficou de fora.

**Responsabilidade:** a clínica continua autorizando e executando os pagamentos. Ela também mantém as decisões trabalhistas, empresariais e assistenciais.

## Módulos

| Módulo | Área | Itens | Peso geral |
|---|---|---|---|
| FIN | Financeiro | 30 | 33,33% |
| PES | Pessoal administrativo | 20 | 16,67% |
| PRO | Processos | 20 | 16,67% |
| TEC | Tecnologia | 20 | 16,67% |
| GOV | Governança | 16 | 16,67% |

Cada módulo se divide em dimensões, 25 no total, com peso interno próprio. Exemplos:

- **FIN-1** — faturamento e caixa
- **FIN-2** — recebíveis e cartões
- **FIN-3** — pagamentos
- **FIN-4** — conciliação bancária
- **FIN-5** — fluxo de caixa e gestão
- **FIN-6** — controles e papéis
- **PES-4** — folha (25% do módulo)
- **PES-5** — processos de pessoal (30% do módulo)

Os pesos do módulo PES são: cadastro 20%, jornada 10%, férias 15%, folha 25% e processos 30%.

## Abas da planilha

| Aba | Conteúdo |
|---|---|
| Instruções | Escopo, método, regras de cálculo e avisos de segurança |
| Pesos | Peso de cada módulo e de cada dimensão |
| Registro 106 | Aqui se trabalha: uma linha por verificação, com pergunta, método, fonte, status, nota, evidência, achado, risco, ação, responsável e data |
| Dimensões | Cálculo por dimensão (itens avaliados, NV, NA, cobertura, nota, pontos ponderados), feito por fórmulas |
| Painel geral | Maturidade por módulo, cobertura, índice geral e riscos críticos |
| Riscos e ações | Plano de ação: problema, risco, se bloqueia a atividade, ação corretiva, responsável, prazo e validação |
| Carga operacional | Estimativa de horas/mês da administradora (pagamentos, recebimentos e cartões, conciliações, pessoal, relacionamento, supervisão) |

## Como pontuar

Escala de 0 a 4 para cada item:

| Nota | Nível | Significado |
|---|---|---|
| 0 | Inexistente | Não há rotina ou controle demonstrável |
| 1 | Informal | Feito sem padrão, depende de pessoas |
| 2 | Parcial | Existe controle, mas com lacunas, atrasos ou inconsistências |
| 3 | Estruturado | Documentado e aplicado, com evidência periódica |
| 4 | Controlado | Como o 3, mais revisão, indicadores e correção de desvios |

Status do item:

- **Avaliado (V):** tem nota de 0 a 4.
- **NV (não verificado):** nunca vale zero. Reduz a *cobertura* e impede conclusão automática.
- **NA (não aplicável):** exige justificativa e sai do denominador da dimensão.

Fórmulas:

- **Nota da dimensão** = média das notas válidas × 25, ou seja, uma escala de 0 a 100.
- **Pontos ponderados** = nota da dimensão × peso interno.
- **Nota do módulo** = soma dos pontos ponderados das suas dimensões.
- **Índice geral** = média ponderada dos 5 módulos. Não há resultado conclusivo enquanto alguma dimensão estiver sem avaliação válida.
- **Cobertura** = avaliados / (avaliados + NV).

Riscos críticos, como bloqueios de segurança e acessos, **não são compensados** por uma nota alta em outro lugar.

## Estado atual do arquivo

O arquivo traz um diagnóstico preenchido, com os 106 itens como "Avaliado". Parece ser um caso real ou um exemplo. A coluna de risco está toda como "Não classificado". Faltam também evidências, responsáveis e datas, e as abas *Riscos e ações* e *Carga operacional* estão vazias.

| Módulo | Maturidade (0–100) |
|---|---|
| FIN | 10,75 |
| PES | 8,13 |
| PRO | 25,63 |
| TEC | 45,00 |
| GOV | 23,44 |
| **Índice geral** | **20,61** |

Leitura: o financeiro e o pessoal são os pontos mais fracos, com caixa, cartões, pagamentos e conciliação praticamente sem controle. A tecnologia é o ponto mais forte, com dados exportáveis e integração viável. O ponto fraco é a segurança e a governança dos acessos.

## DMA Studio (protótipo HTML)

Arquivo: `DMA_Studio_Exemplo_Com_106_Respostas.html`. É a mesma planilha como app de arquivo único, gerado pelo ChatGPT. Não precisa de servidor: abre direto no navegador.

- **Dados:** as 106 perguntas, os pesos e as respostas de exemplo estão embutidos no HTML. As respostas de exemplo são as mesmas do `.xlsx`. O estado fica no `localStorage` do navegador, na chave `dma-studio-106-v2-demo`.
- **Telas:**
  - Visão geral: índice DMA, módulos e riscos.
  - Diagnóstico: as 106 perguntas, com nota 0–4 ou NA, evidência, achado, ação, responsável e risco.
  - Plano de ação: gerado automaticamente a partir de notas 0–1 ou risco alto/crítico, exportável em CSV.
  - Carga operacional: horas/mês da administradora, calculadas a partir de volume e minutos por unidade.
  - Relatório REDA: relatório executivo imprimível ou exportável em PDF.
  - Carteira de clínicas: várias clínicas, com comparação entre elas.
  - Configurações: dados da clínica e limiares de decisão.
- **Regras extras que não existem na planilha:**
  - Controles-gatilho: FIN-14, FIN-20, TEC-13, TEC-14, TEC-16 e TEC-18 exigem nota mínima 3. Risco crítico impede a recomendação automática de prontidão.
  - Limiares ajustáveis: maturidade aceitável 70%, alta 85%, mínimo financeiro 60%, mínimo pessoal 60% e cobertura de evidências 80%.
  - Classificação: Alta (85 ou mais), Aceitável (70 ou mais), Em desenvolvimento (60 ou mais), Baixa (40 ou mais) e Crítica (abaixo de 40).
- **Exportação e importação:** backup em JSON (exportar e importar) e CSV da clínica ativa.
- **Extras:** maturidade por dimensão na Visão geral (25 barras) e um quadro "Como usar" para quem abre pela primeira vez.
- **Limitações:** sem servidor, sem login e sem sincronização. Limpar os dados do navegador apaga tudo, então é preciso exportar o backup.

## Cuidados

- Não registrar senhas, dados clínicos sensíveis nem documentos pessoais desnecessários. Usar IDs ou links seguros nas evidências.
- A "prontidão para implantação" é uma **decisão humana**, separada da nota.
- O modelo está marcado como *revisado e sujeito a aprovação expressa* dos pesos redistribuídos.
