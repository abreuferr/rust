# Convenções deste repositório

- Cada subpasta (`cli/`, `web/`, `bibliotecas/`, `automacao/`, `experimentos/`,
  `aprendizado/`) contém crates Cargo independentes. Não é um workspace: não
  existe `Cargo.toml` na raiz.
- Edition padrão dos crates: 2024.
- `Cargo.lock`: versionar em crates de aplicação (`cli/`, `web/`,
  `automacao/`, `experimentos/`, `aprendizado/`). Não versionar em
  `bibliotecas/` (convenção padrão do ecossistema Rust para crates de
  biblioteca).
- Novo projeto: `cd` na categoria certa e `cargo new nome-do-projeto`.

## Objetivo
Concluir a tarefa atual utilizando a abordagem mínima suficiente.
Evitar complexidade excessiva (*overengineering*).
O planejamento pode ser denso e detalhado; a execução deve ser leve e ágil.
Se não for possível provar que um design é necessário, não o implemente.
Se não for possível provar que um teste é necessário, não o adicione.

## Fluxo de Trabalho
1. Entenda o requisito antes de tocar no código. Não altere o código para depois tentar adivinhar a intenção.
2. A fase de planejamento pode utilizar um nível mais elevado de raciocínio. A fase de execução deve adotar, por padrão, um nível de raciocínio médio-baixo ou um modelo mais leve.
3. Não utilize o nível máximo de raciocínio durante toda a sessão.
4. Não inicie múltiplos agentes por padrão. Conclua a tarefa de forma linear (thread única) primeiro e, então, decida se a divisão do trabalho seria benéfica.
5. Habilite apenas as habilidades (*skills*) realmente necessárias para a tarefa. Não instale habilidades que exijam processamento pesado.
6. Elabore um plano mínimo antes da execução. O plano deve incluir:
   - Objetivo
   - O que não é objetivo (não escopo)
   - Critérios de aceitação
   - O que permanecerá inalterado

## Modos de Falha
1. Falha em compreender a verdadeira intenção; correção apenas superficial.
2. Poderia ter realizado uma correção limpa na causa raiz, mas acumulou *patches*, camadas de compatibilidade, implementações duplicadas e cópias.
3. Design excessivamente complexo para casos raros, tornando a manutenção cotidiana custosa.
4. Premissa incorreta. Nenhum raciocínio, por mais correto que seja, conserta um ponto de partida errado.
5. Deveria ter lido o código diretamente, mas recorreu a buscas ou suposições.
6. Usou a "adição de testes" como pretexto para expandir o escopo, adicionar abstrações ou aparentar minuciosidade.

## Limites de Ação
1. Antes de começar, reafirme:
   - O que o usuário realmente deseja
   - O escopo desta tarefa
   - O que está explicitamente fora do escopo
   - A definição de conclusão (*Definition of Done*)
2. Qualquer operação irreversível exige confirmação do usuário antes de ser executada. 
3. Estas ações NÃO são irreversíveis (podem ser executadas sem pedir permissão):
   - Git revert, restore, troca de branch
   - Mover arquivos para um diretório de backup no repositório
   - Executar testes, visualizar diffs, gerar planos, análises de apenas leitura
4. Ao perceber que está fazendo algo da lista abaixo, pare e mude para um plano mais simples:
   - Adicionar abstrações/frameworks/camadas de configuração que a tarefa não exige
   - Projetar antecipadamente para um possível uso futuro
   - Acumular restrições adicionais para satisfazer restrições existentes
   - Alterar muitos arquivos não relacionados
   - Criar uma segunda implementação para manter a lógica antiga ativa
   - Usar a adição de testes como justificativa para continuar desenvolvendo

## Testes
Os testes servem para validar a alteração atual. Nada além disso.

1. Dê preferência à execução de testes existentes relacionados à alteração.
2. Se os testes existentes comprovarem que a alteração funciona, não adicione novos testes.
3. Novos testes são permitidos apenas quando:
   - A alteração modificar um comportamento que os testes existentes não cobrem
   - O usuário solicitar explicitamente testes
4. Novos testes devem cobrir, no máximo: 1 caminho principal + 1 caminho de falha crítica.
5. Não amplie o escopo dos testes em busca de cobertura completa.
6. Não adicione testes retroativamente a módulos não relacionados.
7. Não introduza novos frameworks ou infraestruturas de teste.
8. Não escreva matrizes de snapshot, grades parametrizadas ou suítes de teste ponta a ponta (e2e).
9. Não teste limites (casos de borda) que não foram solicitados pelo requisito atual.
10. Não permita que testes passando (verdes) justifiquem mais abstração.

Antes de adicionar qualquer teste, responda:
- Qual requisito aceito este teste verifica?
- Sem ele, os testes existentes deixariam passar essa regressão?
- Ele é mais simples do que a implementação?

Se o código do teste for mais extenso ou complexo do que a implementação, considere-o como excesso de engenharia (*overengineering*). 

## Alocação de Modelo
- Esclarecimento de requisitos e revisão do plano: modelo mais robusto
- Escrita/alteração de código e execução de testes: modelo de menor intensidade ou execução mais leve
- Se o modelo de execução começar a acumular complexidade arquitetural ou expandir o escopo: pare, reescreva um plano minimalista

## Checklist de Pré-Conclusão
- Intenção e critérios de aceitação reafirmados
- A solução representa a abordagem mínima, não a máxima
- Itens fora do escopo (non-goals) estão sinalizados
- Leitura direta do código relevante em vez de suposições
- Alteração apenas do conjunto mínimo de arquivos necessário
- Execução de testes existentes relacionados
- Ausência de testes para cenários não solicitados
- Novos testes apenas consolidam o comportamento atual; quantidade reduzida
- Testes não introduziram novas dependências ou estruturas de diretórios
- Diff reduzido, sem arquivos extras ou código de depuração residual
- Ausência de trabalho adicional apenas para parecer completo
