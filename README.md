# fabio_souza
Engenharia de software 
 
Projeto  Sistema da clinica
Bicho do Mato
Autor Fabio Junior de Souza
---
# 1. Descrição do sistema 

1. Uma clínica veterinária atende apenas os animais: gatos e cachorros. 
2. Os clientes devem fazer um cadastro de si e dos animais. 
3. Os clientes devem informar as condições nas quais os animais chegam. 
4. Os clientes devem informar o tipo de ração que o animal come. 
5. O cliente deve informar hábitos do animal. 
6. Para cada animal é possível que mais de um veterinário o atenda. 
7. Os animais podem chegar e serem atendidos de acordo com uma agenda do dia. 
8. Cada animal atendido receberá uma ficha e um prontuário. 
9. Outros donos podem querer marcar horários de atendimento futuro. 
10. O atendimento gera uma receita para o animal. 
11. Quando um cliente chega na clínica veterinária ele é atendido por um atendente. 
12. O atendente deve verificar se existe agenda disponível com um veterinário. 
13. O atendente deve colocar o cliente e seu animal na fila de espera, se for o caso. 
14. O atendente deve levar o cliente e o animal até o veterinário. 
15. O veterinário deve realizar uma entrevista com o dono do animal. 
16. O resultado da entrevista deve ir para um formulário. 
17. O veterinário deverá examinar o animal e anotar em prontuário(ficha) suas observações. 
18. Dependendo da situação do animal este receberá uma receita.
20. área de login
21. cadastro de Funcionários
22. cadastro de clientes,
23. cadastro de fornecedores
24. cadastro do pet
25. sintomas do pet
26. área do veterinário 
27. Prontuário do veterinário 
28. medicamentos prescritos 
29. cadastro de medicamentos e produtos 
31. formas de pagamento(boleto
32. Atendimento 07:00 as 18:00 
33. Fidelização de Clientes 
34. Vale refeição para pet
35. Manicure para pets



---
# 2. Diagrama do banco de dados

``` mermaid 
erDiagram
    CLIENTE {
        int id_cliente PK
        string nome
        string endereco
        string telefone
        string email
    }

    ANIMAL {
        int id_animal PK
        string nome
        string especie
        string raca
        string habitos
        string tipo_racao
        string condicoes_entrada
        int id_cliente FK
    }

    VETERINARIO {
        int id_veterinario PK
        string nome
        string especialidade
    }

    ATENDENTE {
        int id_atendente PK
        string nome
    }

    ATENDIMENTO {
        int id_atendimento PK
        date data
        string horario
        int id_cliente FK
        int id_animal FK
        int id_atendente FK
    }

    RECEITA {
        int id_receita PK
        string descricao
        int id_animal FK
        int id_veterinario FK
        int id_atendimento FK
    }

    PRONTUARIO {
        int id_prontuario PK
        string observacoes
        int id_animal FK
        int id_veterinario FK
        int id_atendimento FK
    }

    FUNCIONARIO {
        int id_funcionario PK
        string nome
        string cargo
    }

    FORNECEDOR {
        int id_fornecedor PK
        string nome
        string produto
        string contato
    }

    MEDICAMENTO {
        int id_medicamento PK
        string nome
        string descricao
        float preco
    }

    CLIENTE ||--o{ ANIMAL: "possui"
    ANIMAL }|--|| VETERINARIO: "atendido por"
    ANIMAL }|--o{ ATENDIMENTO: "participa"
    VETERINARIO }|--o{ ATENDIMENTO: "realiza"
    ATENDENTE }|--o{ ATENDIMENTO: "efetua"
    ATENDIMENTO ||--o{ RECEITA: "gera"
    ATENDIMENTO ||--o{ PRONTUARIO: "cria"
    PRONTUARIO }|--|| ANIMAL: "referencia"
    RECEITA }|--|| MEDICAMENTO: "prescreve"
    FUNCIONARIO ||--o{ VETERINARIO: "pode ser"
    FUNCIONARIO ||--o{ ATENDENTE: "pode ser"
    FORNECEDOR ||--o{ MEDICAMENTO: "fornece"




```

![Diagrama](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/diagrama1.png?raw=true)
---
# 3. Diagrama de casos de uso

![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Diagrama%20sem%20nome.png)
---

![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/diagrama%20casos%20de%20uso.png)
---
# 4. Principais telas do sistemas 

![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-13%20230150.png)
![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-13%20230228.png)
![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-13%20230239.png)
![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-13%20230250.png)
![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-13%20230302.png)
![](https://github.com/FabioJrdeSouza/fabio_souza/blob/main/imagens/Captura%20de%20tela%202024-08-14%20215819.png)
---
# 5. Arquitetura do sistemas 


```mermaid
graph TD
    subgraph "Sistema"
        A1[Área de Login]
        B1[Cadastro de Funcionários]
        B2[Cadastro de Clientes]
        B3[Cadastro de Fornecedores]
        B4[Cadastro de Pets]
        B5[Sintomas do Pet]
        B6[Cadastro de Medicamentos e Produtos]
        B7[Área do Veterinário]
        B8[Prontuário do Veterinário]
        B9[Medicamentos Prescritos]
        C1[Formas de Pagamento]
        C2[Fidelização de Clientes]
        C3[Vale Refeição para Pet]
        C4[Manicure para Pets]
        D1[Atendimento]
        D2[Agendamento]
        D3[Fila de Espera]
        D4[Entrevista com o Dono]
        D5[Exame do Animal]
        D6[Receita]

        A1 --> B1
        A1 --> B2
        A1 --> B3
        A1 --> B4
        A1 --> C1
        A1 --> C2
        A1 --> C3
        A1 --> C4

        B2 --> B4
        B4 --> B5
        B4 --> B7

        B7 --> D4
        B7 --> D5
        B7 --> B8
        B7 --> B9

        B8 --> D6

        D1 --> D2
        D1 --> D3
        D1 --> D4
        D1 --> D5

        D2 --> B1
        D2 --> B2
        D2 --> B4
        D2 --> C1
        D2 --> C2

        D3 --> B2
        D3 --> B4

        D4 --> B5
        D4 --> B7

        D5 --> B8
        D5 --> B9

        C1 --> B4
        C1 --> D6

        C2 --> B2
        C2 --> D6

        C3 --> B4

        C4 --> B4
    end
```
```mermaid
graph TD
    A[Área de Login] --> B[Cadastro de Funcionários]
    A --> C[Cadastro de Clientes]
    A --> D[Cadastro de Fornecedores]
    A --> E[Cadastro de Medicamentos e Produtos]

    C --> F[Cadastro do Pet]
    F --> G[Sintomas do Pet]
    F --> H[Prontuário do Veterinário]
    H --> I[Medicamentos Prescritos]
    I --> J[Área do Veterinário]
    
    J --> K[Formulário de Entrevista]
    J --> L[Exame e Observações]

    L --> M[Receita]
    M --> N[Vale Refeição para Pet]
    
    N --> O[Fidelização de Clientes]
    O --> P[Manicure para Pets]

    C --> Q[Atendimento]
    Q --> R[Fila de Espera]
    R --> S[Agendamento]
    S --> T[Agenda de Veterinários]

    T --> U[Receita do Atendimento]
    U --> V[Formas de Pagamento]

    V --> W[Relatórios]
    W --> X[Cadastro de Medicamentos e Produtos]
```    

![]()