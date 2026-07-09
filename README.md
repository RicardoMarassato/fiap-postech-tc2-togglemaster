# ToggleMaster V2 🚀

> FIAP Postech - DevOps & Cloud Architecture (Tech Challenge - Fase 2)

O **ToggleMaster V2** é a evolução de uma arquitetura monolítica para um ecossistema distribuído de microsserviços rodando em Kubernetes. O projeto gerencia *feature flags* e segmentação de usuários com foco em alta performance e escalabilidade.

---

## 📋 Informações de Entrega

* **RM:** 370358
* **Discord:** marassato7700
* **Repositório do GitHub:** [fiap-postech-tc2-togglemaster](https://github.com/RicardoMarassato/fiap-postech-tc2-togglemaster)
* **Link do Vídeo de Demonstração:** [Vídeo de Demonstração (Google Drive)](https://drive.google.com/file/d/13AwpXtu6ki4e_tJXQc1rfbPe6VK2CNo9/view?usp=sharing)
* **Documentação de Entrega:** [Ricardo-Marassato-readme-tech-phase-2.md](Ricardo-Marassato-readme-tech-phase-2.md)

---

## 🛠️ Tecnologias Utilizadas

![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![AWS EKS](https://img.shields.io/badge/AWS_EKS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)

---

## 🧩 Arquitetura de Microsserviços

O ecossistema é composto por 5 serviços independentes:
* **auth-service (Go + Postgres)**: Autenticação e validação de chaves de API.
* **flag-service (Python + Postgres)**: CRUD e status das feature flags.
* **targeting-service (Python + Postgres)**: Regras de segmentação de usuários.
* **evaluation-service (Go + Redis)**: Avaliação de flags com cache em memória (hot path) e envio de eventos em background via SQS.
* **analytics-service (Python + SQS + DynamoDB)**: Consumo de eventos e gravação de telemetria.

---

## ⚡ Como Rodar Localmente

Para iniciar os 5 microsserviços integrados aos bancos de dados locais em containers Docker, execute:

```bash
docker compose up -d --build
```

### 💡 Dica de Produtividade: Clonando os Repositórios da Organização

Se você precisar clonar localmente todos os 5 repositórios originais dos microsserviços do projeto para desenvolvimento ou auditoria, pode utilizar o script auxiliar [git-cloner.py](git-cloner.py) presente na raiz deste repositório.

**Pré-requisitos:**
* Python 3.x
* GitHub CLI (`gh`) instalado e autenticado.

**Como rodar:**
```bash
python git-cloner.py
```
O script usará a GitHub CLI para clonar automaticamente: `auth-service`, `flag-service`, `targeting-service`, `evaluation-service` e `analytics-service`.

---

## 📖 Relatório de Entrega e Infraestrutura (AWS EKS)

Toda a documentação técnica exigida para a entrega da Fase 2 está detalhada no relatório específico:

👉 **[Documentação de Entrega - Fase 2](Ricardo-Marassato-readme-tech-phase-2.md)**
