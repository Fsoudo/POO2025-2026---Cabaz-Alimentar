# POO2025-2026---Cabaz-Alimentar

**Documento Original:** `TP_PO2_2025_2026_grelhaAlimentos-2026-04-08.pdf`
**Unidade Curricular:** Programação Orientada a Objetos 2 (POO.2)
**Objetivo:** Construir uma aplicação Java com JavaFX que simula a compra de um Cabaz Alimentar Sustentável, focado nos Objetivos de Desenvolvimento Sustentável (ODS) da ONU. A arquitetura tem de seguir estritamente o modelo de **MVC (Model-View-Controller)**.

---

## 🏗️ Arquitetura e Estrutura de Classes (Essencial)

- **`FoodItem`**: Classe abstrata base. Atributos: `id`, `name`, `base_price`, `category` (tipo Enum `FoodGroup` - Proteínas, Hidratos, Vegetais, Frutas) e `kcal`.
- **Hierarquia (Polimorfismo)**:
  - **`PackagedFood` (Embalados):** Vendidos à unidade. Atributo extra de material de embalagem (Plástico, Papel, Vidro).
  - **`BulkFood` (A granel):** Vendidos ao peso (em gramas). Requerem sobrescrever o método `getPrice()` para adequar o cálculo escalar do peso ao preço.

---

## 🎯 Requisitos Funcionais Obrigatórios

1. **Leitura de CSV:** Ler o ficheiro `inventory.csv` usando **apenas classes nativas** do JDK (`java.io`, `java.nio`, variáveis de strings da linguagem). Linhas com erros devem ser ignoradas. No fim da leitura, exibir caixa de diálogo com as linhas problemáticas.
2. **Interface Gráfica (Grid):**
   - Cada alimento deve ter um "cartão/botão" (`Tile`/`Botão`/`Panel`) na UI com o nome e preço.
   - Comidas a granel devem ser visualmente distintas das embaladas na interface.
3. **Interação Polimórfica (Dashboard e Cabaz):**
   - **Click num Embalado:** Adicionado diretamente ao cabaz.
   - **Click num A granel:** Abre uma `TextInputDialog` perguntando: *"Quantas gramas deseja adicionar?"*.
   - **Dashboard (Painel Lateral):** Deve atualizar automaticamente em tempo real exibindo: Custo Total, Calorias e a Lista dos Nomes (Padrão de Observador).
4. **Exportação de Recibo:** Botão "Finalizar Compra". Gera um ficheiro `receipt_[AAAAMMDD].txt` contendo a lista e avisa no final se alcançou um dos objetivos ODS (nomeadamente a meta de Saúde).

---

## 🚀 Requisitos Não-Essenciais (Valorização)

- **Emblemas ODS Dinâmicos:** Ícones (ODS 2, 3 e 12) começam opacos (cinzento) e ativam com objetivos concretos (ex: >400g verdes, 50% não embalados/sem plástico, >4 grupos nutricionais integrados).
- **Filtros e Ordenação:** Mostrar por tipo de categoria. Ordenar (`sort`) por preço ou calorias.
- **Botão Cabaz Inteligente:** Um gerador automático de itens que preenche as condições mínimas de dois emblemas ODS por um custo abaixo de 20€.
- **Undo / Redo:** Atalhos (`CTRL+Z` / `CTRL+Y`) para reverter o que foi adicionado.
- **Som e Animações:** Toques de notificação sonora ao bater as metas dos emblemas ODS e transições visuais dinâmicas em JavaFX (Fade, Scale).
- **Replay Histórico:** Recriar a encomenda a partir da importação de um ficheiro `receipt.txt` antigo em câmara lenta, passo a passo, construindo visualmente.

---

## ⚠️ Regras Críticas e Penalizações (RPB)

> [!CAUTION]
> O desrespeito destas regras pode ser severamente penalizado ou anular a nota do projeto.

1. **Sem Regras na View (-5 valores):** O Controller/View não deve fazer qualquer cálculo lógico de negócios (ex: `if (peso > 400)`). Deve apenas notificar o `Model`. O Model é quem notifica a View do valor alterado.
2. **`instanceof` é Proibido:** É estritamente proibido o seu uso, assim como `getClass()` e mecanismos de "casting" manual. A utilização dos valores monetários é orientada a Polimorfismo, executando algo semelhante ao varrimento na lista de interfaces ou chamando o `item.getPrice()`.
3. **Código Total em Inglês:** Variáveis, métodos e classes inteiramente em Inglês. Só a IU do lado do utilizador real (front-end estético) pode ser em português.
4. **Clean Code (Regras de Estilo):**
   - Máximo de 20 linhas ("pontos e vírgulas") por método.
   - O uso do `this.` associado aos atributos é obrigatório.
   - Constantes obrigam a palavra `final`.
   - **Javadoc** obrigatório sobre cada método. Proibido estender comentários simples dentro dos métodos.

---

## 🤖 Uso de Inteligência Artificial e Entrega

> [!WARNING]
> Ferramentas de IA (ChatGPT, Gemini, etc.) podem auxiliar a gerar código, contudo o limite do controlo é apertado.

- **Ficheiro de Relatório de IA:** Obrigatória a submissão de um `relatorio_ia.txt` onde apresentas a explicação das ferramentas, excertos e lógicas que foram adotadas através de IA.
- **Defesa Oral Eliminatória:** Para validar que a IA não fez o pensamento estrutural, precisas de saber justificar de onde veio o teu código. Excertos gerados ou descarregados dos quais não saibas a explicação ditarão **0 valores** para a nota final.

**Entrega:**
- Prazo: **25 de Maio de 2026** no Moodle.
- ZIP Formato: `Numero-PrimeiroUltimo-Numero-PrimeiroUltimo-TP-PO2-2025-2026.zip`
- Exportação: A pasta global exclui a pasta interna chamada `target`.
