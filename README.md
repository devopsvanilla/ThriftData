
# ThriftData

## Visão Geral
![Logo](https://github.com/user-attachments/assets/a523f69b-fcd8-4947-9825-a0f406b4b72e)

ThriftData é uma stack modular para coleta, análise e visualização de dados operacionais e financeiros em ambientes multi-cloud e on-prem. Foco em FinOps, observabilidade e governança, integrando automação, machine learning e consulta natural com LLMs.

Esta arquitetura foi idealizada para prover uma solução robusta, escalável e flexível de coleta, normalização, armazenamento, análise e visualização de dados em ambientes híbridos multi-cloud e on-premises, com suporte integrado a Machine Learning, FinOps, segurança e consultas naturais (NLQ). A escolha da stack reflete as melhores práticas e ferramentas open source consolidadas no mercado, garantindo interoperabilidade, controle, custo-efetividade e inovação contínua.

```mermaid
graph TD
    A[Fontes de Informação]
    B[Coleta Multi-cloud e On-Prem]
    C[Normalização]
    D[Armazenamento]
    E[Machine Learning]
    F[Custos Multiambiente]
    G[Visualização]
    H[Consulta Natural]
    I[Painéis Administrativos]
    J[Segurança]

    A --> B
    B --> C
    C --> D
    D --> E
    D --> F
    D --> G
    D --> H
    E --> G
    F --> G
    H --> G
    I --> C
    I --> D
    I --> E
    I --> F
    I --> G
    I --> H
    C --> J
    D --> J
    E --> J
    F --> J
    G --> J
```

## Justificativas para a Stack

### Fontes de Informação

Diversidade e abrangência são essenciais para capturar dados relevantes:
- Sistemas administrativos e ERP fornecem informações críticas de negócio.
- Logs, métricas e dados financeiros capturam o estado operacional e econômico.
- Métricas de workloads (Kubernetes, VMs, containers) refletem a utilização real dos recursos.
- Dados de orquestração e pipelines CI/CD trazem visibilidade sobre automação e entrega contínua.
- Logs de segurança e compliance asseguram governança e conformidade.

### Coleta Multi-cloud e On-Premises

- **OpenTelemetry:** padrão aberto, facilita coleta unificada e interoperável de métricas, logs e traces.
- **Steampipe e CloudQuery:** acessam APIs de diversas fontes para dados adicionais como billing e inventário.
- **Cloud Custodian:** permite automação e políticas de governança em múltiplos ambientes.

### Normalização e Orquestração

- **Apache Airflow e n8n:** orquestração flexível dos processos ETL, integração com múltiplas fontes e ferramentas.
- **dbt:** foco em transformação modular, versionada e testada, usando modelos de dados alinhados com negócios.

### Armazenamento

- Uso combinado de Data Lakes (escaláveis e econômicos), Graph DBs (para relacionamentos complexos) e bancos relacionais tradicionais, garantindo flexibilidade e desempenho.

### Machine Learning

- **Kubeflow e MLFlow:** suporte completo para ciclos de vida de modelos ML, desde treino até deployment e monitoramento.
- Permite identificar anomalias, prever tendências e automatizar decisões.

### FinOps e Monitoramento de Custos

- Ferramentas como **Kubecost** e dashboards customizados permitem controle detalhado de custos em Kubernetes e multi-cloud, viabilizando otimização financeira e tomada de decisão baseada em dados.

### Visualização e NLQ

- Plataformas de visualização como **Superset**, **Metabase** e **Grafana** oferecem dashboards ricos e alertas configuráveis.
- **LangChain e LlamaIndex** incorporam consultas naturais e geração de relatórios dinâmicos baseados em IA, facilitando acesso intuitivo à informação.

### Segurança

- **HashiCorp Vault:** gerenciamento seguro de segredos, reduz riscos de exposição.
- **MinIO:** armazenamento seguro, compatível com S3, criptografia e alta disponibilidade.

### Administração

- **React Admin:** framework para painéis administrativos customizados, facilitando controle de acessos, configurações e governança centralizada.

### Arquitetura da solução

```mermaid
flowchart TD
 subgraph Fontes_de_Informacao["Fontes_de_Informacao"]
        F1["Sistemas Administrativos e ERP"]
        F2["Logs de uso erros e metricas de servidores aplicacoes e servicos"]
        F3["Informacoes de faturamento de servicos em nuvens e terceiros"]
        F4["Metricas de workloads - K8s VMs containers"]
        F5["Dados de orquestracao e pipelines CI_CD"]
        F6["Logs de seguranca e compliance"]
        F7["Contratos e SLAs"]
        F8["Inventario de ativos e recursos - CMDB"]
        F9["Dados financeiros e contabeis integrados"]
        F10["Metricas de rede e trafego detalhadas"]
        F11["Utilizacao de software e licenciamento"]
  end
 subgraph Coleta_Multi_cloud_e_On_Prem["Coleta_Multi_cloud_e_On_Prem"]
        A["OpenTelemetry - coleta unificada"]
        B["Steampipe - consultas SQL de APIs"]
        C["Cloud Custodian - automacao"]
        D["CloudQuery - coleta de Billing APIs"]
  end
 subgraph Normalizacao["Normalizacao"]
        E["Airflow e n8n - Orquestracao ETL"]
        F["dbt - Transformacao modelo FOCUS e Cost Model"]
  end
 subgraph Armazenamento["Armazenamento"]
        G["Data Lake ou Graph DB - PostgreSQL Neo4j ChromaDB"]
  end
 subgraph Machine_Learning["Machine_Learning"]
        H["Kubeflow ou MLFlow - modelagem e anomalias"]
  end
 subgraph Custos_Multiambiente["Custos_Multiambiente"]
        I["Kubecost ou OpenCost - Kubernetes"]
        J["FinOps Dashboards - Multi cloud Billing e Cost Allocation"]
  end
 subgraph Visualizacao["Visualizacao"]
        K["Superset - dashboards e NLQ via Semantic Layer e AI Agents"]
        L["Metabase - dashboards e NLQ via Ask Metabase"]
        M["Grafana - alertas e visualizacao"]
  end
 subgraph Consulta_Natural["Consulta_Natural"]
        N["LangChain e LlamaIndex - NLQ e RAG com LLM"]
  end
 subgraph Paines_Administrativos["Paines_Administrativos"]
        O["React Admin - gestao de acessos interfaces e controle centralizado"]
  end
 subgraph Seguranca["Seguranca"]
        P["HashiCorp Vault - cofre de segredos"]
        Q["MinIO - armazenamento seguro e criptografado"]
  end
    F1 --> A
    F2 --> A
    F3 --> D
    F4 --> A
    F5 --> E
    F6 --> C
    F7 --> J
    F8 --> G
    F9 --> J
    F10 --> D
    F11 --> J
    A --> E
    B --> E
    C --> E
    D --> E
    E --> F & P
    F --> G & P
    G --> H & I & J & N & Q
    H --> K & L & P
    I --> M & P
    J --> K & L & P
    N --> K & L & M
    O --> E & F & G & H & I & J & K & L & M & N

    classDef coleta fill:#DDF,stroke:#333,stroke-width:2px
    classDef normalizacao fill:#FDD,stroke:#333,stroke-width:2px
    classDef armazenamento fill:#DFD,stroke:#333,stroke-width:2px
    classDef ml fill:#FFD,stroke:#333,stroke-width:2px
    classDef custos fill:#FDF,stroke:#333,stroke-width:2px
    classDef visualizacao fill:#CDF,stroke:#333,stroke-width:2px
    classDef nlq fill:#FCF,stroke:#333,stroke-width:2px
    classDef admin fill:#DEF,stroke:#333,stroke-width:2px
    classDef seguranca fill:#F9F,stroke:#333,stroke-width:2px
    classDef fontes fill:#FF9,stroke:#333,stroke-width:2px
    style Custos_Multiambiente color:#000000
```

## Benefícios da Stack

- **Escalabilidade e flexibilidade:** apta para crescimento e mudanças sem bloqueios tecnológicos.
- **Open Source e padrões abertos:** evita vendor lock-in, facilita integração e customização.
- **Cobertura abrangente:** do monitoramento à visualização, passando por ML, FinOps e segurança.
- **Custo-benefício:** uso racionalizado de recursos e ferramentas maduras.
- **Suporte à inovação:** incorpora recursos avançados como NLQ e IA.

---

## Conclusão

Esta stack é uma base estratégica para empresas que buscam governança inteligente de ambientes híbridos e multi-cloud, alinhando tecnologia de ponta, segurança, eficiência operacional e experiência do usuário. Ela oferece um ecossistema integrado, capaz de suportar desde operações críticas até análises avançadas, facilitando decisões embasadas e ágeis.

---

WIP
