# l7cr
API DE INTEGRAÇÃO TOTALBANK


// GUIA API CR TOTAL BANK

    // EMITINDO boletos

      ENDPOINT PRINCIPAL: https://carreiraecommerce.com.br/l7cr

        url: /gerarboleto,
        dados: {
            banco: EX 001,
            codigoBeneficiario,
            cnpjBeneficiario,
            vencimento EX 2025-07-01,
            valor: ex: 500,
            accessToken: "ACCESS TOKEN TOTAL BANK",
            referente: EX "REFERENTE A FATURA DE JULHO"
        }

        metodo POST

        retorno do tipo JSON

        exemplo de retorno com sucesso

        {
            "status": 200,
            "token": 544545545414545454545, (SALVAR NO SISTEMA LOCAL PARA VISUALIZAÇÃO E PAGAMENTO DO BOLETO)
        }

    // Visualizando boleto gerado

    url: /visualizarboleto
    dados: {
        token: TOKEN RECEBIDO NA GERAÇÃO DO BOLETO,
    }

    metodo POST

     retorno do tipo JSON

        exemplo de retorno com sucesso

        {
            "status": 200,
            "content": {
                'linhadigitavel': 454545454545454542515454,
                'pdf': link para o arquivo PDF
            }
        }




// PAGAMENTO

    url: /pagamento,
        dados: {
            boleto: Ex TOKEN DO BOLETO GERADO NA GERAÇÃO DO BOLETO,
            codigoConvenio: codigoConvenio - (INFO DA CONTA TOTAL BANK),
            contaDebito: {
                agencia: EX AGENCIA DA CONTADO QUE VAI SER EFETUADO O PAGAMENTO,
                dvAgencia:  Dígito verificador da agência,
                contaCorrente: NUMERO DA CONTA CORRENTE,
                dvContaCorrente:  Dígito verificador da conta corrente
            },
            parametroPagamento: {
                codigoCompromisso: Código do compromisso. O número do compromisso possibilita customizar parâmetros do serviço sem a necessidade de utilização de novo convênio. Por exemplo: o compromisso “1”,
                tipoCompromisso:  Tipo do compromisso. O tipo do compromisso caracteriza qual a finalidade dos pagamentos/transações. Tipos disponíveis no enum (1=Pagamento Fornecedor┃2=Pagamento Salarios┃3=Autopagamento┃6=Salario Ampliacao Base┃11=Debito Conta),
                parametroTransmissao: Parâmetro de transmissão (TIPO INTEIRO  Min 1┃Max 99)
            },
            informacaoComplementar: tipo STRING (NÃO REQUERIDO),
            tipoServico: Código do tipo de serviço. Códigos disponíveis no enum (aceitos:  10-Pagamentos dividendos┃20-Pagamento fornecedor┃50-Pagamento sinistros segurados┃60-Pagamento despesas viajante em trânsito┃70-Pagamento autorizado┃75-Pagamento credenciados┃80-Pagamento representantes / vendedores autorizados┃90-Pagamento benefícios┃98-Pagamentos diversos),
            accessToken: "ACEESS TOKEN TOTAL BANK",
        }

        metodo POST

        retorno do tipo JSON

        exemplo de retorno com sucesso

        {
            "status": 200,
            "mensagem": "Pagamento Solicitado com sucesso!",
        }

        
// Checar Pagamento

        
    url: /checarPagamento,
        dados: {
            boleto: "TOKEN DO BOLETO SALVO NA GERAÇÃO DO BOLETO"
            accessToken: "ACCESS TOKEN TOTAL BANK",
        }

        metodo POST

        retorno do tipo JSON

        exemplo de retorno com sucesso

        {
            "status": 200,
            dataDaPesquisa: data da consulta ao status do pagamento,
            cpfCnpjBeneficiario: CPF ou CNPJ do beneficiário,
            nomeBeneficiario: Nome do beneficiário,
            cpfCnpjPagador: CPF ou CNPJ do pagador,
            nomePagador: Nome do pagador,
            contaPagadora: Conta debitada,
            descricao: Descrição do pagamento,
            docBanco: Documento banco,
            docEmpresa: Documento empresa,
            dataAgendamento: Data de agendamento do pagamento,
            dataVencimento: Data de vencimento do pagamento,
            formaPagamento: Forma de pagamento,
            nsaCliente: NSA do cliente,
            nsaTotalbank: NSA do Totalbank,
            status: Status do pagamento,
            statusUltimaRemsessa: Status da última remessa,
            valorDocumento: Valor do documento,
            valorPagamento: Valor pago
        }
    
