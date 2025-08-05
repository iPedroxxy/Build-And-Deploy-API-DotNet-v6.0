# 🚀 Build & Deploy SmartZ API - Ambiente de QAS

Este repositório contém o workflow automatizado de **build e deploy** API DotNet 6.0 para ambientes de **Homologação (QAS)**, publicado via **GitHub Actions** diretamente em servidores Windows com IIS.

### ✅ Funcionalidades

- Build do projeto `.csproj` em ambiente `net6.0`
- Substituição dinâmica do `appsettings.json` e string de conexão via secrets
- Publicação via PowerShell em servidor IIS com backup automático da versão anterior
- Suporte para múltiplos clientes e branches
- Verificação de permissão de administrador no runner

### 📦 Estrutura do workflow

- Branch de origem: `hml/cliente`
- Runner: `CI-<CLIENTE>API-HOMOLOGACAO`
- Publicação em: `C:\inetpub\wwwroot\<pastaCliente>`
- Workflow: `.github/workflows/build-and-deploy-api.yml`

### 🔧 Como adicionar novos clientes

1. Crie uma nova branch: `hml/novocliente`
2. No step `Determinar cliente`, adicione:
   ```powershell
   "novocliente" {
     $folder = "NovaApi"
     $connSecret = "CONN_NOVOCLIENTE_HOMOLOG"
   }
