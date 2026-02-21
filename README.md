# React + vite + Docker + Dev Container Template

## Sobre este repositório

Este repositório é um template para desenvolvimento de aplicações React utilizando Docker e Dev Container. O objetivo é fornecer um ambiente de desenvolvimento padronizado, isolado e pronto para uso, eliminando problemas de incompatibilidade entre versões do Node e dependências instaladas localmente.

Com este template qualquer desenvolvedor precisa apenas ter o **WSL** e o **Docker** instalados para começar a trabalhar, sem necessidade de instalar o Node.js ou qualquer outra dependência diretamente na máquina.

---

## Pré-requisitos

- WSL instalado
- Docker instalado e funcionando — veja o guia [Como instalar o Docker no Windows | 2026 | Guia passo a passo](https://youtu.be/qrvx6ivyrQw)
- VSCode com a extensão **Dev Containers** (ms-vscode-remote.remote-containers)

---

## Passo a passo

### 1. Fazer fork deste repositório

Clique em **"Fork"** no GitHub e clone o repositório criado:

```bash
git clone https://github.com/seu-usuario/seu-repo.git
cd seu-repo
```

### 2. Criar o projeto Vite

```bash
npm create vite@latest . -- --template react
```

### 3. Abra o VSCODE

```bash
code .
```

### 4. Subir o container

Usando o terminal do vscode

```bash
docker-compose up --build -d
```

### 5. Faça o teste 

✅ Acessa em **http://localhost:5173**


### 6. Instale a extensão Dev Containers 

`Ctrl+Shift+X` → pesquise **Dev Containers**

### 7. Abrir no Dev Container

`Ctrl+Shift+P` → **Reopen in Container**

✅ Acessa em **http://localhost:5173**

A partir daqui tudo pelo terminal do VSCode!


### 8. Habilitar hot reload

Ao alterar o código você vai notar que a página não atualiza automaticamente. Isso acontece porque o Vite por padrão usa eventos nativos do sistema operacional para detectar mudanças, e esses eventos não chegam até o container no Windows.

Substitui o conteúdo do `vite.config.js` por:

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  server: {
    watch: {
      usePolling: true,
    },
    host: true,
  },
})
```

Reinicia o container usando um terminal **fora do container** na pasta do projeto:

```bash
docker-compose up --build -d
```

✅ Agora o hot reload está funcionando!
---

## Comandos úteis

| Comando | Descrição |
|---|---|
| `docker-compose up -d` | Sobe o container em background |
| `docker-compose up --build -d` | Rebuilda e sobe o container |
| `docker-compose down` | Para e remove o container |
| `npm install pacote` | Instala uma dependência dentro do container |

---

## Estrutura do repositório

```
.
├── Dockerfile
├── docker-compose.yml
├── .devcontainer/
│   └── devcontainer.json
└── README.md
```

---

## Autor

Criado por **Fernando Leonid**, professor e desenvolvedor apaixonado por compartilhar conhecimento.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/fernandoleonid/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/fernandoleonid)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@fernandoleonid)