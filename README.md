# 📝 Gerenciador de Tarefas - API .NET com Entity Framework

[![DIO](https://img.shields.io/badge/DIO-%23000000.svg?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxMDAgMTAwIj48cGF0aCBkPSJNNTAgMTBMMTAgNTBsNDAgNDBMOTAgNTB6IiBmaWxsPSIjRkY2QjAwIi8+PC9zdmc+)](https://www.dio.me/)
[![.NET](https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=.net&logoColor=white)](https://dotnet.microsoft.com/)
[![Entity Framework](https://img.shields.io/badge/Entity%20Framework-512BD4?style=for-the-badge&logo=entity-framework&logoColor=white)](https://docs.microsoft.com/ef/)
[![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](https://swagger.io/)

Este projeto foi desenvolvido como parte do desafio da **Trilha .NET** da [Digital Innovation One (DIO)](https://www.dio.me/), com o objetivo de criar uma **API RESTful** para gerenciar tarefas utilizando **ASP.NET Core**, **Entity Framework Core** e **SQL Server** (ou SQLite em ambiente de desenvolvimento).

---

## 🎯 Objetivo

Implementar um sistema completo de **CRUD (Create, Read, Update, Delete)** para gerenciamento de tarefas, permitindo ao usuário:

- Cadastrar novas tarefas
- Listar todas as tarefas
- Buscar tarefas por título, data ou status
- Atualizar tarefas existentes
- Excluir tarefas

---

## 🧱 Modelo de Dados

A entidade principal do sistema é a classe `Tarefa`, com a seguinte estrutura:

```csharp
public class Tarefa
{
    public int Id { get; set; }
    public string Titulo { get; set; }
    public string Descricao { get; set; }
    public DateTime Data { get; set; }
    public StatusTarefa Status { get; set; } // Enum: Pendente, Concluida
}
```

> **StatusTarefa** é um `enum` com os valores: `Pendente` e `Concluida`.

---

## 🌐 Endpoints da API

| Método | Endpoint                     | Descrição                          | Parâmetro(s)     |
|--------|------------------------------|------------------------------------|------------------|
| GET    | `/Tarefa/{id}`               | Obter tarefa por ID                | `id`             |
| PUT    | `/Tarefa/{id}`               | Atualizar tarefa por ID            | `id`, corpo JSON |
| DELETE | `/Tarefa/{id}`               | Deletar tarefa por ID              | `id`             |
| GET    | `/Tarefa/ObterTodos`         | Listar todas as tarefas            | —                |
| GET    | `/Tarefa/ObterPorTitulo`     | Buscar tarefas por título          | `titulo` (query) |
| GET    | `/Tarefa/ObterPorData`       | Buscar tarefas por data            | `data` (query)   |
| GET    | `/Tarefa/ObterPorStatus`     | Buscar tarefas por status          | `status` (query) |
| POST   | `/Tarefa`                    | Criar nova tarefa                  | corpo JSON       |

### Exemplo de corpo da requisição (JSON):

```json
{
  "titulo": "Estudar Entity Framework",
  "descricao": "Completar o módulo de EF Core na DIO",
  "data": "2025-10-22T14:00:00",
  "status": "Pendente"
}
```

---

## 🛠️ Tecnologias Utilizadas

- **ASP.NET Core 8** (Web API)
- **Entity Framework Core** (Code First)
- **SQL Server** (ou **SQLite** para desenvolvimento local)
- **Swagger/OpenAPI** para documentação interativa
- **Migrations** para gerenciamento do banco de dados

---

## 🚀 Como Executar o Projeto

### Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- (Opcional) SQL Server ou ferramenta de banco de dados (ex: SSMS, Azure Data Studio)

### Passos

1. **Clone o repositório**
   ```bash
   git clone https://github.com/seu-usuario/gerenciador-tarefas-dio.git
   cd gerenciador-tarefas-dio
   ```

2. **Restaure as dependências**
   ```bash
   dotnet restore
   ```

3. **Aplique as migrations**
   ```bash
   dotnet ef database update
   ```

4. **Execute a aplicação**
   ```bash
   dotnet run
   ```

5. **Acesse a documentação interativa**
   - Abra seu navegador em: `https://localhost:5001/swagger` (ou `http://localhost:5000/swagger`)
   - Teste os endpoints diretamente pela interface do Swagger!

---

## 📂 Estrutura do Projeto

```
GerenciadorTarefas/
├── Controllers/        # Controladores da API
├── Models/             # Modelos de dados (Tarefa, StatusTarefa)
├── Data/               # Contexto do Entity Framework
├── Properties/         # Configurações de launchSettings
├── appsettings.json    # Configurações de conexão
└── Program.cs          # Configuração do pipeline da aplicação
```
