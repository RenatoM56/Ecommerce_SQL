Consultas SQL (Queries)
A seguir estão exemplos de queries para responder perguntas baseadas no cenário:

Quantidade de pedidos por cliente:

SELECT id_cliente, COUNT(id_pedido) AS quantidade_pedidos
FROM Pedidos
GROUP BY id_cliente;
Verificar se algum vendedor também é fornecedor:


SELECT v.nome AS vendedor, f.nome AS fornecedor
FROM Vendedores v
INNER JOIN Fornecedores f ON v.contato = f.contato;
Relação de produtos, fornecedores e estoque:


SELECT p.nome AS produto, f.nome AS fornecedor, p.quantidade_estoque
FROM Produtos p
INNER JOIN Fornecedores_Produtos fp ON p.id_produto = fp.id_produto
INNER JOIN Fornecedores f ON f.id_fornecedor = fp.id_fornecedor;
Listar nomes dos fornecedores e produtos fornecidos:


SELECT f.nome AS fornecedor, p.nome AS produto
FROM Fornecedores f
INNER JOIN Fornecedores_Produtos fp ON f.id_fornecedor = fp.id_fornecedor
INNER JOIN Produtos p ON p.id_produto = fp.id_produto
ORDER BY f.nome;
Valor total dos pagamentos por pedido:


SELECT id_pedido, SUM(valor) AS total_pagamento
FROM Pagamentos
GROUP BY id_pedido
HAVING SUM(valor) > 0;
Pedidos com status de entrega 'enviado' e ordenados pela data:


SELECT id_pedido, id_cliente, data_pedido, status_entrega
FROM Pedidos
WHERE status_entrega = 'enviado'
ORDER BY data_pedido DESC;
