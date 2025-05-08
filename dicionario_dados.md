
# Dicionário de dados: European Soccer Database

**Descrição:**  
O European Soccer Database é um conjunto de dados para análise e machine learning de partidas de futebol profissional europeu. Contém mais de 25.000 partidas, mais de 10.000 jogadores, atributos extraídos da série de videogames FIFA da EA Sports, dados de odds de apostas, eventos detalhados de partidas e formações de times, abrangendo 11 países europeus e temporadas de 2008 a 2016.

---

## Table: country  
**Descrição:** Lista de países participantes.

| Coluna | Tipo   | Descrição                    |
|--------|--------|------------------------------|
| id     | long   | Identificador único do país  |
| name   | string | Nome do país                 |

---

## Table: league  
**Descrição:** Ligas correspondentes a cada país.

| Coluna     | Tipo   | Descrição                                  |
|------------|--------|--------------------------------------------|
| id         | long   | Identificador único da liga                |
| name       | string | Nome da liga                               |
| country_id | long   | Referência ao `country.id`                 |

---

## Table: player  
**Descrição:** Informações básicas dos jogadores.

| Coluna              | Tipo   | Descrição                                   |
|---------------------|--------|---------------------------------------------|
| id                  | long   | Identificador único do registro             |
| height              | long   | Altura do jogador (cm)                     |
| weight              | long   | Peso do jogador (lbs)                      |
| birthday            | string | Data de nascimento                          |
| player_name         | string | Nome completo do jogador                    |
| player_api_id       | long   | ID do jogador na API de partidas            |
| player_fifa_api_id  | long   | ID do jogador na base FIFA                  |

---

## Table: player_attributes  
**Descrição:** Atributos semanais dos jogadores extraídos do FIFA.

| Coluna                  | Tipo   | Descrição                                |
|-------------------------|--------|------------------------------------------|
| id                      | long   | Identificador único do registro          |
| date                    | string | Data de atualização dos atributos        |
| curve                   | long   | Curvatura em cobranças de falta         |
| vision                  | long   | Visão de jogo                            |
| agility                 | long   | Agilidade                                |
| balance                 | long   | Equilíbrio                               |
| jumping                 | long   | Impulso                                  |
| marking                 | long   | Marcação                                 |
| stamina                 | long   | Resistência física                       |
| volleys                 | long   | Finalização de voleio                    |
| crossing                | long   | Cruzamentos                              |
| strength                | long   | Força                                    |
| dribbling               | long   | Drible                                   |
| finishing               | long   | Finalização                              |
| gk_diving               | long   | Mergulho (goleiro)                       |
| penalties               | long   | Pênaltis                                 |
| potential               | long   | Potencial futuro                         |
| reactions               | long   | Reações                                 |
| aggression              | long   | Agressividade                            |
| gk_kicking              | long   | Chute do goleiro                         |
| long_shots              | long   | Chutes de longa distância                |
| shot_power              | long   | Força de chute                           |
| gk_handling             | long   | Defesa de goleiro                        |
| gk_reflexes             | long   | Reflexos do goleiro                      |
| positioning             | long   | Posicionamento                           |
| acceleration            | long   | Aceleração                               |
| ball_control            | long   | Controle de bola                         |
| long_passing            | long   | Passes longos                            |
| sprint_speed            | long   | Velocidade de corrida                    |
| interceptions           | long   | Interceptações                           |
| short_passing           | long   | Passes curtos                            |
| gk_positioning          | long   | Posicionamento do goleiro                |
| overall_rating          | long   | Avaliação geral                          |
| preferred_foot          | string | Pé preferido (left/right)                |
| sliding_tackle          | long   | Carrinho                                  |
| standing_tackle         | long   | Desarme em pé                            |
| heading_accuracy        | long   | Precisão de cabeça                       |
| free_kick_accuracy      | long   | Precisão em faltas                      |
| player_api_id           | long   | Referência ao `player.player_api_id`      |
| player_fifa_api_id      | long   | Referência ao `player.player_fifa_api_id` |
| attacking_work_rate     | string | Intensidade de trabalho ofensivo         |
| defensive_work_rate     | string | Intensidade de trabalho defensivo        |

---

## Table: team  
**Descrição:** Informação básica dos times.

| Coluna            | Tipo   | Descrição                               |
|-------------------|--------|-----------------------------------------|
| id                | long   | Identificador único do registro         |
| team_api_id       | long   | ID do time na API de partidas           |
| team_long_name    | string | Nome completo do time                   |
| team_short_name   | string | Sigla/nome curto do time                |
| team_fifa_api_id  | long   | ID do time na base FIFA                 |

---

## Table: team_attributes  
**Descrição:** Atributos dos times extraídos do FIFA.

| Coluna                         | Tipo   | Descrição                                    |
|--------------------------------|--------|----------------------------------------------|
| id                             | long   | Identificador único do registro              |
| date                           | string | Data de atualização dos atributos            |
| team_api_id                    | long   | Referência ao `team.team_api_id`              |
| defencePressure                | long   | Pressão defensiva                            |
| buildUpPlaySpeed               | long   | Velocidade de construção de jogo             |
| defenceTeamWidth               | long   | Largura defensiva                            |
| defenceAggression              | long   | Agressividade defensiva                      |
| buildUpPlayPassing             | long   | Qualidade de passe na construção de jogo     |
| buildUpPlayDribbling           | long   | Qualidade de drible na construção de jogo    |
| chanceCreationPassing          | long   | Criação de chance por passe                  |
| chanceCreationCrossing         | long   | Criação de chance por cruzamento             |
| chanceCreationShooting         | long   | Criação de chance por finalização            |
| chanceCreationPositioningClass | string | Classe de posicionamento ofensivo            |
| defencePressureClass           | string | Classe de pressão defensiva                  |
| buildUpPlaySpeedClass          | string | Classe de velocidade de construção de jogo   |
| defenceTeamWidthClass          | string | Classe de largura defensiva                  |
| defenceAggressionClass         | string | Classe de agressividade defensiva            |
| buildUpPlayPassingClass        | string | Classe de passe na construção de jogo        |
| defenceDefenderLineClass       | string | Classe de linha defensiva                    |
| buildUpPlayDribblingClass      | string | Classe de drible na construção de jogo       |
| chanceCreationPassingClass     | string | Classe de criação de chance por passe        |
| buildUpPlayPositioningClass    | string | Classe de posicionamento na construção de jogo |
| chanceCreationCrossingClass    | string | Classe de criação de chance por cruzamento   |
| chanceCreationShootingClass    | string | Classe de criação de chance por finalização  |

---

## Table: Match  
**Descrição:** Dados de partidas, incluindo resultados, estatísticas de jogo e odds de apostas.

| Coluna           | Tipo   | Descrição                                                |
|------------------|--------|----------------------------------------------------------|
| id               | long   | Identificador único da partida                           |
| date             | string | Data e horário da partida                                |
| country_id       | long   | Referência ao `country.id`                               |
| league_id        | long   | Referência ao `league.id`                                |
| season           | string | Temporada (ex: 2008/2009)                                |
| stage            | long   | Rodada da temporada                                      |
| home_team_goal   | long   | Gols do time da casa                                     |
| away_team_goal   | long   | Gols do time visitante                                   |
| B365H, B365D, B365A | double | Odds pré-jogo Bet365 (casa, empate, visitante)         |
| ...              | ...    | Outros campos de odds seguem padrões similares           |
| shoton, shotoff  | string | IDs de jogadores que chutaram (on target/off target)     |
| corner, cross    | string | IDs de jogadores envolvidos em escanteios e cruzamentos  |
| foulcommit       | string | IDs de jogadores que cometeram faltas                    |
| possession       | string | Percentual de posse de bola                              |
| home_player_1...Y11 | long | IDs e coordenadas X,Y da formação de jogadores          |
| card, goal       | string | Eventos de cartões e gols                               |

> **Nota:** As colunas de odds de apostas incluem múltiplos provedores (Bet365, Pinnacle, Betfair, etc.) e cada uma possui colunas para casa (H), empate (D) e visitante (A). Além disso, há colunas detalhadas de eventos de partida e formação de equipe.
