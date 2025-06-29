# 🚀 Node Link Harvester - Coletor de Links Node

**Um script inteligente para coletar e organizar links de binários do Node.js**  
`v1.0` · `Shell Script` · ⏱️ Atualizado em 29/06/2025

## 🌟 Visão Geral

O **Node Link Harvester** é um utilitário em shell script que automatiza a busca, filtragem e organização de links para binários do Node.js diretamente do repositório oficial. Ideal para:

- Administradores de sistemas
- Desenvolvedores que precisam de versões específicas
- Ambientes com restrição de acesso ao npm
- Automação de instalações em múltiplos servidores

## ⚙️ Parâmetros Configuráveis
| Variável         | Valor Padrão               | Descrição                                  |
|------------------|----------------------------|-------------------------------------------|
| `BASE_URL`       | `https://nodejs.org/dist/` | Repositório oficial do Node.js            |
| `EXTENSION`      | `linux-x64.tar.xz`         | Arquitetura e formato do binário          |
| `OUTPUT_FILE`    | `link-node.txt`           | Arquivo de saída com links                |
| `MIN_VERSION`    | `v0.12.14`                 | Versão mínima para inclusão nos resultados|

## 🛠️ Como Usar

### 📦 Como executar rapidamente?

No terminal com sua conta de usuário comum execute:

```bash
wget -qO- https://raw.githubusercontent.com/souza-lb/node-link-harvester/main/get-link-node | bash
```

Após a instalação, reinicie seu terminal ou execute:

```bash
source ~/.bashrc
```

### 📥 Clonar e executar via Git

Para ter controle total sobre o script e personalizá-lo:

```bash
# 1. Clone o repositório
git clone https://github.com/souza-lb/node-link-harvester.git

# 2. Acesse o diretório
cd node-link-harvester

# 3. Dê permissão de execução
chmod +x get-link-node

# 4. Execute o script
./get-link-node

# (Opcional) Mova para seu PATH pessoal
mv get-link-node ~/.local/bin/
```

### ▶️ Execução Básica
```bash
./get-link-node
```

### 📝 Saída Esperada
```
🚀 Iniciando busca em: https://nodejs.org/dist/
🔍 Procurando por arquivos .linux-x64.tar.xz a partir da versão v0.12.14
⏳ Aguarde alguns instantes...
📁 Processando: https://nodejs.org/dist/
📊 Ordenando resultados...

📋 Lista de links ordenados:
  ✅ https://nodejs.org/dist/v18.18.2/node-v18.18.2-linux-x64.tar.xz
  ✅ https://nodejs.org/dist/v20.9.0/node-v20.9.0-linux-x64.tar.xz
  ... [outros links]

✅ Busca concluída!
=================================
📦 Arquivos encontrados:    42
🔧 Após remover duplicatas: 40
💾 Links salvos em:         link-node.txt
=================================
```

### 🔄 Atualizando Parâmetros
Para buscar outras arquiteturas (ex: macOS):
```bash
# Edite o script e modifique:
EXTENSION="darwin-x64.tar.gz"
```

## ⚠️ Dependências

### 📦 Instalação do Curl
O script requer `curl` para funcionar. Instale conforme seu sistema:

| Sistema Operacional      | Comando de Instalação       |
|--------------------------|-----------------------------|
| **Debian/Ubuntu**        | `sudo apt-get install curl` |
| **RHEL/CentOS**          | `sudo yum install curl`     |
| **Arch Linux**           | `sudo pacman -S curl`       |
| **macOS (Homebrew)**     | `brew install curl`         |

## 🧩 Detalhes Técnicos

### 🔍 Algoritmo de Filtragem
1. Coleta todas as tags de versão da página principal
2. Remove versões inferiores à `MIN_VERSION` usando ordenação semântica
3. Valida padrão de URL: `node-vX.X.X-linux-x64.tar.xz`
4. Remove duplicatas e versões inválidas

### 📊 Ordenação Inteligente
As versões são processadas em 3 etapas:
```bash
# 1. Extrai componentes numéricos:
"v18.18.2" → "18 18 2"

# 2. Ordena por: Major > Minor > Patch
sort -k1,1n -k2,2n -k3,3n

# 3. Restaura formato original
```

### ⚡ Otimizações
- Uso de arquivos temporários (`mktemp`) para processamento intermediário
- Contagem precisa de arquivos válidos vs. processados
- Mensagens de status claras com emojis visuais
- Saída formatada para fácil leitura

---

## ❤️ Apoie o Projeto

**Dúvidas, sugestões e contribuições?**  
Leonardo Bruno  
souzalb@proton.me  

**Gostou do projeto e quer realizar uma contribuição voluntária?**  
*(Pode ser o valor de uma xícara de café ou chá...) ☕ 🍵*  

Chave PIX:  
`8dcc7e3c-0c6a-4c6f-a4c0-26a5e62686db`  

Ou utilize o QR Code abaixo:  

<p align="center">
  <img src="images/qrcode-pix.png" alt="QR Code PIX" width="200">
</p>

**Você também pode utilizar o PayPal:**  

[![PayPal](https://img.shields.io/badge/Donate-PayPal-00457C?style=for-the-badge&logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=EQVW5QQ7GBGSY)

<p align="center">
  <img src="images/qrcode-paypal.png" alt="QR Code PayPal" width="200">
</p>

**A utilização deste projeto é livre para alterações e adaptações**  
*Desde que feita a devida referência ao repositório original e seu criador.*
