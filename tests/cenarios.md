# Casos de Teste - Prova de Conceito (PoC)

Esta documentação espelha os testes descritos no artigo, demonstrando a validação da regra de explicabilidade.

### Cenário 1: Primeiro Acesso
*   **Condição inicial:** O histórico do usuário no banco de dados para a disciplina selecionada é nulo.
*   **Ação:** Usuário seleciona Iniciar Trilha.
*   **Comportamento do Sistema:** Busca padrão para o ID do Nível 1.

### Cenário 2: Erro Isolado (Gatilho da Explicabilidade)
*   **Condição inicial:** Usuário está respondendo a uma questão de Nível 2.
*   **Ação:** Submissão de alternativa incorreta.
*   **Comportamento do Sistema:** 
    1. Registra falha no histórico.
    2. Modifica a flag de estado para forçar a regressão de nível.
    3. Carrega a próxima questão (Nível 1) injetando a string dinâmica na interface: *"Você errou a questão anterior de [Disciplina] (nível [X]). Por isso, para fixação do conceito, a próxima questão selecionada é de nível [X-1]"*.

### Cenário 3: Acertos Contínuos (Borda Superior)
*   **Condição inicial:** Usuário acertou 3 questões seguidas.
*   **Ação:** Responde corretamente a próxima questão do Nível 2 (máximo).
*   **Comportamento do Sistema:** Mantém a progressão presa no ID do Nível 2, não avançando para níveis inexistentes.

### Cenário 4: Erros Sucessivos (Borda Inferior)
*   **Condição inicial:** Usuário acumula 3 falhas seguidas no Nível 1.
*   **Ação:** Responde incorretamente à questão.
*   **Comportamento do Sistema:** Bloqueia a regressão e gera o alerta visual (modal) sugerindo a revisão teórica antes da próxima tentativa.
