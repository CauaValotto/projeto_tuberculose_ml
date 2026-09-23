# Dicionário de Variáveis do SINAN (Tuberculose)

Este documento contém a descrição e o significado de todas as 98 variáveis presentes no arquivo original `dados_tuberculose.csv` do SINAN (Sistema de Informação de Agravos de Notificação) / DATASUS.

---

O arquivo original `dados_tuberculose.csv` possui **98 colunas**, correspondendo a todos os campos oficiais da ficha de notificação e acompanhamento de Tuberculose do SINAN/DATASUS. 

Abaixo apresentamos a tradução completa e o significado por extenso de **todas as 98 variáveis**, organizadas por blocos temáticos e sem códigos numéricos para facilitar a interpretação:

---

#### 1. Identificação da Notificação e Unidade Notificadora
* **Tipo de Notificação (`TP_NOT`):** Identifica que se trata de uma notificação compulsória individual de caso suspeito ou confirmado.
* **Código do Agravo (`ID_AGRAVO`):** Identificador da doença no sistema (Tuberculose, sob os códigos CID-10 A15 a A19).
* **Data da Notificação (`DT_NOTIFIC`):** Data em que a ficha foi formalmente preenchida na unidade de saúde.
* **Ano da Notificação (`NU_ANO`):** Ano em que a notificação foi realizada.
* **Estado Notificador (`SG_UF_NOT`):** Sigla do estado onde a unidade de saúde notificadora está situada.
* **Município Notificador (`ID_MUNICIP`):** Código do município onde a notificação foi emitida.
* **Região de Saúde Notificadora (`ID_REGIONA`):** Região administrativa de saúde onde a unidade notificadora atua.
* **Data do Diagnóstico (`DT_DIAG`):** Data em que a equipe médica confirmou o diagnóstico de tuberculose.
* **Tipo de Unidade Notificadora (`TPUNINOT`):** Classificação do serviço que realizou a notificação (Posto/Unidade Básica de Saúde, Hospital, Pronto-Socorro ou Centro de Referência).

---

#### 2. Dados Pessoais e Sociodemográficos do Paciente
* **Ano de Nascimento (`ANO_NASC`):** Ano em que o paciente nasceu.
* **Idade Bruta (`NU_IDADE_N`):** Idade bruta registrada no formulário oficial do SINAN.
* **Idade em Anos (`IDADE_ANOS`):** Idade do paciente calculada em anos completos (variável contínua chave da análise).
* **Sexo Biológico (`CS_SEXO`):** Sexo registrado do paciente (Masculino ou Feminino).
* **Situação Gestacional (`CS_GESTANT`):** Condição de gravidez e trimestre gestacional no momento da notificação.
* **Raça e Cor (`CS_RACA`):** Raça ou cor autodeclarada pelo paciente (Branca, Preta, Parda, Amarela ou Indígena).
* **Escolaridade (`CS_ESCOL_N`):** Nível de instrução e estudo formal concluído pelo paciente.
* **Ocupação Principal (`ID_OCUPA_N`):** Código da profissão ou ocupação habitual do paciente.

---

#### 3. Local de Residência do Paciente
* **Estado de Residência (`SG_UF`):** Sigla do estado (Unidade da Federação) onde o paciente reside habitualmente.
* **Município de Residência (`ID_MN_RESI`):** Código do município onde o paciente mora.
* **Região de Saúde de Residência (`ID_RG_RESI`):** Região de saúde correspondente ao endereço do paciente.
* **País de Residência (`ID_PAIS`):** País onde o paciente reside (para identificação de residentes no Brasil ou estrangeiros).

---

#### 4. Trâmite Administrativo e Controle do Sistema
* **Controle de Duplicidade (`NDUPLIC_N`):** Verificação de duplicidade de cadastros para evitar contagem repetida do mesmo paciente.
* **Vínculo de Fichas (`IN_VINCULA`):** Indicador de prontuários ou cadastros vinculados ao mesmo histórico clínico.
* **Data de Digitação (`DT_DIGITA`):** Data em que a ficha física foi digitada no sistema informatizado do SINAN.
* **Data de Envio para a Unidade (`DT_TRANSUS`):** Trâmite de transferência de dados para a unidade local.
* **Data de Envio para o Distrito (`DT_TRANSDM`):** Trâmite de transferência de dados para o distrito municipal.
* **Data de Envio para o Município (`DT_TRANSSM`):** Data em que os dados foram transferidos para a Secretaria Municipal de Saúde.
* **Data de Envio para a Região Municipal (`DT_TRANSRM`):** Trâmite de dados no nível regional municipal.
* **Data de Envio para a Regional Estadual (`DT_TRANSRS`):** Trâmite de dados para a regional de saúde do estado.
* **Data de Envio para o Estado (`DT_TRANSSE`):** Data de envio dos dados para a Secretaria Estadual de Saúde.
* **Fluxo de Retorno (`CS_FLXRET`):** Código técnico de retorno de processamento do sistema.
* **Confirmação de Recebimento (`FLXRECEBI`):** Indicador de confirmação de recebimento do pacote de dados.
* **Registro Migrado (`MIGRADO_W`):** Identificador de dados migrados de versões anteriores em Windows do SINAN.

---

#### 5. Histórico Clínico e Forma Anatômica da Doença
* **Tipo de Entrada no Sistema (`TRATAMENTO`):** Como o paciente ingressou no atendimento (Caso novo, Recidiva, Reingresso após abandono, Transferência de outra unidade ou Pós-óbito).
* **Institucionalização (`INSTITUCIO`):** Se o paciente vive em abrigos, asilos, orfanatos ou outras instituições coletivas.
* **Radiografia de Tórax (`RAIOX_TORA`):** Resultado do exame de raio-X pulmonar inicial (Suspeito, Normal, Outra patologia ou Não realizado).
* **Teste Tuberculínico (`TESTE_TUBE`):** Resultado da prova tuberculínica (PPD) para verificar resposta imunológica à bactéria.
* **Forma Clínica da Tuberculose (`FORMA`):** Como a infecção se manifesta no corpo (Pulmonar, Extrapulmonar ou Mista).
* **Primeira Localização Extrapulmonar (`EXTRAPU1_N`):** Local afetado na forma extrapulmonar (pleural, ganglionar periférica, óssea, ocular, meningoencefálica, etc.).
* **Segunda Localização Extrapulmonar (`EXTRAPU2_N`):** Segundo órgão afetado na forma extrapulmonar, quando houver acometimento múltiplo.
* **Outra Localização Extrapulmonar (`EXTRAPUL_O`):** Especificação de outra localização anatômica não contemplada nas opções padrão.

---

#### 6. Comorbidades e Agravos Associados
* **Aids (`AGRAVAIDS`):** Presença de Síndrome da Imunodeficiência Adquirida diagnosticada.
* **Consumo de Álcool (`AGRAVALCOO`):** Histórico de dependência alcoólica ou etilismo crônico como agravo associado.
* **Diabetes Mellitus (`AGRAVDIABE`):** Diagnóstico prévio de diabetes.
* **Doença Mental (`AGRAVDOENC`):** Presença de transtorno psiquiátrico ou doença mental associada.
* **Tabagismo (`AGRAVTABAC`):** Dependência do tabaco (fumante habitual).
* **Uso de Outras Drogas (`AGRAVDROGA`):** Uso de substâncias psicoativas ilícitas.
* **Outros Agravos (`AGRAVOUTRA`):** Presença de outras doenças crônicas ou comorbidades não listadas acima.
* **Descrição de Outros Agravos (`AGRAVOUTDE`):** Especificação textual de outras comorbidades relatadas.

---

#### 7. Exames Laboratoriais e Confirmação Diagnóstica
* **Baciloscopia de Escarro Inicial (`BACILOSC_E`):** Primeiro exame direto no escarro para detecção do bacilo da tuberculose.
* **Segunda Baciloscopia de Escarro (`BACILOS_E2`):** Segunda amostra de escarro para confirmação diagnóstica.
* **Baciloscopia de Outro Material (`BACILOSC_O`):** Exame microscópico direto em outro material biológico (líquido pleural, líquor, urina, etc.).
* **Cultura de Escarro (`CULTURA_ES`):** Cultura microbiológica da amostra de escarro para identificação do bacilo.
* **Cultura de Outro Material (`CULTURA_OU`):** Cultura microbiológica de material extrapulmonar.
* **Sorologia para HIV (`HIV`):** Resultado do teste rápido ou laboratorial para infecção pelo vírus HIV (Positivo, Negativo, Em andamento ou Não realizado).
* **Exame Histopatológico (`HISTOPATOL`):** Resultado da biópsia tecidual com análise microscópica da lesão.
* **Teste Rápido Molecular (`TEST_MOLEC`):** Teste de biologia molecular (TRM-TB / GeneXpert) para detecção rápida do DNA bacteriano e resistência à Rifampicina.
* **Teste de Sensibilidade aos Antimicrobianos (`TEST_SENSI`):** Antibiograma para testar a sensibilidade ou resistência a antibióticos (TSA).

---

#### 8. Esquema Terapêutico e Medicamentos Prescritos
* **Data de Início do Tratamento (`DT_INIC_TR`):** Data em que o paciente tomou a primeira dose dos remédios.
* **Rifampicina (`RIFAMPICIN`):** Uso do antibiótico Rifampicina no esquema padrão.
* **Isoniazida (`ISONIAZIDA`):** Uso do antibiótico Isoniazida no esquema padrão.
* **Etambutol (`ETAMBUTOL`):** Uso do antibiótico Etambutol no esquema padrão.
* **Estreptomicina (`ESTREPTOMI`):** Uso do antibiótico injetável Estreptomicina.
* **Pirazinamida (`PIRAZINAMI`):** Uso do antibiótico Pirazinamida no esquema padrão.
* **Etionamida (`ETIONAMIDA`):** Uso do medicamento de segunda linha Etionamida (usado em casos de resistência ou intolerância).
* **Outras Medicações (`OUTRAS`):** Uso de outros medicamentos antituberculose no esquema terapêutico.
* **Descrição de Outras Medicações (`OUTRAS_DES`):** Nome por extenso de outros remédios especiais prescritos.
* **Tratamento Supervisionado Inicial (`TRAT_SUPER`):** Se foi prevista no início a realização do Tratamento Diretamente Observado (TDO).
* **Terapia Antirretroviral (`ANT_RETRO`):** Uso concomitante de medicamentos antirretrovirais (TARV) para pacientes com HIV.
* **Doença do Trabalho (`DOENCA_TRA`):** Se a infecção por tuberculose possui relação comprovada com o trabalho exercido pelo paciente.

---

#### 9. Investigação de Contatos e Baciloscopias de Controle
* **Total de Contatos Identificados (`NU_CONTATO`):** Quantidade de pessoas que convivem com o paciente identificadas para avaliação preventiva.
* **Contatos Examinados (`NU_COMU_EX`):** Quantidade de contatos que compareceram à unidade e realizaram exames diagnósticos.
* **Baciloscopia do 1º Mês (`BACILOSC_1`):** Exame de controle bacteriológico realizado no 1º mês de medicação.
* **Baciloscopia do 2º Mês (`BACILOSC_2`):** Exame de controle bacteriológico realizado no 2º mês de medicação (fundamental para verificar negativação do escarro).
* **Baciloscopia do 3º Mês (`BACILOSC_3`):** Exame de controle realizado no 3º mês de medicação.
* **Baciloscopia do 4º Mês (`BACILOSC_4`):** Exame de controle realizado no 4º mês de medicação.
* **Baciloscopia do 5º Mês (`BACILOSC_5`):** Exame de controle realizado no 5º mês de medicação.
* **Baciloscopia do 6º Mês (`BACILOSC_6`):** Exame de controle realizado no 6º mês de medicação (ao término do esquema básico).
* **Baciloscopia após o 6º Mês (`BAC_APOS_6`):** Exame de controle em casos que exigem extensão do tratamento além do sexto mês.
* **TDO Atual (`TRATSUP_AT`):** Confirmação se o Tratamento Diretamente Observado foi de fato executado ao longo do acompanhamento.
* **Data de Mudança de Conduta (`DT_MUDANCA`):** Data em que houve troca de medicamentos por efeitos adversos graves, toxicidade hepática ou falha terapêutica.

---

#### 10. Acompanhamento de Transferências e Mudanças
* **Estado de Atendimento Atual (`SG_UF_AT`):** Sigla do estado onde o paciente está sendo atendido atualmente caso tenha se mudado.
* **Município de Atendimento Atual (`ID_MUNIC_A`):** Município onde o paciente está sendo acompanhado atualmente.
* **Data da Notificação Atual (`DT_NOTI_AT`):** Data em que o novo município registrou a continuidade do atendimento.
* **Segundo Estado de Acompanhamento (`SG_UF_2`):** Segundo estado de atendimento em caso de nova migração.
* **Segundo Município de Acompanhamento (`ID_MUNIC_2`):** Segundo município de atendimento em caso de nova migração.
* **Transferência (`TRANSF`):** Indicador de que o paciente foi transferido para outra unidade ou cidade para continuar o tratamento.
* **Estado de Destino (`UF_TRANSF`):** Estado para onde o paciente foi transferido.
* **Município de Destino (`MUN_TRANSF`):** Município para onde o paciente foi transferido.

---

#### 11. Populações Especiais e Vulnerabilidades Sociais
* **População Privada de Liberdade (`POP_LIBER`):** Se o paciente cumpre pena no sistema prisional ou cadeias.
* **População em Situação de Rua (`POP_RUA`):** Se o paciente vive em situação de rua, com alta vulnerabilidade social e desnutrição.
* **Profissional de Saúde (`POP_SAUDE`):** Se o paciente trabalha na área da saúde (maior exposição ocupacional a patógenos respiratórios).
* **População Imigrante (`POP_IMIG`):** Se o paciente é imigrante ou refugiado.
* **Benefício Governamental (`BENEF_GOV`):** Se o paciente ou sua família são beneficiários de programas de transferência de renda (como o Bolsa Família).

---

#### 12. Acompanhamento Trimestral, Encerramento e Desfecho
* **Situação no 9º Mês (`SITUA_9_M`):** Avaliação clínica do paciente no nono mês de acompanhamento para esquemas prolongados.
* **Situação no 12º Mês (`SITUA_12_M`):** Avaliação clínica do paciente no décimo segundo mês de acompanhamento.
* **Situação de Encerramento (`SITUA_ENCE`):** Desfecho final do caso registrado pelo sistema (Cura, Abandono do tratamento, Óbito por tuberculose, Óbito por outras causas, Transferência para outro município ou Erro de diagnóstico).
* **Data de Encerramento (`DT_ENCERRA`):** Data oficial em que o caso foi formalmente encerrado no SINAN.