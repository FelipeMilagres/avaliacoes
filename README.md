1. Schema SQLite (pronto pra rodar)
-- customers
CREATE TABLE customers (
  id TEXT PRIMARY KEY,
  name TEXT,
  age INTEGER,
  city TEXT,
  state TEXT,
  persona TEXT,
  monthly_income REAL,
  created_at TEXT
);

-- accounts
CREATE TABLE accounts (
  id TEXT PRIMARY KEY,
  customer_id TEXT,
  institution TEXT,
  type TEXT,
  balance REAL,
  open_finance INTEGER,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- transactions
CREATE TABLE transactions (
  id TEXT PRIMARY KEY,
  account_id TEXT,
  amount REAL,
  category TEXT,
  subcategory TEXT,
  merchant TEXT,
  transaction_date TEXT,
  payment_method TEXT,
  is_recurring INTEGER,
  FOREIGN KEY (account_id) REFERENCES accounts(id)
);

-- liabilities
CREATE TABLE liabilities (
  id TEXT PRIMARY KEY,
  customer_id TEXT,
  type TEXT,
  outstanding REAL,
  monthly_payment REAL,
  interest_rate REAL,
  delinquency_days INTEGER,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- income_sources
CREATE TABLE income_sources (
  id TEXT PRIMARY KEY,
  customer_id TEXT,
  type TEXT,
  amount REAL,
  frequency TEXT,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- feature store
CREATE TABLE customer_features (
  customer_id TEXT PRIMARY KEY,
  monthly_spend REAL,
  food_ratio REAL,
  fuel_ratio REAL,
  pharmacy_ratio REAL,
  debt_to_income REAL,
  credit_utilization REAL,
  financial_stress_score REAL,
  lifestyle_cluster TEXT,
  propensity_credit REAL,
  propensity_cashback REAL
);

-- offers
CREATE TABLE offers (
  id TEXT PRIMARY KEY,
  name TEXT,
  category TEXT,
  description TEXT,
  target_persona TEXT,
  min_score REAL
);

-- decision logs
CREATE TABLE decision_logs (
  id TEXT PRIMARY KEY,
  customer_id TEXT,
  offer_id TEXT,
  score REAL,
  reason TEXT,
  created_at TEXT
);
🧪 2. Mock de dados (3 personas)
👩 Maria (família)
INSERT INTO customers VALUES 
('c1','Maria Silva',34,'São Paulo','SP','familia',3500,'2026-01-01');

INSERT INTO accounts VALUES 
('a1','c1','Banco X','checking',1200,1);

INSERT INTO transactions VALUES
('t1','a1',-500,'food','supermarket','Carrefour','2026-09-01','credit',0),
('t2','a1',-300,'food','supermarket','Atacadão','2026-09-02','debit',0),
('t3','a1',-200,'shopping','clothes','Renner','2026-09-03','credit',0);

INSERT INTO customer_features VALUES
('c1',2800,0.42,0.05,0.02,0.3,0.6,0.5,'familia',0.7,0.9);
🚗 João (motorista)
INSERT INTO customers VALUES 
('c2','João Carlos',41,'São Paulo','SP','mobilidade',4000,'2026-01-01');

INSERT INTO accounts VALUES 
('a2','c2','Banco Y','checking',800,1);

INSERT INTO transactions VALUES
('t4','a2',-600,'fuel','gas','Shell','2026-09-01','credit',0),
('t5','a2',-400,'fuel','gas','Ipiranga','2026-09-02','debit',0);

INSERT INTO customer_features VALUES
('c2',3200,0.1,0.38,0.01,0.4,0.8,0.7,'mobilidade',0.8,0.5);
👵 Louder (idosa)
INSERT INTO customers VALUES 
('c3','Louder Carvalho',64,'Belo Horizonte','MG','idoso',2000,'2026-01-01');

INSERT INTO accounts VALUES 
('a3','c3','Banco Z','checking',500,1);

INSERT INTO transactions VALUES
('t6','a3',-300,'pharmacy','medicines','Drogaria','2026-09-01','debit',0);

INSERT INTO customer_features VALUES
('c3',1800,0.1,0.02,0.25,0.2,0.3,0.4,'idoso',0.6,0.7);
🎯 3. Ofertas
INSERT INTO offers VALUES
('o1','Cashback Supermercado','food','Ganhe cashback em compras','familia',0.7),
('o2','Desconto Combustível','fuel','Desconto em postos','mobilidade',0.7),
('o3','Farmácia Desconto','pharmacy','Desconto em medicamentos','idoso',0.6),
('o4','Crédito Pessoal','credit','Crédito facilitado','todos',0.75);
🧠 4. Query base (pré-decision engine)
SELECT 
  c.name,
  f.lifestyle_cluster,
  o.name AS offer,
  f.food_ratio,
  f.fuel_ratio,
  f.pharmacy_ratio
FROM customers c
JOIN customer_features f ON c.id = f.customer_id
JOIN offers o ON 
  o.target_persona = f.lifestyle_cluster
;
⚙️ 5. Lógica do Decision Engine (Node exemplo)
function evaluateOffers(features) {
  const offers = [];

  if (features.food_ratio > 0.3) {
    offers.push({
      name: "Cashback Supermercado",
      score: features.food_ratio * 2,
      reason: "Alto gasto com supermercado"
    });
  }

  if (features.fuel_ratio > 0.2) {
    offers.push({
      name: "Desconto Combustível",
      score: features.fuel_ratio * 2,
      reason: "Alto gasto com combustível"
    });
  }

  if (features.pharmacy_ratio > 0.2) {
    offers.push({
      name: "Farmácia Desconto",
      score: features.pharmacy_ratio * 2,
      reason: "Alto gasto com farmácia"
    });
  }

  return offers.sort((a, b) => b.score - a.score);
}
🔌 6. API simples (Express)
Endpoint principal
app.get('/customers/:id/offers', async (req, res) => {
  const { id } = req.params;

  const customer = await db.get(`
    SELECT * FROM customers WHERE id = ?
  `, [id]);

  const features = await db.get(`
    SELECT * FROM customer_features WHERE customer_id = ?
  `, [id]);

  const offers = evaluateOffers(features);

  res.json({
    customer: customer.name,
    persona: features.lifestyle_cluster,
    offers
  });
});
🚀 7. O que você tem pronto com isso

✔ Mock de Open Finance
✔ Feature store
✔ Decision engine
✔ API funcional
✔ 3 personas reais
✔ Explicabilidade

💡 8. Próximo nível (se quiser subir muito)

Você pode adicionar:

tabela events → simular contexto (salário, saldo baixo)
boost de score por evento
logs no decision_logs
🎯 Resumo

Você agora tem:

👉 um mini banco digital rodando em SQLite
👉 com motor de decisão plugado
👉 pronto pra demonstrar personalização real

Se quiser, eu posso te mandar na próxima:

📦 projeto Node completo (estrutura de pastas)
🐳 docker pronto
📊 script pra gerar 100 clientes fake
🎤 roteiro de apresentação (isso aqui fecha o hackathon)

Só falar 👍