import pandas as pd
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/drive')

caminho = '/content/drive/MyDrive/INVESTIGAÇÕES/LEVANTAMENTO SENAPPEN/JAN-JUN_2025/18o-ciclo-base-de-dados-2025-1-semestre.csv'

df = pd.read_csv(caminho,delimiter=';', encoding='utf-8', low_memory=False)

df.columns = (
    df.columns.str.strip()
              .str.lower()
              .str.replace(' ', '_')
              .str.replace(r'[^\w\s]', '', regex=True)
              .str.replace('__', '_')

)

pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)

colunas = df.columns.to_list()

colunas

df.head()

df_cela_fisica = df[df['tipo_do_estabelecimento'] == 'Cela física'].reset_index(drop=True)

df_tipo_penal = df_cela_fisica.filter(like='514_quantidade_de_incidências_por_tipo_penal', axis=1)

df_tempo_pena = df_cela_fisica.filter(like='512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas', axis=1)

df_faixa_etaria = df_cela_fisica.filter(like='51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária', axis=1)

df_raça_etnia = df_cela_fisica.filter(like='52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia', axis=1)

df_escolaridade = df_cela_fisica.filter(like='56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução', axis=1)

# Tipo penal | Feminino

df_tipo_penal_fem = df_tipo_penal.filter(like='feminino', axis=1)

df_tipo_penal_fem = df_tipo_penal_fem.dropna(how='all')

df_tipo_penal_fem = df_tipo_penal_fem.fillna(0)

df_tipo_penal_fem.head(10)

df_tipo_penal_fem = df_tipo_penal_fem.astype(int)

df_tipo_penal_fem.rename(columns={
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_simples_art_121_caput_feminino': 'homicidio_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicílio_culposo_art_121_3_feminino': 'homicidio_culposo_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_qualificado_art_121_2_feminino': 'homicidio_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_aborto_art_124_125_126_e_127_feminino': 'aborto_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_lesão_corporal_art_129_caput_e_1_2_3_e_6_feminino': 'lesao_corporal_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_violência_doméstica_art_129__9_feminino': 'violencia_domestica_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_sequestro_e_cárcere_privado_art_148_feminino': 'sequestro_carcere_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_outros_não_listados_acima_entre_os_artigos_122_e_154a_feminino': 'crimes_pessoa_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_simples_art_155_feminino': 'furto_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_qualificado_art_155_4_e_5_feminino': 'furto_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_simples_art_157_feminino': 'roubo_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_qualificado_art_157_2_feminino': 'roubo_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_latrocínio_art_157_3_feminino': 'latrocinio_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_art_158_feminino': 'extorsao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_mediante_sequestro_art_159_feminino': 'extorsao_sequestro_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_art_168_feminino': 'aprop_indebita_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_previdenciária_art_168a_feminino': 'aprop_indebita_prev_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_estelionato_art_171_feminino': 'estelionato_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_art_180_feminino': 'receptacao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_qualificada_art_180_1_feminino': 'receptacao_qualificada_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_outros_não_listados_acima_entre_os_artigos_156_e_179_feminino': 'patrimonio_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_art_213_feminino': 'estupro_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_atentado_violento_ao_pudor_art_214_feminino': 'atentado_pudor_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_de_vulnerável_art_217a_feminino': 'estupro_vulneravel_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_corrupção_de_menores_art_218_feminino': 'corrupcao_menores_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_internacional_de_pessoa_para_fim_de_exploração_sexual_art_231_feminino': 'trafico_pessoas_internac_sex_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_interno_de_pessoa_para_fim_de_exploração_sexual_art_231a_feminino': 'trafico_pessoas_interno_sex_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_outros_artigos_215_216a_218a_218b_227_228_229_230_feminino': 'dignidade_sexual_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_paz_pública_quadrilha_ou_bando_art_288_feminino': 'quadrilha_bando_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_moeda_falsa_art_289_feminino': 'moeda_falsa_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsificação_de_papéis_selos_sinal_e_documentos_públicos_art_293_a_297_feminino': 'falsificacao_docs_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsidade_ideológica_art_299_feminino': 'falsidade_ideologica_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_uso_de_documento_falso_art_304_feminino': 'uso_doc_falso_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_peculato_art_312_e_313_feminino': 'peculato_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_concussão_e_excesso_de_exação_art_316_feminino': 'concussao_exacao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_corrupção_passiva_art_317_feminino': 'corrupcao_passiva_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_corrupção_ativa_art_333_feminino': 'corrupcao_ativa_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_contrabando_ou_descaminho_art_334_feminino': 'contrabando_descaminho_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_de_drogas_art_12_da_lei_636876_e_art_33_da_lei_1134306_feminino': 'trafico_drogas_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_associação_para_o_tráfico_art_14_da_lei_636876_e_art_35_da_lei_1134306_feminino': 'assoc_trafico_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_internacional_de_drogas_art_18_da_lei_636876_e_art_33_e_40_inciso_i_da_lei_1134306_feminino': 'trafico_drogas_internac_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_porte_ilegal_de_arma_de_fogo_de_uso_permitido_art_14_feminino': 'porte_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_disparo_de_arma_de_fogo_art_15_feminino': 'disparo_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_posse_ou_porte_ilegal_de_arma_de_fogo_de_uso_restrito_art_16_feminino': 'posse_porte_arma_restrita_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_comércio_ilegal_de_arma_de_fogo_art_17_feminino': 'comercio_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_tráfico_internacional_de_arma_de_fogo_art_18_feminino': 'trafico_arma_internac_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_crimes_de_trânsito_lei_9503_de_23091997_homicídio_culposo_na_condução_de_veículo_automotor_art_302_feminino': 'homicidio_culposo_transito_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_outros_art_303_a_312_feminino': 'leg_esp_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_estatuto_da_criança_e_do_adolescente_lei_8069_de_13011990_feminino': 'eca_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_genocídio_lei_2889_de_01101956_feminino': 'genocidio_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_de_tortura_lei_9455_de_07041997_feminino': 'tortura_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_contra_o_meio_ambiente_lei_9605_de_12021998_feminino': 'meio_ambiente_fem',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_com_informação_sobre_tipificação_criminal_feminino': 'ppl_com_info_fem',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_sem_informação_sobre_tipificação_criminal_feminino': 'ppl_sem_info_fem',
    '514_quantidade_de_incidências_por_tipo_penal_feminino': 'incidencias_total_fem'
}, inplace=True)

df_tipo_penal_fem = df_tipo_penal_fem.drop(columns=['ppl_com_info_fem','ppl_sem_info_fem','incidencias_total_fem'])

df_tipo_penal_fem.head()

df_tipo_penal_fem_total = df_tipo_penal_fem.sum()

df_tipo_penal_fem_total

plt.figure(figsize=(15, 10))
plt.barh(df_tipo_penal_fem_total.index, df_tipo_penal_fem_total.values)
plt.xticks(rotation=90)
plt.title("Incidências por tipo penal")
plt.ylabel("Tipo Penal")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Tempo de pena | Feminino

df_tempo_pena_fem = df_tempo_pena.filter(like='feminino', axis=1)

df_tempo_pena_fem =df_tempo_pena_fem.dropna(how='all')

df_tempo_pena_fem = df_tempo_pena_fem.fillna(0)

df_tempo_pena_fem = df_tempo_pena_fem.astype(int)

df_tempo_pena_fem.rename(columns={'512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__até_6_meses_inclusive_feminino':'pena_ate_6_meses_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_6_meses_até_1_ano_inclusive_feminino':'pena_6m_a_1a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_1_ano_até_2_anos_inclusive_feminino':'pena_1a_a_2a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_2_até_4_anos_inclusive_feminino':'pena_2a_a_4a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_4_até_8_anos_inclusive_feminino':'pena_4a_a_8a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_8_até_15_anos_inclusive_feminino':'pena_8a_a_15a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_15_até_20_anos_inclusive_feminino':'pena_15a_a_20a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_20_até_30_anos_inclusive_feminino':'pena_20a_a_30a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_30_até_50_anos_inclusive_feminino':'pena_30a_a_50a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_50_até_100_anos_inclusive_feminino':'pena_50a_a_100a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_100_anos_feminino':'pena_mais_100a_fem',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__número_de_pessoas_sem_informação_feminino':'sem_informacao_fem'},
    inplace=True)

df_tempo_pena_fem = df_tempo_pena_fem.sum()

df_tempo_pena_fem

plt.figure(figsize=(16, 8))
plt.barh(df_tempo_pena_fem.index, df_tempo_pena_fem.values)
plt.xticks(rotation=90)
plt.title("Tempo de pena - Presídios femininos")
plt.ylabel("Tempo de pena")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Faixa etária | Feminino

df_faixa_etaria_fem = df_faixa_etaria.filter(like='feminino', axis=1)

df_faixa_etaria_fem  =df_faixa_etaria_fem.dropna(how='all')

df_faixa_etaria_fem = df_faixa_etaria_fem.fillna(0)

df_faixa_etaria_fem = df_faixa_etaria_fem.astype(int)

df_faixa_etaria_fem.rename(columns={'51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_18_a_24_anos_feminino': '18_a_24_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_25_a_29_anos_feminino':'25_a_29_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_30_a_34_anos_feminino':'30_a_34_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_35_a_45_anos_feminino':'35_a_45_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_46_a_60_anos_feminino':'46_a_60_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_61_a_70_anos_feminino':'61_a_70_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_mais_de_70_anos_feminino':'mais_de_70_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_não_informado_feminino':'nao_informado_fem'}, inplace=True)

df_faixa_etaria_fem = df_faixa_etaria_fem.drop(columns=['51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_feminino_total'])

df_faixa_etaria_fem = df_faixa_etaria_fem.sum(axis=0)

df_faixa_etaria_fem

plt.figure(figsize=(16, 8))
plt.barh(df_faixa_etaria_fem.index, df_faixa_etaria_fem.values)
plt.xticks(rotation=90)
plt.title("Faixa etária – Penitenciárias femininas")
plt.ylabel("Faixa etária")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()



# Cor, raça e etnia | Feminino

df_raça_etnia_fem = df_raça_etnia.filter(like='feminino', axis=1)

df_raça_etnia_fem = df_raça_etnia_fem.dropna(how='all')

df_raça_etnia_fem = df_raça_etnia_fem.fillna(0)

df_raça_etnia_fem = df_raça_etnia_fem.astype(int)

df_raça_etnia_fem.rename(columns={'52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_branca_feminino': 'branca_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_preta_feminino':'preta_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_parda_feminino':'parda_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_amarela_feminino':'amarela_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_indígena_feminino':'indígena_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_não_informado_feminino':'nao_informado_fem'}, inplace=True)

df_raça_etnia_fem = df_raça_etnia_fem.drop(columns=['52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_feminino_total'])

df_raça_etnia_fem = df_raça_etnia_fem.sum(axis=0)

df_raça_etnia_fem

plt.figure(figsize=(16, 8))
plt.barh(df_raça_etnia_fem.index, df_raça_etnia_fem.values)
plt.xticks(rotation=90)
plt.title("Pele, raça e etnia – Penitenciárias femininas")
plt.ylabel("Pele, raça e etnia")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()



# Escolaridade | Feminino

df_escolaridade_fem = df_escolaridade.filter(like='feminino', axis=1)

df_escolaridade_fem = df_escolaridade_fem.dropna(how='all')

df_escolaridade_fem = df_escolaridade_fem.fillna(0)

df_escolaridade_fem = df_escolaridade_fem.astype(int)

df_escolaridade_fem.rename(columns={'56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_analfabeto_feminino':'analfabeto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_alfabetizado_sem_cursos_regulares_feminino':'alfabetizado_sem_cursos_regulares_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_incompleto_feminino':'fundamental_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_completo_feminino':'fundamental_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_incompleto_feminino':'médio_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_completo_feminino':'médio_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_incompleto_feminino':'superior_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_completo_feminino':'superior_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_acima_de_superior_completo_feminino':'acima_superior_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_não_informado_feminino':'nao_informado_fem'}, inplace=True)

df_escolaridade_fem = df_escolaridade_fem.drop(columns=['56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_feminino'])

df_escolaridade_fem.head()

df_escolaridade_fem = df_escolaridade_fem.sum(axis=0)

df_escolaridade_fem

plt.figure(figsize=(16, 8))
plt.barh(df_escolaridade_fem.index, df_escolaridade_fem.values)
plt.xticks(rotation=90)
plt.title("Escolaridade – Penitenciárias femininas")
plt.ylabel("Escolaridade")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Tipo penal | Masculino

df_tipo_penal_masc = df_tipo_penal.filter(like='masculino', axis=1)

df_tipo_penal_masc = df_tipo_penal_masc.dropna(how='all')
df_tipo_penal_masc = df_tipo_penal_masc.fillna(0)

df_tipo_penal_masc = df_tipo_penal_masc.astype(int)

df_tipo_penal_masc.rename(columns={
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_simples_art_121_caput_masculino': 'homicidio_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicílio_culposo_art_121_3_masculino': 'homicidio_culposo_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_qualificado_art_121_2_masculino': 'homicidio_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_aborto_art_124_125_126_e_127_masculino': 'aborto_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_lesão_corporal_art_129_caput_e_1_2_3_e_6_masculino': 'lesao_corporal_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_violência_doméstica_art_129__9_masculino': 'violencia_domestica_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_sequestro_e_cárcere_privado_art_148_masculino': 'sequestro_carcere_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_outros_não_listados_acima_entre_os_artigos_122_e_154a_masculino': 'crimes_pessoa_outros_masc',

    # PATRIIMÔNIO
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_simples_art_155_masculino': 'furto_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_qualificado_art_155_4_e_5_masculino': 'furto_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_simples_art_157_masculino': 'roubo_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_qualificado_art_157_2_masculino': 'roubo_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_latrocínio_art_157_3_masculino': 'latrocinio_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_art_158_masculino': 'extorsao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_mediante_sequestro_art_159_masculino': 'extorsao_sequestro_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_art_168_masculino': 'aprop_indebita_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_previdenciária_art_168a_masculino': 'aprop_indebita_prev_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_estelionato_art_171_masculino': 'estelionato_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_art_180_masculino': 'receptacao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_qualificada_art_180_1_masculino': 'receptacao_qualificada_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_outros_não_listados_acima_entre_os_artigos_156_e_179_masculino': 'patrimonio_outros_masc',

    # DIGNIDADE SEXUAL
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_art_213_masculino': 'estupro_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_atentado_violento_ao_pudor_art_214_masculino': 'atentado_pudor_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_de_vulnerável_art_217a_masculino': 'estupro_vulneravel_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_corrupção_de_menores_art_218_masculino': 'corrupcao_menores_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_internacional_de_pessoa_para_fim_de_exploração_sexual_art_231_masculino': 'trafico_pessoas_internac_sex_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_interno_de_pessoa_para_fim_de_exploração_sexual_art_231a_masculino': 'trafico_pessoas_interno_sex_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_outros_artigos_215_216a_218a_218b_227_228_229_230_masculino': 'dignidade_sexual_outros_masc',

    # PAZ PÚBLICA
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_paz_pública_quadrilha_ou_bando_art_288_masculino': 'quadrilha_bando_masc',

    # FÉ PÚBLICA
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_moeda_falsa_art_289_masculino': 'moeda_falsa_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsificação_de_papéis_selos_sinal_e_documentos_públicos_art_293_a_297_masculino': 'falsificacao_docs_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsidade_ideológica_art_299_masculino': 'falsidade_ideologica_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_uso_de_documento_falso_art_304_masculino': 'uso_doc_falso_masc',

    # ADMINISTRAÇÃO PÚBLICA
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_peculato_art_312_e_313_masculino': 'peculato_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_concussão_e_excesso_de_exação_art_316_masculino': 'concussao_exacao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_corrupção_passiva_art_317_masculino': 'corrupcao_passiva_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_corrupção_ativa_art_333_masculino': 'corrupcao_ativa_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_contrabando_ou_descaminho_art_334_masculino': 'contrabando_descaminho_masc',

    # DROGAS
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_de_drogas_art_12_da_lei_636876_e_art_33_da_lei_1134306_masculino': 'trafico_drogas_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_associação_para_o_tráfico_art_14_da_lei_636876_e_art_35_da_lei_1134306_masculino': 'assoc_trafico_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_internacional_de_drogas_art_18_da_lei_636876_e_art_33_e_40_inciso_i_da_lei_1134306_masculino': 'trafico_drogas_internac_masc',

    # ESTATUTO DO DESARMAMENTO
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_porte_ilegal_de_arma_de_fogo_de_uso_permitido_art_14_masculino': 'porte_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_disparo_de_arma_de_fogo_art_15_masculino': 'disparo_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_posse_ou_porte_ilegal_de_arma_de_fogo_de_uso_restrito_art_16_masculino': 'posse_porte_arma_restrita_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_comércio_ilegal_de_arma_de_fogo_art_17_masculino': 'comercio_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_tráfico_internacional_de_arma_de_fogo_art_18_masculino': 'trafico_arma_internac_masc',

    # CRIMES DE TRÂNSITO
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_crimes_de_trânsito_lei_9503_de_23091997_homicídio_culposo_na_condução_de_veículo_automotor_art_302_masculino': 'homicidio_culposo_transito_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_outros_art_303_a_312_masculino': 'leg_esp_outros_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_estatuto_da_criança_e_do_adolescente_lei_8069_de_13011990_masculino': 'eca_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_genocídio_lei_2889_de_01101956_masculino': 'genocidio_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_de_tortura_lei_9455_de_07041997_masculino': 'tortura_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_contra_o_meio_ambiente_lei_9605_de_12021998_masculino': 'meio_ambiente_masc',

    # TOTAIS
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_com_informação_sobre_tipificação_criminal_masculino': 'ppl_com_info_masc',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_sem_informação_sobre_tipificação_criminal_masculino': 'ppl_sem_info_masc',
    '514_quantidade_de_incidências_por_tipo_penal_masculino': 'incidencias_total_masc'
}, inplace=True)

df_tipo_penal_masc = df_tipo_penal_masc.drop(columns=['ppl_com_info_masc','ppl_sem_info_masc','incidencias_total_masc'])

df_tipo_penal_masc.head()

df_tipo_penal_masc_total = df_tipo_penal_masc.sum()

df_tipo_penal_masc_total

plt.figure(figsize=(15, 10))
plt.barh(df_tipo_penal_masc_total.index, df_tipo_penal_masc_total.values)
plt.xticks(rotation=90)
plt.title("Incidências por tipo penal – Masculino")
plt.ylabel("Tipo Penal")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()


# Tempo de pena | Masculino

df_tempo_pena_masc = df_tempo_pena.filter(like='masculino', axis=1)

df_tempo_pena_masc = df_tempo_pena_masc.dropna(how='all')
df_tempo_pena_masc = df_tempo_pena_masc.fillna(0)

df_tempo_pena_masc = df_tempo_pena_masc.astype(int)

df_tempo_pena_masc.rename(columns={
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__até_6_meses_inclusive_masculino':'pena_ate_6_meses_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_6_meses_até_1_ano_inclusive_masculino':'pena_6m_a_1a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_1_ano_até_2_anos_inclusive_masculino':'pena_1a_a_2a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_2_até_4_anos_inclusive_masculino':'pena_2a_a_4a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_4_até_8_anos_inclusive_masculino':'pena_4a_a_8a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_8_até_15_anos_inclusive_masculino':'pena_8a_a_15a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_15_até_20_anos_inclusive_masculino':'pena_15a_a_20a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_20_até_30_anos_inclusive_masculino':'pena_20a_a_30a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_30_até_50_anos_inclusive_masculino':'pena_30a_a_50a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_50_até_100_anos_inclusive_masculino':'pena_50a_a_100a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_100_anos_masculino':'pena_mais_100a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__número_de_pessoas_sem_informação_masculino':'sem_informacao_masc'
}, inplace=True)

df_tempo_pena_masc = df_tempo_pena_masc.sum()

df_tempo_pena_masc

plt.figure(figsize=(16, 8))
plt.barh(df_tempo_pena_masc.index, df_tempo_pena_masc.values)
plt.xticks(rotation=90)
plt.title("Tempo de pena - Presídios masculinos")
plt.ylabel("Tempo de pena")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()


# Faixa etária | Masculino

df_faixa_etaria_masc = df_faixa_etaria.filter(like='masculino', axis=1)

df_faixa_etaria_masc = df_faixa_etaria_masc.dropna(how='all')
df_faixa_etaria_masc = df_faixa_etaria_masc.fillna(0)

df_faixa_etaria_masc = df_faixa_etaria_masc.astype(int)

df_faixa_etaria_masc.rename(columns={
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_18_a_24_anos_masculino': '18_24_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_25_a_29_anos_masculino': '25_29_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_30_a_34_anos_masculino': '30_34_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_35_a_45_anos_masculino': '35_45_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_46_a_60_anos_masculino': '46_60_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_61_a_70_anos_masculino': '61_70_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_mais_de_70_anos_masculino': 'mais_70_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_não_informado_masculino': 'nao_informado_masc'
}, inplace=True)

df_faixa_etaria_masc = df_faixa_etaria_masc.drop(
    columns=['51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_masculino_total']
)

df_faixa_etaria_masc = df_faixa_etaria_masc.sum(axis=0)
df_faixa_etaria_masc

plt.figure(figsize=(16, 8))
plt.barh(df_faixa_etaria_masc.index, df_faixa_etaria_masc.values)
plt.xticks(rotation=90)
plt.title("Faixa etária – Penitenciárias masculinas")
plt.ylabel("Faixa etária")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()


# Cor, raça e etnia | Masculino

df_raca_etnia_masc = df_raça_etnia.filter(like='masculino', axis=1)
df_raca_etnia_masc = df_raca_etnia_masc.dropna(how='all')
df_raca_etnia_masc = df_raca_etnia_masc.fillna(0)
df_raca_etnia_masc = df_raca_etnia_masc.astype(int)

df_raca_etnia_masc.rename(columns={
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_branca_masculino': 'branca_masc',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_preta_masculino': 'preta_masc',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_parda_masculino': 'parda_masc',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_amarela_masculino': 'amarela_masc',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_indígena_masculino': 'indígena_masc',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_não_informado_masculino': 'nao_informado_masc'
}, inplace=True)

df_raca_etnia_masc = df_raca_etnia_masc.drop(
    columns=['52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_masculino_total']
)

df_raca_etnia_masc = df_raca_etnia_masc.sum(axis=0)
df_raca_etnia_masc

plt.figure(figsize=(16, 8))
plt.barh(df_raca_etnia_masc.index, df_raca_etnia_masc.values)
plt.xticks(rotation=90)
plt.title("Pele, raça e etnia – Penitenciárias masculinas")
plt.ylabel("Pele, raça e etnia")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()


# Escolaridade | Masculino

df_escolaridade_masc = df_escolaridade.filter(like='masculino', axis=1)
df_escolaridade_masc = df_escolaridade_masc.dropna(how='all')
df_escolaridade_masc = df_escolaridade_masc.fillna(0)
df_escolaridade_masc = df_escolaridade_masc.astype(int)

df_escolaridade_masc.rename(columns={
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_analfabeto_masculino':'analfabeto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_alfabetizado_sem_cursos_regulares_masculino':'alfabetizado_sem_cursos_regulares_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_incompleto_masculino':'fundamental_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_completo_masculino':'fundamental_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_incompleto_masculino':'médio_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_completo_masculino':'médio_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_incompleto_masculino':'superior_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_completo_masculino':'superior_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_acima_de_superior_completo_masculino':'acima_superior_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_não_informado_masculino':'nao_informado_masc'
}, inplace=True)

df_escolaridade_masc = df_escolaridade_masc.drop(columns=['56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_masculino'])
df_escolaridade_masc.head()

df_escolaridade_masc = df_escolaridade_masc.sum(axis=0)
df_escolaridade_masc

plt.figure(figsize=(16, 8))
plt.barh(df_escolaridade_masc.index, df_escolaridade_masc.values)
plt.xticks(rotation=90)
plt.title("Escolaridade – Penitenciárias masculinas")
plt.ylabel("Escolaridade")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()


df_escolaridade_masc

# Presídios de Tremembé

tremembe = df[df['município'] == 'Tremembé'].reset_index(drop=True)

tremembe

tipo_penal = tremembe.filter(like='514_quantidade_de_incidências_por_tipo_penal', axis=1)

tempo_pena = tremembe.filter(like='512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas', axis=1)

faixa_etaria = tremembe.filter(like='51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária', axis=1)

raça_etnia = tremembe.filter(like='52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia', axis=1)

escolaridade = tremembe.filter(like='56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução', axis=1)

df_tremembe = pd.concat([tremembe['nome_do_estabelecimento'],tipo_penal,tempo_pena, faixa_etaria, raça_etnia, escolaridade],axis=1)

#Pen. Feminina I  "Santa Maria Eufrásia Pelettier



---



df_tremembe_fem = df_tremembe[df_tremembe['nome_do_estabelecimento'] == 'Pen. Feminina I  "Santa Maria Eufrásia Pelettier" de Tremembé + APP'].reset_index(drop=True)

df_tremembe_fem

valor_celula = df_tremembe.at[1, 'nome_do_estabelecimento']

print(valor_celula)

df_tremembe_masc = df_tremembe[df_tremembe['nome_do_estabelecimento'] == 'Penit. "Dr. José Augusto César Salgado" de Tremembé + APP'].reset_index(drop=True)

df_tremembe_masc

dropar_fem = df_tremembe_masc.filter(regex='feminino', axis=1).columns.tolist()

df_tremembe_masc = df_tremembe_masc.drop(columns=dropar_fem, axis=1)

dropar_masc = df_tremembe_fem.filter(regex='masculino', axis=1).columns.tolist()

df_tremembe_fem= df_tremembe_fem.drop(columns=dropar_masc, axis=1)

df_tremembe_fem

# Tipo penal | Pen. Feminina I  "Santa Maria Eufrásia Pelettier


df_tremembe_fem_tipo_penal = df_tremembe_fem.filter(regex='514_quantidade_de_incidências_por_tipo_penal', axis=1)

drop_total_fem = df_tremembe_fem_tipo_penal.filter(regex='total', axis=1).columns.tolist()

df_tremembe_fem_tipo_penal = df_tremembe_fem_tipo_penal.drop(columns=drop_total_fem, axis=1)

df_tremembe_fem_tipo_penal

df_tremembe_fem_tipo_penal = df_tremembe_fem_tipo_penal.drop(columns=['514_quantidade_de_incidências_por_tipo_penal_o_estabelecimento_detém_alguma_forma_de_registro_que_permite_a_obtenção_desta_informação', '514_quantidade_de_incidências_por_tipo_penal_como_é_registrada_essa_informação'], axis=1)

df_tremembe_fem_tipo_penal = df_tremembe_fem_tipo_penal.fillna(0)

df_tremembe_fem_tipo_penal = df_tremembe_fem_tipo_penal.astype(int)

df_tremembe_fem_tipo_penal.columns.tolist()

import matplotlib.pyplot as plt
import numpy as np

df_tremembe_fem_tipo_penal.rename(columns={
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_simples_art_121_caput_feminino': 'homicidio_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicílio_culposo_art_121_3_feminino': 'homicidio_culposo_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_qualificado_art_121_2_feminino': 'homicidio_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_aborto_art_124_125_126_e_127_feminino': 'aborto_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_lesão_corporal_art_129_caput_e_1_2_3_e_6_feminino': 'lesao_corporal_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_violência_doméstica_art_129__9_feminino': 'violencia_domestica_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_sequestro_e_cárcere_privado_art_148_feminino': 'sequestro_carcere_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_outros_não_listados_acima_entre_os_artigos_122_e_154a_feminino': 'crimes_pessoa_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_simples_art_155_feminino': 'furto_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_qualificado_art_155_4_e_5_feminino': 'furto_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_simples_art_157_feminino': 'roubo_simples_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_qualificado_art_157_2_feminino': 'roubo_qualificado_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_latrocínio_art_157_3_feminino': 'latrocinio_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_art_158_feminino': 'extorsao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_mediante_sequestro_art_159_feminino': 'extorsao_sequestro_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_art_168_feminino': 'aprop_indebita_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_previdenciária_art_168a_feminino': 'aprop_indebita_prev_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_estelionato_art_171_feminino': 'estelionato_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_art_180_feminino': 'receptacao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_qualificada_art_180_1_feminino': 'receptacao_qualificada_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_outros_não_listados_acima_entre_os_artigos_156_e_179_feminino': 'patrimonio_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_art_213_feminino': 'estupro_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_atentado_violento_ao_pudor_art_214_feminino': 'atentado_pudor_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_de_vulnerável_art_217a_feminino': 'estupro_vulneravel_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_corrupção_de_menores_art_218_feminino': 'corrupcao_menores_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_internacional_de_pessoa_para_fim_de_exploração_sexual_art_231_feminino': 'trafico_pessoas_internac_sex_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_interno_de_pessoa_para_fim_de_exploração_sexual_art_231a_feminino': 'trafico_pessoas_interno_sex_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_outros_artigos_215_216a_218a_218b_227_228_229_230_feminino': 'dignidade_sexual_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_paz_pública_quadrilha_ou_bando_art_288_feminino': 'quadrilha_bando_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_moeda_falsa_art_289_feminino': 'moeda_falsa_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsificação_de_papéis_selos_sinal_e_documentos_públicos_art_293_a_297_feminino': 'falsificacao_docs_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsidade_ideológica_art_299_feminino': 'falsidade_ideologica_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_uso_de_documento_falso_art_304_feminino': 'uso_doc_falso_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_peculato_art_312_e_313_feminino': 'peculato_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_concussão_e_excesso_de_exação_art_316_feminino': 'concussao_exacao_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_corrupção_passiva_art_317_feminino': 'corrupcao_passiva_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_corrupção_ativa_art_333_feminino': 'corrupcao_ativa_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_contrabando_ou_descaminho_art_334_feminino': 'contrabando_descaminho_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_de_drogas_art_12_da_lei_636876_e_art_33_da_lei_1134306_feminino': 'trafico_drogas_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_associação_para_o_tráfico_art_14_da_lei_636876_e_art_35_da_lei_1134306_feminino': 'assoc_trafico_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_internacional_de_drogas_art_18_da_lei_636876_e_art_33_e_40_inciso_i_da_lei_1134306_feminino': 'trafico_drogas_internac_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_porte_ilegal_de_arma_de_fogo_de_uso_permitido_art_14_feminino': 'porte_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_disparo_de_arma_de_fogo_art_15_feminino': 'disparo_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_posse_ou_porte_ilegal_de_arma_de_fogo_de_uso_restrito_art_16_feminino': 'posse_porte_arma_restrita_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_comércio_ilegal_de_arma_de_fogo_art_17_feminino': 'comercio_arma_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_tráfico_internacional_de_arma_de_fogo_art_18_feminino': 'trafico_arma_internac_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_crimes_de_trânsito_lei_9503_de_23091997_homicídio_culposo_na_condução_de_veículo_automotor_art_302_feminino': 'homicidio_culposo_transito_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_outros_art_303_a_312_feminino': 'leg_esp_outros_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_estatuto_da_criança_e_do_adolescente_lei_8069_de_13011990_feminino': 'eca_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_genocídio_lei_2889_de_01101956_feminino': 'genocidio_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_de_tortura_lei_9455_de_07041997_feminino': 'tortura_fem',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_contra_o_meio_ambiente_lei_9605_de_12021998_feminino': 'meio_ambiente_fem',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_com_informação_sobre_tipificação_criminal_feminino': 'ppl_com_info_fem',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_sem_informação_sobre_tipificação_criminal_feminino': 'ppl_sem_info_fem',
    '514_quantidade_de_incidências_por_tipo_penal_feminino': 'incidencias_total_fem'
}, inplace=True)

df_tremembe_fem_tipo_penal

df_tremembe_fem_tipo_penal = df_tremembe_fem_tipo_penal.drop(columns=['ppl_com_info_fem','ppl_sem_info_fem','incidencias_total_fem'])

serie_fem_tipo_penal = df_tremembe_fem_tipo_penal.iloc[0]
serie_fem_tipo_penal = serie_fem_tipo_penal[serie_fem_tipo_penal > 0]


plt.figure(figsize=(15, 10))
plt.barh(serie_fem_tipo_penal.index, serie_fem_tipo_penal.values)
plt.xticks(rotation=90)
plt.title('Incidências por tipo penal – Pen. Feminina I  "Santa Maria Eufrásia Pelettier"')
plt.ylabel("Tipo Penal")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

df_tremembe_fem.columns.tolist()

df_tremembe_fem_pena = df_tremembe_fem.filter(regex='512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas', axis=1)

# Tempo de pena | Pen. Feminina I  "Santa Maria Eufrásia Pelettier


df_tremembe_fem_pena = df_tremembe_fem_pena.drop(columns=['512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',	'512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__como_é_registrada_essa_informação', '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__número_de_pessoas_sem_informação_feminino'])

df_tremembe_fem_pena

df_tremembe_fem_pena.rename(columns={'512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__até_6_meses_inclusive_feminino':'pena_ate_6_meses_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_6_meses_até_1_ano_inclusive_feminino':'pena_6m_a_1a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_1_ano_até_2_anos_inclusive_feminino':'pena_1a_a_2a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_2_até_4_anos_inclusive_feminino':'pena_2a_a_4a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_4_até_8_anos_inclusive_feminino':'pena_4a_a_8a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_8_até_15_anos_inclusive_feminino':'pena_8a_a_15a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_15_até_20_anos_inclusive_feminino':'pena_15a_a_20a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_20_até_30_anos_inclusive_feminino':'pena_20a_a_30a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_30_até_50_anos_inclusive_feminino':'pena_30a_a_50a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_50_até_100_anos_inclusive_feminino':'pena_50a_a_100a_fem',

    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_100_anos_feminino':'pena_mais_100a_fem'}, inplace=True)

df_tremembe_fem_pena.astype(int)

serie_fem_pena = df_tremembe_fem_pena.iloc[0]
serie_fem_pena = serie_fem_pena[serie_fem_pena > 0]

plt.figure(figsize=(16, 8))
plt.barh(serie_fem_pena.index, serie_fem_pena.values)
plt.xticks(rotation=90)
plt.title('Tempo de pena – Pen. Feminina I  "Santa Maria Eufrásia Pelettier"')
plt.ylabel("Tempo de pena")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

#Faixa etária | Pen. Feminina I  "Santa Maria Eufrásia Pelettier


df_tremembe_fem_idade = df_tremembe_fem.filter(regex='51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária', axis=1)

drop_total_fem_idade = df_tremembe_fem_idade.filter(regex='total', axis=1).columns.tolist()

df_tremembe_fem_idade = df_tremembe_fem_idade.drop(columns=['51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',	'51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_não_informado_feminino'])

df_tremembe_fem_idade = df_tremembe_fem_idade.drop(columns=drop_total_fem_idade, axis=1)

df_tremembe_fem_idade = df_tremembe_fem_idade.astype(int)

df_tremembe_fem_idade.rename(columns={'51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_18_a_24_anos_feminino': '18_a_24_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_25_a_29_anos_feminino':'25_a_29_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_30_a_34_anos_feminino':'30_a_34_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_35_a_45_anos_feminino':'35_a_45_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_46_a_60_anos_feminino':'46_a_60_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_61_a_70_anos_feminino':'61_a_70_anos_fem',
 '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_mais_de_70_anos_feminino':'mais_de_70_anos_fem'}, inplace=True)

serie_fem_idade = df_tremembe_fem_idade.iloc[0]
serie_fem_idade = serie_fem_idade[serie_fem_idade > 0]

plt.figure(figsize=(16, 8))
plt.barh(serie_fem_idade.index, serie_fem_idade.values)
plt.xticks(rotation=90)
plt.title("Faixa etária – Penitenciária Feminina II de Tremembé")
plt.ylabel("Faixa etária")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

#Pele, raça e etnia | Pen. Feminina I  "Santa Maria Eufrásia Pelettier


df_tremembe_fem_raça = df_tremembe_fem.filter(regex='52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia', axis=1)

drop_total_fem_raça = df_tremembe_fem_raça.filter(regex='total', axis=1).columns.tolist()

df_tremembe_fem_raça = df_tremembe_fem_raça.drop(columns=['52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
                                                                              '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_não_informado_feminino',
                                                                              '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_povo_indígena',
                                                                              '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_idioma',
                                                                              '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_quantidade'])

df_tremembe_fem_raça = df_tremembe_fem_raça.drop(columns=drop_total_fem_raça, axis=1)

df_tremembe_fem_raça.columns.tolist()

df_tremembe_fem_idade = df_tremembe_fem_idade.astype(int)

df_tremembe_fem_raça.rename(columns={'52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_branca_feminino': 'branca_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_preta_feminino':'preta_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_parda_feminino':'parda_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_amarela_feminino':'amarela_feminino',
 '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_indígena_feminino':'indígena_feminino'}, inplace=True)

serie_fem_raça = df_tremembe_fem_raça.iloc[0]

plt.figure(figsize=(12, 6))
plt.barh(serie_fem_raça.index, serie_fem_raça.values)
plt.xticks(rotation=90)
plt.title('Pele, raça e etnia – Pen. Feminina I  "Santa Maria Eufrásia Pelettier"')
plt.ylabel("Pele, raça e etnia")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

#Escolaridade | Pen. Feminina I  "Santa Maria Eufrásia Pelettier


df_tremembe_fem_esc = df_tremembe_fem.filter(regex='56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução', axis=1)

drop_total_fem_esc = df_tremembe_fem_esc.filter(regex='total', axis=1).columns.tolist()

df_tremembe_fem_esc = df_tremembe_fem_esc.drop(columns=drop_total_fem_esc, axis=1)

df_tremembe_fem_esc = df_tremembe_fem_esc.drop(columns=['56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
                                               '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_não_informado_feminino',
                                               '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_feminino'])

df_tremembe_fem_esc.columns.tolist()

df_tremembe_fem_esc = df_tremembe_fem_esc.astype(int)

df_tremembe_fem_esc.rename(columns={'56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_analfabeto_feminino':'analfabeto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_alfabetizado_sem_cursos_regulares_feminino':'alfabetizado_sem_cursos_regulares_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_incompleto_feminino':'fundamental_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_completo_feminino':'fundamental_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_incompleto_feminino':'médio_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_completo_feminino':'médio_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_incompleto_feminino':'superior_incompleto_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_completo_feminino':'superior_completo_fem',
                                    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_acima_de_superior_completo_feminino':'acima_superior_completo_fem'}, inplace=True)

serie_fem_esc = df_tremembe_fem_esc.iloc[0]
serie_fem_esc = serie_fem_esc[serie_fem_esc > 0]

plt.figure(figsize=(12, 6))
plt.barh(serie_fem_esc.index, serie_fem_esc.values)
plt.xticks(rotation=90)
plt.title('Grau de escolaridade – Pen. Feminina I  "Santa Maria Eufrásia Pelettier"')
plt.ylabel("Grau de escolaridade")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Tipo penal | Penitenciária Dr. José Augusto César Salgado de Tremembé

df_tremembe_masc.columns.tolist()

df_tremembe_masc_tipo_penal = df_tremembe_masc.filter(regex='514_quantidade_de_incidências_por_tipo_penal', axis=1)

drop_total_masc = df_tremembe_masc_tipo_penal.filter(regex='total', axis=1).columns.tolist()

df_tremembe_masc_tipo_penal = df_tremembe_masc_tipo_penal.drop(columns=drop_total_masc, axis=1)

df_tremembe_masc_tipo_penal = df_tremembe_masc_tipo_penal.drop(columns=['514_quantidade_de_incidências_por_tipo_penal_o_estabelecimento_detém_alguma_forma_de_registro_que_permite_a_obtenção_desta_informação', '514_quantidade_de_incidências_por_tipo_penal_como_é_registrada_essa_informação'], axis=1)

df_tremembe_masc_tipo_penal = df_tremembe_masc_tipo_penal.astype(int)

df_tremembe_masc_tipo_penal.rename(columns={
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_simples_art_121_caput_masculino': 'homicidio_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicílio_culposo_art_121_3_masculino': 'homicidio_culposo_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_homicídio_qualificado_art_121_2_masculino': 'homicidio_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_aborto_art_124_125_126_e_127_masculino': 'aborto_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_lesão_corporal_art_129_caput_e_1_2_3_e_6_masculino': 'lesao_corporal_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_violência_doméstica_art_129__9_masculino': 'violencia_domestica_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_sequestro_e_cárcere_privado_art_148_masculino': 'sequestro_carcere_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_pessoa_outros_não_listados_acima_entre_os_artigos_122_e_154a_masculino': 'pessoa_outros_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_simples_art_155_masculino': 'furto_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_furto_qualificado_art_155_4_e_5_masculino': 'furto_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_simples_art_157_masculino': 'roubo_simples_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_roubo_qualificado_art_157_2_masculino': 'roubo_qualificado_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_latrocínio_art_157_3_masculino': 'latrocinio_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_art_158_masculino': 'extorsao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_extorsão_mediante_sequestro_art_159_masculino': 'extorsao_sequestro_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_art_168_masculino': 'aprop_indebita_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_apropriação_indébita_previdenciária_art_168a_masculino': 'aprop_indebita_prev_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_estelionato_art_171_masculino': 'estelionato_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_art_180_masculino': 'receptacao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_receptação_qualificada_art_180_1_masculino': 'receptacao_qualificada_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_o_patrimônio_outros_não_listados_acima_entre_os_artigos_156_e_179_masculino': 'patrimonio_outros_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_art_213_masculino': 'estupro_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_atentado_violento_ao_pudor_art_214_masculino': 'atentado_pudor_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_estupro_de_vulnerável_art_217a_masculino': 'estupro_vulneravel_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_corrupção_de_menores_art_218_masculino': 'corrupcao_menores_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_internacional_de_pessoa_para_fim_de_exploração_sexual_art_231_masculino': 'trafico_pessoas_intl_sex_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_tráfico_interno_de_pessoa_para_fim_de_exploração_sexual_art_231a_masculino': 'trafico_pessoas_int_sex_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_dignidade_sexual_outros_artigos_215_216a_218a_218b_227_228_229_230_masculino': 'dignidade_sexual_outros_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_paz_pública_quadrilha_ou_bando_art_288_masculino': 'quadrilha_bando_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_moeda_falsa_art_289_masculino': 'moeda_falsa_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsificação_de_papéis_selos_sinal_e_documentos_públicos_art_293_a_297_masculino': 'falsificacao_docs_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_falsidade_ideológica_art_299_masculino': 'falsidade_ideologica_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_fé_pública_uso_de_documento_falso_art_304_masculino': 'uso_doc_falso_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_peculato_art_312_e_313_masculino': 'peculato_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_concussão_e_excesso_de_exação_art_316_masculino': 'concussao_exacao_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_contra_a_administração_pública_corrupção_passiva_art_317_masculino': 'corrupcao_passiva_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_corrupção_ativa_art_333_masculino': 'corrupcao_ativa_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_código_penal_grupo_crimes_praticados_por_particular_contra_a_administração_pública_contrabando_ou_descaminho_art_334_masculino': 'contrabando_descaminho_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_de_drogas_art_12_da_lei_636876_e_art_33_da_lei_1134306_masculino': 'trafico_drogas_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_associação_para_o_tráfico_art_14_da_lei_636876_e_art_35_da_lei_1134306_masculino': 'assoc_trafico_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_drogas_lei_636876_e_lei_1134306_tráfico_internacional_de_drogas_art_18_da_lei_636876_e_art_33_e_40_inciso_i_da_lei_1134306_masculino': 'trafico_drogas_intl_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_porte_ilegal_de_arma_de_fogo_de_uso_permitido_art_14_masculino': 'porte_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_disparo_de_arma_de_fogo_art_15_masculino': 'disparo_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_posse_ou_porte_ilegal_de_arma_de_fogo_de_uso_restrito_art_16_masculino': 'posse_porte_arma_restrita_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_comércio_ilegal_de_arma_de_fogo_art_17_masculino': 'comercio_arma_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_estatuto_do_desarmamento_lei_10826_de_22122003_tráfico_internacional_de_arma_de_fogo_art_18_masculino': 'trafico_arma_intl_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_crimes_de_trânsito_lei_9503_de_23091997_homicídio_culposo_na_condução_de_veículo_automotor_art_302_masculino': 'homicidio_culposo_transito_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_outros_art_303_a_312_masculino': 'leg_esp_outros_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_estatuto_da_criança_e_do_adolescente_lei_8069_de_13011990_masculino': 'eca_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_genocídio_lei_2889_de_01101956_masculino': 'genocidio_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_de_tortura_lei_9455_de_07041997_masculino': 'tortura_masc',
    '514_quantidade_de_incidências_por_tipo_penal__grupo_legislação_específica_grupo_legislação_específica_outros_crimes_contra_o_meio_ambiente_lei_9605_de_12021998_masculino': 'meio_ambiente_masc',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_com_informação_sobre_tipificação_criminal_masculino': 'ppl_com_info_masc',
    '514_quantidade_de_incidências_por_tipo_penal_número_de_pessoas_privadas_de_liberdade_sem_informação_sobre_tipificação_criminal_masculino': 'ppl_sem_info_masc',
    '514_quantidade_de_incidências_por_tipo_penal_masculino': 'incidencias_total_masc'},inplace=True)

df_tremembe_masc_tipo_penal

serie_masc_tipo_penal = df_tremembe_masc_tipo_penal.iloc[0]
serie_masc_tipo_penal = serie_masc_tipo_penal[serie_masc_tipo_penal > 0]

plt.figure(figsize=(15, 10))
plt.barh(serie_masc_tipo_penal.index, serie_masc_tipo_penal.values)
plt.xticks(rotation=90)
plt.title('Incidências por tipo penal – Penit. "Dr. José Augusto César Salgado" de Tremembé + APP')
plt.ylabel("Tipo Penal")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Tempo de pena | Penitenciária Dr. José Augusto César Salgado de Tremembé

df_tremembe_masc_pena = df_tremembe_masc.filter(regex='512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas', axis=1)
df_tremembe_masc_pena = df_tremembe_masc_pena.drop(columns=[
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__como_é_registrada_essa_informação',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__número_de_pessoas_sem_informação_masculino'
])

df_tremembe_masc_pena

df_tremembe_masc_pena.rename(columns={
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__até_6_meses_inclusive_masculino':'pena_ate_6_meses_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_6_meses_até_1_ano_inclusive_masculino':'pena_6m_a_1a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_1_ano_até_2_anos_inclusive_masculino':'pena_1a_a_2a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_2_até_4_anos_inclusive_masculino':'pena_2a_a_4a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_4_até_8_anos_inclusive_masculino':'pena_4a_a_8a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_8_até_15_anos_inclusive_masculino':'pena_8a_a_15a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_15_até_20_anos_inclusive_masculino':'pena_15a_a_20a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_20_até_30_anos_inclusive_masculino':'pena_20a_a_30a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_30_até_50_anos_inclusive_masculino':'pena_30a_a_50a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_50_até_100_anos_inclusive_masculino':'pena_50a_a_100a_masc',
    '512_quantidade_de_pessoas_privadas_de_liberdade_por_tempo_total_de_penas_presosas_condenadosas_e__mais_de_100_anos_masculino':'pena_mais_100a_masc'
}, inplace=True)

df_tremembe_masc_pena.astype(int)

serie_masc_pena = df_tremembe_masc_pena.iloc[0]
serie_masc_pena = serie_masc_pena[serie_masc_pena > 0]

plt.figure(figsize=(16, 8))
plt.barh(serie_masc_pena.index, serie_masc_pena.values)
plt.xticks(rotation=90)
plt.title('Tempo de pena – Penit. "Dr. José Augusto César Salgado" de Tremembé + APP')
plt.ylabel("Tempo de pena")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Faixa etária | Penitenciária Dr. José Augusto César Salgado de Tremembé

df_tremembe_masc_idade = df_tremembe_masc.filter(regex='51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária', axis=1)

drop_total_masc_idade = df_tremembe_masc_idade.filter(regex='total', axis=1).columns.tolist()

df_tremembe_masc_idade = df_tremembe_masc_idade.drop(columns=[
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_não_informado_masculino'
])

df_tremembe_masc_idade = df_tremembe_masc_idade.drop(columns=drop_total_masc_idade, axis=1)

df_tremembe_masc_idade = df_tremembe_masc_idade.astype(int)

df_tremembe_masc_idade.rename(columns={
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_18_a_24_anos_masculino': '18_a_24_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_25_a_29_anos_masculino':'25_a_29_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_30_a_34_anos_masculino':'30_a_34_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_35_a_45_anos_masculino':'35_a_45_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_46_a_60_anos_masculino':'46_a_60_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_61_a_70_anos_masculino':'61_a_70_anos_masc',
    '51_quantidade_de_pessoas_privadas_de_liberdade_por_faixa_etária_mais_de_70_anos_masculino':'mais_de_70_anos_masc'
}, inplace=True)

serie_masc_idade = df_tremembe_masc_idade.iloc[0]
serie_masc_idade = serie_masc_idade[serie_masc_idade > 0]

plt.figure(figsize=(16, 8))
plt.barh(serie_masc_idade.index, serie_masc_idade.values)
plt.xticks(rotation=90)
plt.title('Tempo de pena – Penit. "Dr. José Augusto César Salgado" de Tremembé + APP')
plt.ylabel("Faixa etária")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Cor, raça e etnia | Penitenciária Dr. José Augusto César Salgado de Tremembé

df_tremembe_masc_raça = df_tremembe_masc.filter(regex='52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia', axis=1)

drop_total_masc_raça = df_tremembe_masc_raça.filter(regex='total', axis=1).columns.tolist()

df_tremembe_masc_raça = df_tremembe_masc_raça.drop(columns=[
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_não_informado_masculino',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_povo_indígena',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_idioma',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_se_houver_indígenas_destacar_povo_indígena_ao_qual_pertence_e_respectivo_idioma_campos_abertos_quantidade'
])

df_tremembe_masc_raça = df_tremembe_masc_raça.drop(columns=drop_total_masc_raça, axis=1)

df_tremembe_masc_raça.columns.tolist()

df_tremembe_masc_raça = df_tremembe_masc_raça.astype(int)

df_tremembe_masc_raça.rename(columns={
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_branca_masculino': 'branca_masculino',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_preta_masculino':'preta_masculino',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_parda_masculino':'parda_masculino',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_amarela_masculino':'amarela_masculino',
    '52_quantidade_de_pessoas_privadas_de_liberdade_por_cor_de_peleraçaetnia_indígena_masculino':'indígena_masculino'
}, inplace=True)

serie_masc_raça = df_tremembe_masc_raça.iloc[0]

plt.figure(figsize=(12, 6))
plt.barh(serie_masc_raça.index, serie_masc_raça.values)
plt.xticks(rotation=90)
plt.title('Tempo de pena – Penit. "Dr. José Augusto César Salgado" de Tremembé + APP')
plt.ylabel("Pele, raça e etnia")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()

# Escolaridade | Penitenciária Dr. José Augusto César Salgado de Tremembé

df_tremembe_masc_esc = df_tremembe_masc.filter(regex='56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução', axis=1)

drop_total_masc_esc = df_tremembe_masc_esc.filter(regex='total', axis=1).columns.tolist()

df_tremembe_masc_esc = df_tremembe_masc_esc.drop(columns=drop_total_masc_esc, axis=1)

df_tremembe_masc_esc = df_tremembe_masc_esc.drop(columns=[
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_o_estabelecimento_tem_condições_de_obter_estas_informações_em_seus_registros',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_não_informado_masculino',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_masculino'
])

df_tremembe_masc_esc.columns.tolist()

df_tremembe_masc_esc = df_tremembe_masc_esc.astype(int)

df_tremembe_masc_esc.rename(columns={
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_analfabeto_masculino':'analfabeto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_alfabetizado_sem_cursos_regulares_masculino':'alfabetizado_sem_cursos_regulares_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_incompleto_masculino':'fundamental_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_fundamental_completo_masculino':'fundamental_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_incompleto_masculino':'médio_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_médio_completo_masculino':'médio_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_incompleto_masculino':'superior_incompleto_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_superior_completo_masculino':'superior_completo_masc',
    '56_quantidade_de_pessoas_privadas_de_liberdade_por_grau_de_instrução_ensino_acima_de_superior_completo_masculino':'acima_superior_completo_masc'
}, inplace=True)

serie_masc_esc = df_tremembe_masc_esc.iloc[0]
serie_masc_esc = serie_masc_esc[serie_masc_esc > 0]

plt.figure(figsize=(12, 6))
plt.barh(serie_masc_esc.index, serie_masc_esc.values)
plt.xticks(rotation=90)
plt.title('Tempo de pena – Penit. "Dr. José Augusto César Salgado" de Tremembé + APP')
plt.ylabel("Grau de escolaridade")
plt.xlabel("Quantidade")
plt.tight_layout()
plt.show()
