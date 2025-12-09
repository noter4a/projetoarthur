# Guia de Instalação no Linux

## Pré-requisitos
- Um servidor Linux (Ubuntu, Debian, CentOS, etc.)
- **Docker** e **Docker Compose** instalados e rodando.

---

## 1. Instalar Docker e Docker Compose (se ainda não tiver)
**Ubuntu / Debian:**
```bash
sudo apt-get update
sudo apt-get install -y docker.io docker-compose
sudo systemctl enable docker
sudo systemctl start docker
```

---

## 2. Preparar o Projeto

### Opção A: Usando Git (Recomendado)
Se você subiu o projeto para o GitHub:
```bash
git clone https://seu-repositorio.git
cd ciklo-geradores
```

### Opção B: Copiando Arquivos Manualmente
Se não usar Git, copie **toda a pasta do projeto** para o servidor usando SCP ou FileZilla.
Certifique-se de que os seguintes arquivos estejam presentes na raiz:
- `Dockerfile`
- `docker-compose.yml`
- `nginx.conf`
- `package.json`
- `package-lock.json`
- Pasta `src`, `public` e outros arquivos de configuração.

---

## 3. Rodar o Projeto

Na pasta raiz do projeto, execute:

```bash
sudo docker-compose up -d --build
```

- `up`: Sobe os serviços.
- `-d`: Roda em segundo plano (detached).
- `--build`: Garante que a imagem seja construída do zero.

---

## 4. Verificar Status

Para ver se está rodando:
```bash
sudo docker ps
```
Você deve ver o container `ciklo-geradores` rodando na porta `0.0.0.0:80`.

Para ver os logs (caso algo dê errado):
```bash
sudo docker logs -f ciklo-geradores
```

---

## 5. Acessar o App

Abra seu navegador e digite o IP do seu servidor:
`http://SEU_IP_DO_SERVIDOR`

O app deve aparecer.

---

## Dicas Adicionais

### Atualizar o App
Se você mudar o código, puxe as alterações e rode novamente:
```bash
git pull origin main
sudo docker-compose up -d --build
```

### Reiniciar forçadamente
```bash
sudo docker-compose down
sudo docker-compose up -d --build
```
