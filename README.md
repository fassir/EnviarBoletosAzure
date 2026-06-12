<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=200&color=gradient&customColorList=0:1F9BD4,50:2E75B6,100:16265F&text=EnviarBoletosAzure&fontColor=ffffff&fontSize=38&fontAlignY=35&desc=Sistema%20de%20Gera%C3%A7%C3%A3o%20e%20Envio%20de%20Boletos%20%7C%20C%23%20%2B%20Azure%20Functions&descAlignY=55&descSize=15&animation=twinkling" width="100%" />

[![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)](https://docs.microsoft.com/pt-br/dotnet/csharp/)
[![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![Azure Functions](https://img.shields.io/badge/Azure%20Functions-0062AD?style=for-the-badge&logo=azurefunctions&logoColor=white)](https://azure.microsoft.com/pt-br/products/functions/)
[![Azure](https://img.shields.io/badge/Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com/)

[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/CSS)
[![Serverless](https://img.shields.io/badge/arquitetura-serverless-blue?style=flat-square)]()
[![Status](https://img.shields.io/badge/status-ativo-brightgreen?style=flat-square)]()

</div>

---

## 📋 Sobre o Projeto

O **EnviarBoletosAzure** é um sistema completo de **geração e envio de boletos bancários** utilizando arquitetura **serverless na nuvem Azure**. O projeto combina um frontend moderno em HTML/CSS/JavaScript com um backend robusto em **Azure Functions (.NET / C#)**, demonstrando integração de sistemas financeiros na nuvem Microsoft Azure.

O sistema permite a geração de boletos com código de barras, validação dos dados financeiros e envio automatizado — tudo orquestrado por funções serverless que escalam automaticamente conforme a demanda.

---

<div align="center">

## 🛠️ Stack de Tecnologias

[![My Skills](https://skillicons.dev/icons?i=cs,dotnet,azure,js,html,css&theme=dark)](https://skillicons.dev)

</div>

| Camada | Tecnologia | Versão | Papel |
|---|---|---|---|
| **Frontend** | HTML5 + CSS3 + JavaScript | — | Interface de geração de boletos |
| **Código de barras** | barcode.js | — | Geração visual do código de barras |
| **Backend** | Azure Functions | v4 (.NET) | Processamento serverless |
| **Linguagem backend** | C# | .NET 6/7 | Lógica de negócio |
| **Nuvem** | Microsoft Azure | — | Hospedagem e infraestrutura |

---

## 📁 Estrutura do Repositório

```
EnviarBoletosAzure/
│
├── Front/                          # Frontend da aplicação
│   ├── index.html                  # Página principal de geração de boletos
│   ├── css/
│   │   └── style.css               # Estilos da interface
│   └── js/
│       ├── barcode.js              # Biblioteca de geração de código de barras
│       └── script.js               # Lógica do frontend (integração com API)
│
└── fnGeradorBoletos/               # Azure Function (projeto C# .NET)
    ├── fnGeradorBoletos.csproj     # Projeto .NET
    ├── local.settings.json         # Configurações locais (desenvolvimento)
    ├── GeradorBoletos.cs           # Function principal
    ├── Models/
    │   └── Boleto.cs               # Model de dados do boleto
    └── host.json                   # Configuração do host Azure Functions
```

---

## 🏗️ Arquitetura do Sistema

```
┌─────────────────────────────────────────────────────────────────────┐
│                    ARQUITETURA DO SISTEMA                           │
│                                                                     │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │                    FRONTEND (Browser)                         │  │
│  │                                                               │  │
│  │  ┌─────────────┐  ┌───────────────┐  ┌──────────────────┐   │  │
│  │  │  index.html │  │  barcode.js   │  │   script.js      │   │  │
│  │  │  (formulário│  │  (geração de  │  │  (integração     │   │  │
│  │  │   de dados) │  │  código barr.)│  │   com API)       │   │  │
│  │  └─────────────┘  └───────────────┘  └────────┬─────────┘   │  │
│  └───────────────────────────────────────────────┼─────────────┘  │
│                                                   │ HTTP POST       │
│                                                   ▼                 │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │               AZURE FUNCTIONS (Backend C# .NET)               │  │
│  │                                                               │  │
│  │  ┌─────────────────────────────────────────────────────────┐ │  │
│  │  │              fnGeradorBoletos                           │ │  │
│  │  │                                                         │ │  │
│  │  │  1. Recebe dados do boleto (JSON)                       │ │  │
│  │  │  2. Valida campos obrigatórios                          │ │  │
│  │  │  3. Gera código de barras bancário                      │ │  │
│  │  │  4. Processa dados financeiros                          │ │  │
│  │  │  5. Envia boleto (e-mail / retorno)                     │ │  │
│  │  └─────────────────────────────────────────────────────────┘ │  │
│  └───────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 💻 Frontend — Interface de Geração de Boletos

<details>
<summary>🌐 <strong>index.html — Formulário de Dados</strong></summary>

<br>

O frontend exibe um formulário para inserção dos dados necessários à geração do boleto:

```html
<!-- Front/index.html -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Gerador de Boletos</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div class="container">
        <h1>Gerador de Boletos Bancários</h1>
        <form id="formBoleto">
            <input type="text" id="cedente" placeholder="Nome do Cedente" required>
            <input type="text" id="cpfCnpj" placeholder="CPF/CNPJ" required>
            <input type="number" id="valor" placeholder="Valor (R$)" required>
            <input type="date" id="vencimento" required>
            <input type="text" id="sacado" placeholder="Nome do Sacado" required>
            <button type="submit">Gerar Boleto</button>
        </form>
        <div id="resultado"></div>
    </div>
    <script src="js/barcode.js"></script>
    <script src="js/script.js"></script>
</body>
</html>
```

</details>

<details>
<summary>📊 <strong>barcode.js + script.js — Código de Barras e Integração</strong></summary>

<br>

```javascript
// Front/js/script.js
document.getElementById('formBoleto').addEventListener('submit', async (e) => {
    e.preventDefault();

    const boleto = {
        cedente: document.getElementById('cedente').value,
        cpfCnpj: document.getElementById('cpfCnpj').value,
        valor: parseFloat(document.getElementById('valor').value),
        vencimento: document.getElementById('vencimento').value,
        sacado: document.getElementById('sacado').value
    };

    const response = await fetch('/api/fnGeradorBoletos', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(boleto)
    });

    const data = await response.json();

    // Exibir código de barras gerado
    if (data.codigoBarras) {
        JsBarcode('#barcode', data.codigoBarras, {
            format: 'CODE128',
            width: 2,
            height: 80
        });
    }
});
```

</details>

---

## ⚡ Azure Function — Backend C#

<details>
<summary>🔧 <strong>GeradorBoletos.cs — Function Principal</strong></summary>

<br>

```csharp
// fnGeradorBoletos/GeradorBoletos.cs
using Microsoft.Azure.Functions.Worker;
using Microsoft.Azure.Functions.Worker.Http;
using Microsoft.Extensions.Logging;
using System.Net;
using System.Text.Json;

namespace fnGeradorBoletos
{
    public class GeradorBoletos
    {
        private readonly ILogger _logger;

        public GeradorBoletos(ILoggerFactory loggerFactory)
        {
            _logger = loggerFactory.CreateLogger<GeradorBoletos>();
        }

        [Function("fnGeradorBoletos")]
        public async Task<HttpResponseData> Run(
            [HttpTrigger(AuthorizationLevel.Anonymous, "post")] HttpRequestData req)
        {
            _logger.LogInformation("Processando requisição de geração de boleto.");

            var body = await req.ReadAsStringAsync();
            var boleto = JsonSerializer.Deserialize<BoletoModel>(body);

            // Validar dados
            if (boleto == null || boleto.Valor <= 0)
            {
                var badResponse = req.CreateResponse(HttpStatusCode.BadRequest);
                await badResponse.WriteStringAsync("Dados do boleto inválidos.");
                return badResponse;
            }

            // Gerar código de barras (simplificado)
            var codigoBarras = GerarCodigoBarras(boleto);

            var response = req.CreateResponse(HttpStatusCode.OK);
            await response.WriteAsJsonAsync(new
            {
                codigoBarras,
                mensagem = "Boleto gerado com sucesso!",
                vencimento = boleto.Vencimento
            });

            return response;
        }

        private static string GerarCodigoBarras(BoletoModel boleto)
        {
            // Lógica de geração do código de barras bancário
            return $"34191{boleto.Valor:0000000000}00001{DateTime.Now:yyyyMMdd}";
        }
    }
}
```

</details>

---

## 🚀 Como Executar Localmente

### Pré-requisitos

```bash
# Instalar .NET SDK
winget install Microsoft.DotNet.SDK.7

# Instalar Azure Functions Core Tools
npm install -g azure-functions-core-tools@4 --unsafe-perm true

# Verificar instalação
func --version
```

### Executando a Azure Function localmente

```bash
# Navegar até o projeto
cd fnGeradorBoletos

# Restaurar dependências
dotnet restore

# Executar a function localmente
func start
# Azure Functions Core Tools
# Functions:
#   fnGeradorBoletos: [POST] http://localhost:7071/api/fnGeradorBoletos
```

### Executando o Frontend

```bash
# Instalar live-server (ou usar qualquer HTTP server)
npm install -g live-server

cd Front
live-server
# Serving at http://localhost:8080
```

### Testando a API

```bash
# Teste via curl
curl -X POST http://localhost:7071/api/fnGeradorBoletos \
  -H "Content-Type: application/json" \
  -d '{
    "cedente": "Empresa Exemplo Ltda",
    "cpfCnpj": "12.345.678/0001-90",
    "valor": 150.00,
    "vencimento": "2024-12-31",
    "sacado": "Cliente Teste"
  }'
```

---

## ☁️ Deploy no Azure

```bash
# Login no Azure
az login

# Criar Resource Group
az group create --name rg-boletos --location brazilsouth

# Criar Storage Account (necessário para Functions)
az storage account create \
  --name stboletos \
  --resource-group rg-boletos \
  --location brazilsouth \
  --sku Standard_LRS

# Criar Function App
az functionapp create \
  --resource-group rg-boletos \
  --consumption-plan-location brazilsouth \
  --runtime dotnet-isolated \
  --functions-version 4 \
  --name fn-gerador-boletos \
  --storage-account stboletos

# Deploy da function
func azure functionapp publish fn-gerador-boletos
```

---

## 👤 Autor

<div align="center">

| | |
|---|---|
| **Nome** | Fabio Piassi |
| **LinkedIn** | [linkedin.com/in/fabio-piassi](https://linkedin.com/in/fabio-piassi) |
| **GitHub** | [github.com/fassir](https://github.com/fassir) |

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&section=footer&height=120&color=gradient&customColorList=0:16265F,50:2E75B6,100:1F9BD4" width="100%" />

*Sistema serverless de geração e envio de boletos bancários com C# e Azure Functions*

</div>
