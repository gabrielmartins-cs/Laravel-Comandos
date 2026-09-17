🚩 COMANDO  PARA RODAR A MIGRATION
php artisan migrate --path=database/migrations/2026_09_16_152508_create_tabela_configuracoes_gerais_e_prompt_ia.php

php artisan migrate --path=database/migrations/2026_09_16_173149_alter_tabela_prompt_ia.php

🚩 COMANDO  CRIAR MODEL
php artisan make:model ConfiguracaoGeralInteligenciaArtificial

🚩INSERIR DADOS: 
\App\Models\ConfiguracaoGeralInteligenciaArtificial::criarPrompt([
    'prompt' => "Atue como o CÉREBRO PRINCIPAL da defesa jurídica em contestação civil e securitária.\nAbaixo, forneço os FATOS DO PROCESSO extraídos e a lista completa de teses disponíveis no sistema:\n\n=== FATOS DO PROCESSO ===\n{fatos_processo}\n\n=== CATÁLOGO DE TESES DISPONÍVEIS ===\n{teses_para_avaliacao}\n\n=== REGRAS DE SELEÇÃO E ELEGIBILIDADE ===\n1. REGULARIDADE DA CONTRATAÇÃO: Se o autor alegar cobrança indevida, venda casada ou ausência de contratação, SELECIONE OBRIGATORIAMENTE a tese 'DA REGULARIDADE DA CONTRATAÇÃO E DA INEXISTÊNCIA DE VENDA CASADA'.\n2. PRESCRIÇÃO / DECADÊNCIA: Se 'ha_certificado_prescrito' for TRUE ou se 'maior_tempo_decorrido_anos' for maior ou igual a 1, SELECIONE OBRIGATORIAMENTE as teses referentes a PRESCRIÇÃO (ex: Prescrição Trienal/Anual). Avalie cada certificado da lista 'certificados_detalhados'.\n3. RESTITUIÇÃO EM DOBRO: Se houver pedido de devolução/restituição em dobro ou repetição de indébito, SELECIONE OBRIGATORIAMENTE a tese 'DA AUSÊNCIA DE MÁ-FÊ DA SEGURADORA - DESCABIMENTO DA RESTITUIÇÃO EM DOBRO'.\n4. AUSÊNCIA DE PRETENSÃO RESISTIDA: Se 'ausencia_contato_adm' for TRUE ou 'cancelamento_incompleto' for TRUE, SELECIONE OBRIGATORIAMENTE a tese 'DA ATUAÇÃO ADMINISTRATIVA E AUSÊNCIA DE RESISTÊNCIA DA SEGURADORA' (ou nome equivalente no catálogo).\n5. CANCELAMENTO / RESTITUIÇÃO ADMINISTRATIVA: Se 'cancelamento_realizado' for TRUE, SELECIONE OBRIGATORIAMENTE a tese 'DO CANCELAMENTO E DA RESTITUIÇÃO ADMINISTRATIVA'.\n6. ESPECIALIDADE / CDC: Em QUALQUER ação que envolva contratos de seguro regidos pela SUSEP/CNSP ou alegações de CDC, SELECIONE OBRIGATORIAMENTE a tese 'DA IMPOSSIBILIDADE DA INCIDÊNCIA DO CÓDIGO DE DEFESA DO CONSUMIDOR EM RAZÃO DO PRINCÍPIO DA ESPECIALIDADE'.\n7. COAÇÃO (BLOQUEIO RIGOROSO): NUNCA selecione a tese 'DA IMPUGNAÇÃO À ALEGAÇÃO DE COAÇÃO' a menos que 'alega_coacao' seja estritamente TRUE nos fatos.\n8. INGRESSO ESPONTÂNEO CAIXA VIDA: Se 'empresa_responsavel_caixa_vida' === true E 'caixa_vida_no_polo_passivo' === false, SELECIONE OBRIGATORIAMENTE a tese 'INGRESSO ESPONTÂNEO NA LIDE PELA CAIXA VIDA E PREVIDÊNCIA S.A.'. BLOQUEIO ABSOLUTO: Se 'caixa_vida_no_polo_passivo' === true, É PROIBIDO selecionar esta tese.",
    'instrucao' => 'Você é um advogado sênior. Selecione APENAS os IDs das teses aplicáveis ao caso. Retorne APENAS o JSON.',
    'saida' => 'Retorne ESTRITAMENTE um objeto JSON no formato: { "teses_validadas": [id1, id2, id3...] } contendo os IDs numéricos das teses aplicáveis ao caso.',
    'empresa' => 'CVP',
    'identificador' => 'processamentoIa_teses'
]);


DB::table('prompt_ia')->get();
DB::table('dossie_processamentos')->get();
DB::table('palavras_teses')->get();
DB::table('ia_consumos')->get();
DB::table('teses_formatadas')->get();
DB::table('auditoria_aut_dossie')->get();


🚩 exibir 10 casos: \
DB::table('auditoria_aut_dossie')->limit(10)->get()   \
DB::table('auditoria_aut_dossie') ->orderBy('id', 'desc') ->limit(10) ->get() \
DB::select("SELECT TOP 10 * FROM auditoria_aut_dossie ORDER BY id DESC") \





