# massa-de-dados-mercenaria-
-- Compatível com MySQL.
-- Os dados abaixo não representam pessoas, empresas ou valores reais.
-- Pressupõe que as tabelas e colunas tenham sido criadas pelo script do banco.

SET NAMES utf8mb4;

-- 8 profissionais, conforme o porte informado:
-- 1 proprietário, 1 vendedor/projetista, 1 comprador,
-- 2 marceneiros, 2 montadores e 1 entregador.

INSERT INTO vendedor (id_vendedor, nome, email, telefone, carga) VALUES
(1, 'Ana Beatriz Lima', 'ana.vendas@exemplo.com', '(11) 90000-1001', 'Atendimento, vendas e projetos');

INSERT INTO comprador (id_comprador, nome, email, telefone, carga) VALUES
(1, 'Bruno Henrique Alves', 'bruno.compras@exemplo.com', '(11) 90000-1002', 'Compras e contato com fornecedores');

INSERT INTO marceneiro (id_marceneiro, nome, email, telefone, carga) VALUES
(1, 'Carlos Eduardo Nunes', 'carlos.marcenaria@exemplo.com', '(11) 90000-1003', 'Fabricação e acabamento'),
(2, 'Diego Martins Rocha', 'diego.marcenaria@exemplo.com', '(11) 90000-1004', 'Fabricação e acabamento');

INSERT INTO montador (id_montador, nome, email, telefone, carga) VALUES
(1, 'Eduardo Felipe Costa', 'eduardo.montagem@exemplo.com', '(11) 90000-1005', 'Montagem e instalação'),
(2, 'Fábio Augusto Melo', 'fabio.montagem@exemplo.com', '(11) 90000-1006', 'Montagem e instalação');

INSERT INTO proprietario (id_proprietario, nome, email, telefone, carga) VALUES
(1, 'Marcos Vinícius Duarte', 'marcos.gestao@exemplo.com', '(11) 90000-1007', 'Administração e decisões gerais');

INSERT INTO entregador (id_entregador, nome, email, telefone, carga) VALUES
(1, 'Gustavo Henrique Reis', 'gustavo.entregas@exemplo.com', '(11) 90000-1008', 'Entrega de materiais e móveis');

-- 10 clientes fictícios; o cliente 10 permanece sem projeto para testar consultas de auditoria.
INSERT INTO cliente (id_cliente, nome, telefone, cpf, email, endereco) VALUES
(1, 'Camila Ferreira Souza', '(11) 91111-2001', '000.000.000-01', 'camila.souza@exemplo.com', 'Rua das Acácias, 101 - São Paulo/SP'),
(2, 'Rafael Oliveira Mendes', '(11) 91111-2002', '000.000.000-02', 'rafael.mendes@exemplo.com', 'Avenida Central, 220 - São Paulo/SP'),
(3, 'Juliana Martins Araújo', '(11) 91111-2003', '000.000.000-03', 'juliana.araujo@exemplo.com', 'Rua do Bosque, 315 - Osasco/SP'),
(4, 'Marcelo Gomes Ribeiro', '(11) 91111-2004', '000.000.000-04', 'marcelo.ribeiro@exemplo.com', 'Rua Projetada, 48 - Barueri/SP'),
(5, 'Patrícia Almeida Castro', '(11) 91111-2005', '000.000.000-05', 'patricia.castro@exemplo.com', 'Alameda das Flores, 76 - Cotia/SP'),
(6, 'Felipe Santos Moraes', '(11) 91111-2006', '000.000.000-06', 'felipe.moraes@exemplo.com', 'Rua das Palmeiras, 190 - Guarulhos/SP'),
(7, 'Renata Carvalho Dias', '(11) 91111-2007', '000.000.000-07', 'renata.dias@exemplo.com', 'Avenida das Nações, 501 - São Paulo/SP'),
(8, 'Leonardo Barbosa Freitas', '(11) 91111-2008', '000.000.000-08', 'leonardo.freitas@exemplo.com', 'Rua do Comércio, 88 - Taboão da Serra/SP'),
(9, 'Sônia Cristina Lopes', '(11) 91111-2009', '000.000.000-09', 'sonia.lopes@exemplo.com', 'Rua dos Ipês, 412 - Santo André/SP'),
(10, 'Thiago Pires da Silva', '(11) 91111-2010', '000.000.000-10', 'thiago.silva@exemplo.com', 'Rua Nova, 33 - São Paulo/SP');

-- 8 fornecedores fictícios de materiais primários.
INSERT INTO fornecedor (id_fornecedor, nome, telefone, email, cnpj, endereco) VALUES
(1, 'Madeiras Horizonte Ltda.', '(11) 92222-3001', 'contato@madeirashorizonte.exemplo', '00.000.000/0001-01', 'Rua Industrial, 10 - São Paulo/SP'),
(2, 'Painéis Brasil Fictícia Ltda.', '(11) 92222-3002', 'vendas@paineisbrasil.exemplo', '00.000.000/0001-02', 'Avenida das Fábricas, 20 - Guarulhos/SP'),
(3, 'Ferragens União Comercial', '(11) 92222-3003', 'pedidos@ferragensuniao.exemplo', '00.000.000/0001-03', 'Rua dos Oficiais, 30 - Osasco/SP'),
(4, 'Vidros Linha Clara', '(11) 92222-3004', 'contato@linhaclara.exemplo', '00.000.000/0001-04', 'Avenida dos Vidros, 40 - Barueri/SP'),
(5, 'Acabamentos Prime', '(11) 92222-3005', 'vendas@acabamentosprime.exemplo', '00.000.000/0001-05', 'Rua do Acabamento, 50 - Cotia/SP'),
(6, 'Colas e Insumos Alfa', '(11) 92222-3006', 'comercial@insumosalfa.exemplo', '00.000.000/0001-06', 'Rua dos Insumos, 60 - São Paulo/SP'),
(7, 'Perfis Metálicos Beta', '(11) 92222-3007', 'pedidos@perfisbeta.exemplo', '00.000.000/0001-07', 'Avenida Metalúrgica, 70 - Santo André/SP'),
(8, 'Embalagens Protege', '(11) 92222-3008', 'vendas@protege.exemplo', '00.000.000/0001-08', 'Rua das Embalagens, 80 - Taboão da Serra/SP');

-- 15 materiais, cobrindo chapas, madeira, ferragens, acabamento e embalagem.
INSERT INTO material (id_material, nome, descricao, tipo_de_material, medida) VALUES
(1, 'MDF branco 15 mm', 'Chapa branca para estrutura e divisórias', 'Chapa de madeira', 'chapa'),
(2, 'MDF amadeirado 18 mm', 'Chapa amadeirada para portas e painéis', 'Chapa de madeira', 'chapa'),
(3, 'MDF preto 15 mm', 'Chapa preta para nichos e detalhes', 'Chapa de madeira', 'chapa'),
(4, 'Compensado 10 mm', 'Painel auxiliar para fundos', 'Chapa de madeira', 'chapa'),
(5, 'Madeira maciça pinus', 'Peças para reforços e acabamentos', 'Madeira', 'metro'),
(6, 'Fita de borda branca', 'Fita para acabamento de bordas', 'Acabamento', 'metro'),
(7, 'Fita de borda amadeirada', 'Fita para acabamento amadeirado', 'Acabamento', 'metro'),
(8, 'Dobradiça com amortecimento', 'Ferragem para portas de armário', 'Ferragem', 'unidade'),
(9, 'Corrediça telescópica', 'Ferragem para gavetas', 'Ferragem', 'par'),
(10, 'Puxador preto', 'Puxador para portas e gavetas', 'Ferragem', 'unidade'),
(11, 'Parafuso para MDF', 'Parafuso para montagem das estruturas', 'Ferragem', 'unidade'),
(12, 'Cola para madeira', 'Adesivo para montagem e acabamento', 'Insumo', 'litro'),
(13, 'Verniz acetinado', 'Produto para acabamento de madeira', 'Acabamento', 'litro'),
(14, 'Vidro incolor 6 mm', 'Vidro para portas e nichos', 'Vidro', 'metro quadrado'),
(15, 'Manta de proteção', 'Material para proteção durante transporte', 'Embalagem', 'metro');

-- 15 registros de estoque, incluindo saldos baixos e sobras reaproveitáveis.
INSERT INTO estoque (id_estoque, nome, quantidade, medida) VALUES
(1, 'MDF branco 15 mm', 18, 'chapas'),
(2, 'MDF amadeirado 18 mm', 7, 'chapas'),
(3, 'MDF preto 15 mm', 4, 'chapas'),
(4, 'Compensado 10 mm', 12, 'chapas'),
(5, 'Madeira maciça pinus', 32, 'metros'),
(6, 'Fita de borda branca', 185, 'metros'),
(7, 'Fita de borda amadeirada', 96, 'metros'),
(8, 'Dobradiça com amortecimento', 46, 'unidades'),
(9, 'Corrediça telescópica', 18, 'pares'),
(10, 'Puxador preto', 38, 'unidades'),
(11, 'Parafuso para MDF', 620, 'unidades'),
(12, 'Cola para madeira', 9, 'litros'),
(13, 'Verniz acetinado', 3, 'litros'),
(14, 'Vidro incolor 6 mm', 11, 'metros quadrados'),
(15, 'Manta de proteção', 74, 'metros');

-- 12 projetos em três períodos, mantendo a média de 4 projetos por mês.
-- O projeto 12 foi cancelado para cobrir uma situação excepcional.
INSERT INTO projeto (id_projeto, descricao, dados, valor, prazo, status, id_cliente, id_vendedor) VALUES
(1, 'Cozinha planejada em MDF branco e amadeirado', '2026-08-04', 18500.00, '2026-08-29', 'Concluído', 1, 1),
(2, 'Quarto planejado com armário e bancada', '2026-08-08', 12800.00, '2026-09-05', 'Concluído', 2, 1),
(3, 'Home office com estante e gaveteiro', '2026-08-15', 7600.00, '2026-09-12', 'Concluído', 3, 1),
(4, 'Painel de sala com rack suspenso', '2026-08-22', 6900.00, '2026-09-19', 'Em montagem', 4, 1),
(5, 'Cozinha compacta para apartamento', '2026-09-02', 14900.00, '2026-09-30', 'Concluído', 5, 1),
(6, 'Armários para lavanderia', '2026-09-07', 8300.00, '2026-10-03', 'Em montagem', 6, 1),
(7, 'Closet planejado com portas de correr', '2026-09-14', 21700.00, '2026-10-15', 'Em fabricação', 7, 1),
(8, 'Balcão de atendimento comercial', '2026-09-21', 11200.00, '2026-10-18', 'Em fabricação', 8, 1),
(9, 'Estante para escritório comercial', '2026-10-01', 9700.00, '2026-10-28', 'Concluído', 9, 1),
(10, 'Cozinha planejada com torre quente', '2026-10-06', 23400.00, '2026-11-12', 'Em fabricação', 1, 1),
(11, 'Quarto infantil com bancada', '2026-10-15', 10100.00, '2026-11-20', 'Em orçamento', 2, 1),
(12, 'Painel decorativo sob medida', '2026-10-25', 5400.00, '2026-11-15', 'Cancelado', 3, 1);

-- 12 planos de corte, um por projeto, vinculando a liberação dos materiais.
INSERT INTO plano_de_corte (id_plano, dados, descricao, id_projeto) VALUES
(1, '2026-08-05', 'Cortes para cozinha branca e amadeirada', 1),
(2, '2026-08-09', 'Cortes para armário, bancada e portas', 2),
(3, '2026-08-16', 'Cortes para estante, tampo e gaveteiro', 3),
(4, '2026-08-23', 'Cortes para painel e rack suspenso', 4),
(5, '2026-09-03', 'Cortes para cozinha compacta', 5),
(6, '2026-09-08', 'Cortes para armários de lavanderia', 6),
(7, '2026-09-15', 'Cortes para closet e portas de correr', 7),
(8, '2026-09-22', 'Cortes para balcão e prateleiras comerciais', 8),
(9, '2026-10-02', 'Cortes para estante comercial', 9),
(10, '2026-10-07', 'Cortes para cozinha e torre quente', 10),
(11, '2026-10-16', 'Cortes para quarto infantil e bancada', 11),
(12, '2026-10-26', 'Cortes previstos para painel decorativo', 12);

-- Participação dos marceneiros na fabricação de cada projeto.
INSERT INTO projeto_marceneiro (id_projeto, id_plano, id_marceneiro) VALUES
(1, 1, 1), (1, 1, 2),
(2, 2, 1), (2, 2, 2),
(3, 3, 2),
(4, 4, 1), (4, 4, 2),
(5, 5, 1),
(6, 6, 2),
(7, 7, 1), (7, 7, 2),
(8, 8, 1),
(9, 9, 2),
(10, 10, 1), (10, 10, 2),
(11, 11, 2),
(12, 12, 1);

-- 10 montagens; projetos em orçamento ou cancelado não possuem montagem concluída.
INSERT INTO montagem (id_montagem, id_projeto, id_montador, data_prevista, data_realizada, status) VALUES
(1, 1, 1, '2026-08-29', '2026-08-29', 'Concluída'),
(2, 2, 2, '2026-09-05', '2026-09-06', 'Concluída'),
(3, 3, 1, '2026-09-12', '2026-09-12', 'Concluída'),
(4, 4, 2, '2026-09-19', NULL, 'Agendada'),
(5, 5, 1, '2026-09-30', '2026-10-01', 'Concluída'),
(6, 6, 2, '2026-10-03', NULL, 'Agendada'),
(7, 7, 1, '2026-10-15', NULL, 'Aguardando fabricação'),
(8, 8, 2, '2026-10-18', NULL, 'Aguardando fabricação'),
(9, 9, 1, '2026-10-28', '2026-10-29', 'Concluída'),
(10, 10, 2, '2026-11-12', NULL, 'Aguardando fabricação');

-- 8 pedidos de compra com diferentes situações e períodos.
INSERT INTO pedido (id_pedido, id_fornecedor, id_comprador, dados, valor, status) VALUES
(1, 1, 1, '2026-08-01', 4280.00, 'Recebido'),
(2, 3, 1, '2026-08-06', 1760.00, 'Recebido'),
(3, 2, 1, '2026-08-28', 3950.00, 'Recebido'),
(4, 4, 1, '2026-09-10', 1480.00, 'Recebido'),
(5, 5, 1, '2026-09-18', 980.00, 'Recebido'),
(6, 1, 1, '2026-10-03', 5120.00, 'Em trânsito'),
(7, 6, 1, '2026-10-11', 690.00, 'Solicitado'),
(8, 8, 1, '2026-10-20', 430.00, 'Cancelado');

-- Itens dos pedidos: um pedido pode conter vários materiais.
INSERT INTO item_pedido (id_pedido, id_material, quantidade, preco_unitario) VALUES
(1, 1, 20, 145.00), (1, 2, 8, 210.00), (1, 6, 120, 1.50),
(2, 8, 50, 18.00), (2, 9, 20, 43.00), (2, 11, 500, 0.56),
(3, 1, 15, 145.00), (3, 3, 6, 198.00), (3, 7, 100, 1.50),
(4, 14, 12, 120.00),
(5, 13, 5, 88.00), (5, 10, 30, 18.00),
(6, 2, 20, 215.00), (6, 5, 35, 24.00),
(7, 12, 10, 69.00),
(8, 15, 40, 10.75);

-- Pagamentos em formas variadas e em diferentes situações.
INSERT INTO pagamento (id_pagamento, id_projeto, valor, dados_de_emissao, forma_de_pagamento, status) VALUES
(1, 1, 9250.00, '2026-08-04', 'PIX', 'Recebido'),
(2, 1, 9250.00, '2026-08-29', 'Transferência', 'Recebido'),
(3, 2, 6400.00, '2026-08-08', 'Cartão', 'Recebido'),
(4, 2, 6400.00, '2026-09-06', 'Boleto', 'Recebido'),
(5, 3, 3800.00, '2026-08-15', 'PIX', 'Recebido'),
(6, 4, 3450.00, '2026-08-22', 'PIX', 'Recebido'),
(7, 5, 7450.00, '2026-09-02', 'Transferência', 'Recebido'),
(8, 6, 4150.00, '2026-09-07', 'Cartão', 'Recebido'),
(9, 7, 10850.00, '2026-09-14', 'Boleto', 'Pendente'),
(10, 8, 5600.00, '2026-09-21', 'PIX', 'Recebido'),
(11, 9, 9700.00, '2026-10-29', 'Transferência', 'Recebido'),
(12, 10, 11700.00, '2026-10-06', 'PIX', 'Recebido');

-- Uma nota fiscal por projeto faturado; o projeto cancelado não possui nota.
INSERT INTO nota_fiscal (id_nota, numero, dados_de_emissao, valor, id_projeto) VALUES
(1, 'NF-2026-0001', '2026-08-29', 18500.00, 1),
(2, 'NF-2026-0002', '2026-09-06', 12800.00, 2),
(3, 'NF-2026-0003', '2026-09-12', 7600.00, 3),
(4, 'NF-2026-0004', '2026-09-19', 6900.00, 4),
(5, 'NF-2026-0005', '2026-10-01', 14900.00, 5),
(6, 'NF-2026-0006', '2026-10-03', 8300.00, 6),
(7, 'NF-2026-0007', '2026-10-15', 21700.00, 7),
(8, 'NF-2026-0008', '2026-10-18', 11200.00, 8),
(9, 'NF-2026-0009', '2026-10-29', 9700.00, 9),
(10, 'NF-2026-0010', '2026-10-30', 23400.00, 10);

-- Fim da carga da massa de dados.
