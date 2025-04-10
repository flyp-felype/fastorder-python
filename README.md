# 🧠 Desafio: Sistema de Pedidos com Django + PostgreSQL + Kafka + Docker + Clean Architecture

## 💡 Descrição do desafio

Crie uma aplicação Django chamada **"FastOrder"**, que simule um sistema de pedidos para uma lanchonete. O sistema terá dois domínios principais:

- **Cliente realiza um pedido**
- **Sistema envia o pedido para uma fila (Kafka)**
- **Outro serviço Django (ou comando) consome essa fila e marca o pedido como "Em preparação"**

---

## ✅ Requisitos funcionais

1. Um **cliente** pode criar um **pedido**, com:
   - nome do cliente
   - itens do pedido (hambúrguer, batata, refrigerante, etc.)
   - horário do pedido
   - status (aguardando, em preparação, pronto)

2. O **pedido** é salvo no PostgreSQL.

3. O pedido é enviado para um **tópico Kafka** chamado `new_orders`.

4. Um **consumidor Kafka** lê do tópico e atualiza o status para “em preparação”.

---

## ✅ Requisitos técnicos

- Django (usando Django REST Framework)
- Banco: PostgreSQL
- Fila: Kafka
- Docker + Docker Compose
- Clean Architecture (camadas separadas: domain, application, infrastructure, etc.)
- Design Patterns:
  - Repository Pattern
  - Service Layer
  - DTOs (opcional)
  - Factory ou Strategy (extra, se quiser ir além)

---

## 📁 Sugestão de estrutura de pastas (Clean Architecture)

fastorder/
│
├── domain/
│   └── models/
│       └── order.py
│
├── application/
│   └── services/
│       └── create_order_service.py
│
├── infrastructure/
│   ├── kafka/
│   │   ├── producer.py
│   │   └── consumer.py
│   └── database/
│       └── order_repository.py
│
├── interface/
│   └── api/
│       ├── serializers.py
│       ├── views.py
│       └── urls.py
│
├── settings/
│   └── base.py
│
├── manage.py
└── Dockerfile / docker-compose.yml




