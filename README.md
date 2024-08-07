*Estrutura do Banco de Dados*

Abaixo estão descritas as principais entidades do banco de dados e seus relacionamentos.

Entidades

*Cliente*

idCliente INT (chave primária)

Nome VARCHAR(45)

CPF INT

CNPJ INT

TipoPessoa ENUM('CPF', 'CNPJ')

Endereco VARCHAR(255)

Telefone VARCHAR(20)

Email VARCHAR(45)

Aniversario DATE

*Pedido*

idPedido INT (chave primária)

Cliente_idCliente INT (chave estrangeira referenciando Cliente)

Data 

Endereco VARCHAR(255)

DataEntrega DATE

ValorFrete DECIMAL(10,2)

PeriodoCarencia VARCHAR(45)

*Produto*

idProduto INT (chave primária)

Nome VARCHAR(45)

Fornecedor_idFornecedor INT (chave estrangeira referenciando Fornecedor)

Estoque_idEstoque INT (chave estrangeira referenciando Estoque)

*Fornecedor*

idFornecedor INT (chave primária)

Nome VARCHAR(45)

CNPJ INT

*Estoque*

idEstoque INT (chave primária)

Localizacao VARCHAR(255)

*Vendedor*

idVendedor INT (chave primária)

Nome VARCHAR(45)

Estoque_idEstoque INT (chave estrangeira referenciando Estoque)

Pedido_Produto (Entidade associativa para N:M entre Pedido e Produto)

Pedido_idPedido INT (chave estrangeira referenciando Pedido)

Produto_idProduto INT (chave estrangeira referenciando Produto)

Quantidade INT

*Pagamento*

idPagamento INT (chave primária)

Pedido_idPedido INT (chave estrangeira referenciando Pedido)

TipoPagamento ENUM('Cartao', 'Boleto', 'Pix')

Valor DECIMAL(10,2)

*Cartao (detalhes do cartão de crédito, se o pagamento for feito via cartão)*

idCartao INT (chave primária)

Pagamento_idPagamento INT (chave estrangeira referenciando Pagamento)

NumeroCartao VARCHAR(16)

NomeTitular VARCHAR(45)

Validade DATE

CVV INT

*Relacionamentos*

Cliente 1:N Pedido: Um cliente pode realizar vários pedidos.

Pedido N:M Produto (por meio de Pedido_Produto): Um pedido pode conter vários produtos, e um produto pode estar em vários pedidos.

Produto 1:N Fornecedor: Um produto é fornecido por um fornecedor, mas um fornecedor pode fornecer vários produtos.

Fornecedor 1:N Produto: Um fornecedor pode fornecer vários produtos.

Vendedor N:M Pedido (por meio de Pedido_has_Vendedor): Um pedido pode envolver vários vendedores e um vendedor pode estar envolvido em vários pedidos.

Estoque 1:N Produto: Um estoque pode conter vários produtos, e um produto pode estar em diferentes estoques.

Vendedor 1:N Estoque: Um vendedor pode gerenciar múltiplos estoques.

Pedido 1:N Pagamento: Um pedido pode ser pago por meio de vários pagamentos (múltiplos métodos de pagamento).

Pagamento 1:1 Cartao: Um pagamento pode ter detalhes do cartão de crédito se for realizado via cartão.

*Como Executar*

Clone o repositório para o seu ambiente local.

Abra o arquivo SQL no seu cliente de banco de dados preferido (por exemplo, MySQL Workbench).

Execute o script para criar o banco de dados e as tabelas.

Insira dados de exemplo nas tabelas para testar a estrutura e as relações.

Futuras Melhorias

Implementação de triggers e procedures para automação de certas operações.

Adição de logs de auditoria para monitorar alterações nos dados.

Desenvolvimento de uma interface frontend para interação com o banco de dados.

*Contribuições*

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e enviar pull requests para melhorar o projeto.

*Licença*

Este projeto está licenciado sob a Licença MIT. Consulte o arquivo LICENSE para obter mais detalhes.
