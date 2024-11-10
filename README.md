# desafio_da_calculadora
Criar uma API em C# com front end  react e que se autentique, para realizar 4 operações matemáticas.
Criar uma API em C# com as seguintes features:

1 - Método que recebe dois valores e um parâmetro para indicar a operação matemática desejada: somar, subtrair, multiplicar ou dividir. Essa rota permite acesso somente se o usuário estiver autenticado e ter autorização de acesso;

2 - Autenticação e autorização utilizando JWT e Bearer;

Criar frontend em  React com as seguintes features:


1 - Tela que contém dois campos e quatro botões que executem as operações matemáticas criadas pela API. Ao inserir os valores nesses campos e clicar em um dos botões, deve-se chamar a API para calcular. Após isso, exibir o resultado na tela.

2 - Tela de login que deve chamar a API e obter o token de acesso.

Utilizar Docker e Docker-Compose para ambos os projetos.

Aqui está o conteúdo completo do `README.md` com base nas instruções fornecidas:

---

# Calculator API & Frontend

<img width="369" alt="image" src="https://github.com/user-attachments/assets/89afd3dc-fcd0-488e-af3d-4fa319f45167">


## Descrição

Este projeto consiste em uma API de calculadora com autenticação JWT e um frontend em React que consome essa API. A aplicação permite que usuários autenticados realizem operações matemáticas básicas (soma, subtração, multiplicação e divisão) através de uma interface visual.

## Estrutura do Projeto

- **Backend**: Desenvolvido em C# (.NET 6) com autenticação JWT para segurança dos endpoints.
- **Frontend**: Desenvolvido em React com componentes estilizados usando Bootstrap para uma interface intuitiva e responsiva.

---

## Tecnologias Usadas

- **Backend**:
  - C# (.NET 6)
  - Autenticação JWT
  - ASP.NET Core Web API
  - Docker

- **Frontend**:
  - React
  - Bootstrap
  - Axios
  - Docker

---

## Requisitos

- Docker e Docker Compose instalados na máquina
- Node.js e npm (para desenvolvimento local do frontend)

---

## Configuração e Execução

### 1. Backend

1. **Clone o Repositório**:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio/backend
   ```

2. **Configuração do Backend**:
   No arquivo `appsettings.json`, verifique as configurações de JWT para garantir que correspondem ao frontend. As chaves incluem `Issuer`, `Audience` e `Key` para o token JWT.

   Exemplo:
   ```json
   {
     "Jwt": {
       "Key": "SuperSecretKeyForJwtTokenAuthentication123!",
       "Issuer": "CalculatorApi",
       "Audience": "CalculatorApiUsers"
     }
   }
   ```

3. **Build e Execução com Docker**:
   ```bash
   docker-compose up --build
   ```

   O backend ficará acessível em `https://localhost:32779`.

### 2. Frontend

1. **Navegue para o Diretório do Frontend**:
   ```bash
   cd ../frontend
   O Projeto frontend esta no arquivo zip
   ```

2. **Configuração do Frontend**:
   No arquivo `src/componentes/Calculator.js`, verifique se a URL base da API está configurada corretamente:
   ```javascript
   const response = await axios.get(`https://localhost:32779/api/calculator/${operation}`, {
   ```

3. **Instalação de Dependências e Execução Local**:
   Para testar localmente, execute os comandos:
   ```bash
   npm install
   npm start
   ```

   O frontend ficará acessível em `http://localhost:3000`.

4. **Execução com Docker**:
   Caso deseje rodar o frontend com Docker, use:
   ```bash
   docker-compose up --build
   ```

---

## Funcionalidades

### Backend (API)

- **Autenticação**: Endpoint `/api/auth/login` para autenticação de usuário, que retorna um token JWT.
- **Operações Matemáticas**: Endpoints protegidos para operações matemáticas, como:
  - `GET /api/calculator/add?a=10&b=5`
  - `GET /api/calculator/subtract?a=10&b=5`
  - `GET /api/calculator/multiply?a=10&b=5`
  - `GET /api/calculator/divide?a=10&b=5`

### Frontend

- **Login**: Tela de login para autenticação do usuário, que armazena o token JWT no `localStorage`.
- **Calculadora**: Interface para realizar operações matemáticas após login, mostrando o resultado na tela.

---

## Como Testar

1. Acesse a aplicação frontend em `http://localhost:3000`.
2. Na tela de login, utilize as credenciais:
   - **Usuário**: `admin`
   - **Senha**: `password`
3. Após o login, você será redirecionado para a calculadora.
4. Insira valores e selecione a operação desejada (soma, subtração, multiplicação ou divisão) para ver o resultado.

---

## Problemas Conhecidos

- **Erro de CORS**: Certifique-se de que o backend permite requisições de diferentes origens. No `Program.cs` do backend, adicione as configurações de CORS se necessário.
- **Problemas de SSL no Frontend**: Desative a verificação de certificado SSL ao testar localmente, caso esteja utilizando `https` no backend.

---

## Contribuição

1. Faça um fork do repositório.
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`).
3. Commit suas alterações (`git commit -m 'Adiciona nova feature'`).
4. Push para a branch (`git push origin feature/nova-feature`).
5. Abra um Pull Request.

---

## Licença

Este projeto está sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.

---
