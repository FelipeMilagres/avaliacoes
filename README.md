Boa, isso aqui dá pra estruturar de forma bem sólida pra hackathon — principalmente se você quiser simular algo próximo de Open Finance + recomendação inteligente (IA).

Vou te montar um modelo de dados (banco mockado) + como usar esses dados pra gerar ofertas personalizadas baseado nas personas que você mostrou.

🧠 1. Conceito da arquitetura

Você precisa separar em 3 camadas:

🔹 1. Dados brutos (Open Finance - mock)

Simula o que viria de bancos:

contas
transações
renda
dívidas
comportamento
🔹 2. Enriquecimento (Feature Store / IA)

Transforma dados em insights

score de perfil
categorias de consumo
momento de vida
🔹 3. Motor de recomendação

Entrega:

ofertas (cashback, crédito, desconto, etc)
priorização
🗄️ 2. Modelo de Banco (Mock Open Finance)
👤 Tabela: customers
{
  "customer_id": "uuid",
  "name": "string",
  "age": 34,
  "region": "SP",
  "city": "São Paulo",
  "persona": "MASSA | IDOSO | MOTORISTA_APP",
  "monthly_income": 3500,
  "family_size": 3
}
🏦 Tabela: accounts
{
  "account_id": "uuid",
  "customer_id": "uuid",
  "bank": "Banco X",
  "type": "checking | savings",
  "balance": 1200.50
}
💳 Tabela: transactions

(simula Open Finance real)

{
  "transaction_id": "uuid",
  "account_id": "uuid",
  "date": "2026-09-01",
  "amount": -150.00,
  "category": "food | fuel | pharmacy | utilities | shopping",
  "merchant": "Carrefour",
  "channel": "debit | credit | pix"
}
💸 Tabela: loans
{
  "loan_id": "uuid",
  "customer_id": "uuid",
  "type": "consignado | pessoal",
  "outstanding_balance": 5000,
  "installment_value": 250,
  "interest_rate": 1.8
}
💰 Tabela: income_sources
{
  "income_id": "uuid",
  "customer_id": "uuid",
  "type": "salary | aposentadoria | informal",
  "amount": 2000,
  "frequency": "monthly"
}
🧾 Tabela: bills
{
  "bill_id": "uuid",
  "customer_id": "uuid",
  "type": "energia | agua | telefone",
  "amount": 300,
  "due_day": 10,
  "status": "paid | overdue"
}
🧠 3. Camada de Inteligência (Feature Engineering)

Aqui você transforma dados em algo útil:

📊 Tabela: customer_features
{
  "customer_id": "uuid",
  "avg_monthly_spend": 2800,
  "food_ratio": 0.35,
  "fuel_ratio": 0.25,
  "pharmacy_ratio": 0.10,
  "credit_usage": 0.8,
  "has_debt": true,
  "financial_health_score": 650,
  "price_sensitivity": "high | medium | low",
  "lifestyle": "familia | idoso | mobilidade"
}
🎯 4. Mapeando suas Personas
👩 Maria Silva (família / orçamento apertado)
{
  "lifestyle": "familia",
  "price_sensitivity": "high",
  "top_categories": ["food", "groceries"],
  "goal": "economizar"
}

👉 Ofertas ideais:

cashback supermercado
parcelamento
cupons
👨 João Carlos (motorista app)
{
  "lifestyle": "mobilidade",
  "top_categories": ["fuel", "maintenance"],
  "price_sensitivity": "medium"
}

👉 Ofertas:

desconto combustível
seguro auto
lavagem rápida
👵 Louder Carvalho (idosa / saúde)
{
  "lifestyle": "idoso",
  "top_categories": ["pharmacy"],
  "has_fixed_income": true
}

👉 Ofertas:

farmácia
consignado
descontos recorrentes
🤖 5. Motor de Recomendação (Regra + IA)
🔹 Versão simples (hackathon-friendly)
function getOffers(customer) {
  if (customer.lifestyle === "familia") {
    return ["cashback_supermercado", "parcele_facil"];
  }

  if (customer.lifestyle === "mobilidade") {
    return ["desconto_combustivel", "seguro_auto"];
  }

  if (customer.lifestyle === "idoso") {
    return ["farmacia_desconto", "credito_consignado"];
  }
}
🔹 Versão mais avançada (scoring)
{
  "offer": "cashback_supermercado",
  "score": 0.92
}

Baseado em:

frequência de compra
valor gasto
momento financeiro
📦 6. Tabela de Ofertas
{
  "offer_id": "uuid",
  "name": "Cashback Supermercado",
  "category": "food",
  "target_lifestyle": ["familia"],
  "min_score": 0.7
}
🔗 7. Fluxo completo (o que você apresenta no hackathon)
Mock Open Finance → carrega dados
Processa features
Classifica cliente
Gera recomendações
Mostra no app
💡 8. Extra (diferencial de hackathon)

Se quiser se destacar mesmo:

🔥 Adiciona:
NLP em descrição de transações
clusterização (K-Means) pra descobrir perfis

explicabilidade:

"Recomendamos desconto em combustível porque você gasta 28% com isso"

🚀 9. Resumo direto pra você usar

Você precisa de:

customers
transactions
accounts
loans
features
offers

E um motor que liga:
👉 comportamento → perfil → oferta

Se quiser, eu posso te montar:

dataset fake completo (JSON ou CSV)
API mock (Node/Python)
ou até um fluxo com IA usando prompt (LLM recomendando ofertas)

Só me fala como você quer implementar 👍