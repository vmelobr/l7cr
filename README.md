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
            valor,
            accessToken
        }

        metodo POST

        retorno do tipo JSON

        exemplo de retorno com sucesso

        {
            "status": 200,
            "token": 544545545414545454545,
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
