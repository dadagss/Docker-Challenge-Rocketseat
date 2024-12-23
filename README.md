1. **Dockerfile:**
   - Foi criado um Dockerfile utilizando uma imagem base leve e otimizada (ex.: Alpine Linux).
   - O Dockerfile utiliza múltiplos estágios para reduzir o tamanho da imagem final.

2. **Docker Compose:**
   - Dois serviços configurados:
     - Um container para a aplicação (ex.: backend ou frontend).
     - Um container para o banco de dados (MySQL, PostgreSQL, MongoDB, etc.).
   - Configuração de variáveis de ambiente para flexibilizar o deploy.

3. **Volumes:**
   - Foram configurados volumes persistentes para armazenar dados do banco de forma segura e permanente.

4. **Rede Customizada:**
   - Foi criada uma rede Docker isolada para permitir comunicação entre os containers de forma segura.

5. **Segurança:**
   - O banco de dados está configurado com um usuário dedicado à aplicação, em vez de usar o usuário root.
   - Senhas e outros dados sensíveis foram configurados através de variáveis de ambiente ou arquivos externos (.env).

---

## Como Executar o Projeto

### 1. Clonar o Repositório
bash
$ git clone <URL-do-repositório>
$ cd <nome-do-diretório>
```

### 2. Configurar Variáveis de Ambiente
Crie um arquivo `.env` na raiz do projeto com os seguintes valores:
```env
APP_PORT=8080
DB_HOST=db
DB_PORT=3306
DB_USER=usuario
DB_PASSWORD=senha
DB_NAME=nome_do_banco
```

### 3. Iniciar os Containers
Suba o ambiente utilizando o Docker Compose:
```bash
$ docker-compose up -d
```

### 4. Verificar os Containers Ativos
```bash
$ docker ps
```

### 5. Testar a Aplicação
- **Aplicativo:** Acesse `http://localhost:8080` no navegador.
- **Banco de Dados:** Conecte-se ao banco usando ferramentas como MySQL Workbench ou pgAdmin com as credenciais do `.env`.

---

## Estrutura do Docker Compose
```yaml
version: '3.8'
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - \${APP_PORT}:8080\
    environment:
      - DB_HOST=${DB_HOST}
      - DB_PORT=${DB_PORT}
      - DB_USER=${DB_USER}
      - DB_PASSWORD=${DB_PASSWORD}
      - DB_NAME=${DB_NAME}
    networks:
      - app_network

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: ${DB_NAME}
      MYSQL_USER: ${DB_USER}
      MYSQL_PASSWORD: ${DB_PASSWORD}
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - app_network

volumes:
  db_data:

networks:
  app_network:
```

---

## Resultados Esperados
- **Ambiente Multi-Container:** Configurado e funcionando com serviço da aplicação e banco de dados.
- **Persistência de Dados:** Garantida através de volumes configurados.
- **Comunicação Segura:** Rede customizada configurada para isolar os containers.
- **Flexibilidade:** Variáveis de ambiente configuradas para ajustar as configurações sem alterar o código.
- **Segurança:** Evitada a utilização do usuário root no banco de dados.

---

## Conclusão
Este desafio proporcionou a configuração de um ambiente Docker Compose seguindo boas práticas de segurança e flexibilidade.
O uso de volumes, redes personalizadas e variáveis de ambiente garantiu uma solução robusta e pronta para deploy.

---

Feito com 💜 por Rocketseat 👋

return 0;---

## Estrutura do Projeto
1. **Dockerfile:**
   - Foi criado um Dockerfile utilizando uma imagem base leve e otimizada (ex.: Alpine Linux).
   - O Dockerfile utiliza múltiplos estágios para reduzir o tamanho da imagem final.

2. **Docker Compose:**
   - Dois serviços configurados:
     - Um container para a aplicação (ex.: backend ou frontend).
     - Um container para o banco de dados (MySQL, PostgreSQL, MongoDB, etc.).
   - Configuração de variáveis de ambiente para flexibilizar o deploy.

3. **Volumes:**
   - Foram configurados volumes persistentes para armazenar dados do banco de forma segura e permanente.

4. **Rede Customizada:**
   - Foi criada uma rede Docker isolada para permitir comunicação entre os containers de forma segura.

5. **Segurança:**
   - O banco de dados está configurado com um usuário dedicado à aplicação, em vez de usar o usuário root.
   - Senhas e outros dados sensíveis foram configurados através de variáveis de ambiente ou arquivos externos (.env).

---

## Como Executar o Projeto

### 1. Clonar o Repositório
```bash
$ git clone <URL-do-repositório>
$ cd <nome-do-diretório>
```

### 2. Configurar Variáveis de Ambiente
Crie um arquivo `.env` na raiz do projeto com os seguintes valores:
```env
APP_PORT=8080
DB_HOST=db
DB_PORT=3306
DB_USER=usuario
DB_PASSWORD=senha
DB_NAME=nome_do_banco
```

### 3. Iniciar os Containers
Suba o ambiente utilizando o Docker Compose:
```bash
$ docker-compose up -d
```

### 4. Verificar os Containers Ativos
```bash
$ docker ps
```

### 5. Testar a Aplicação
- **Aplicativo:** Acesse `http://localhost:8080` no navegador.
- **Banco de Dados:** Conecte-se ao banco usando ferramentas como MySQL Workbench ou pgAdmin com as credenciais do `.env`.

---

## Estrutura do Docker Compose
```yaml
version: '3.8'
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - \${APP_PORT}:8080\
    environment:
      - DB_HOST=${DB_HOST}
      - DB_PORT=${DB_PORT}
      - DB_USER=${DB_USER}
      - DB_PASSWORD=${DB_PASSWORD}
      - DB_NAME=${DB_NAME}
    networks:
      - app_network

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: ${DB_NAME}
      MYSQL_USER: ${DB_USER}
      MYSQL_PASSWORD: ${DB_PASSWORD}
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - app_network

volumes:
  db_data:

networks:
  app_network:
```

---

## Resultados Esperados
- **Ambiente Multi-Container:** Configurado e funcionando com serviço da aplicação e banco de dados.
- **Persistência de Dados:** Garantida através de volumes configurados.
- **Comunicação Segura:** Rede customizada configurada para isolar os containers.
- **Flexibilidade:** Variáveis de ambiente configuradas para ajustar as configurações sem alterar o código.
- **Segurança:** Evitada a utilização do usuário root no banco de dados.

---

## Conclusão
Este desafio proporcionou a configuração de um ambiente Docker Compose seguindo boas práticas de segurança e flexibilidade.
O uso de volumes, redes personalizadas e variáveis de ambiente garantiu uma solução robusta e pronta para deploy.

---

Feito com 💜 por Rocketseat 👋

return 0;