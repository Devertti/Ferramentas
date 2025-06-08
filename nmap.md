## 🔍 **O que é o Nmap?**  
**Nmap** (*Network Mapper*) é um **software livre e de código aberto** criado por Gordon "Fyodor" Lyon em 1997. É o principal scanner de redes do mundo, usado para:  
- 🕵️‍♂️ **Descobrir dispositivos** em redes (computadores, roteadores, servidores)  
- 🔓 **Identificar portas abertas** e serviços vulneráveis  
- 🖥️ **Detectar sistemas operacionais** e versões de softwares  
- 📜 **Automatizar testes** com scripts personalizados (NSE)  

#### 💡 **Funcionalidades-chave:**  
| Característica | Exemplo de Uso |
|----------------|----------------|
| **Varredura de portas** | Encontrar servidores web (porta 80/443) |
| **Fingerprinting** | Identificar Windows Server 2022 vs Linux |
| **Scripting (NSE)** | Testar vulnerabilidades como SQL Injection |
| **Evasion de firewalls** | Escanear redes protegidas sem ser detectado |

#### ⚙️ **Como funciona?**  
O Nmap envia **pacotes personalizados** para alvos e analisa respostas:  
```bash
nmap -sS 192.168.1.1  # Envia SYN packets para mapear portas
```  
- 🟢 **Host discovery**: Detecta dispositivos ativos via ICMP/ARP  
- 🔵 **Port scanning**: Verifica 65.535 portas TCP/UDP  
- 🟣 **OS detection**: Analisa respostas para "adivinhar" o SO  
- 🟠 **Service detection**: Determina versões exatas (Apache 2.4.52)  

---

  
   ### **Por que usar o Nmap?**  
  É a ferramenta essencial para mapeamento de redes, auditoria de segurança e descoberta de vulnerabilidades. Funciona em Windows, Linux e macOS.
  
  
  ---
  
  ### **📥 Instalação do Nmap**  
  #### **Windows**  
  1. Acesse [nmap.org/download](https://nmap.org/download.html).  
  2. Baixe o instalador `nmap-<versão>-setup.exe`.  
  3. **Importante:** Durante a instalação, marque **Npcap** (driver para captura de pacotes).  
  
  #### **Linux (Debian/Ubuntu)**  
  ```bash
  sudo apt update && sudo apt install nmap
  ```
  
  #### **macOS**  
  ```bash
  brew install nmap  # Via Homebrew
  ```
  
  ---
  
  ### **🔍 Comandos Essenciais**  
  *(Substitua `[alvo]` por IP, domínio ou rede. Ex: `192.168.1.1`, `exemplo.com`, `192.168.1.0/24`)*  
  
  | Comando | Função | Exemplo |
  |---------|--------|---------|
  | **Scan básico** | Portas mais comuns | `nmap [alvo]` |
  | **Scan completo** | Todas as portas (1-65535) | `nmap -p- [alvo]` |
  | **Scan rápido** | 1000 portas comuns + agilidade | `nmap -T4 -F [alvo]` |
  | **Detectar SO** | Identifica sistema operacional | `nmap -O [alvo]` |
  | **Detectar versões** | Versões de serviços (ex: Apache 2.4) | `nmap -sV [alvo]` |
  | **Scan UDP** | Verifica portas UDP (lento!) | `nmap -sU [alvo]` |
  | **Scan sigiloso** | SYN scan (evita logs) | `nmap -sS [alvo]` |
  | **Scripts NSE** | Automação com scripts | `nmap --script [script] [alvo]` |
  
  ---
  
  ### **🚀 Técnicas Avançadas**  
  #### **1. Scan com Scripts (NSE)**  
  - **Exemplo 1:** Detectar vulnerabilidades comuns:  
    ```bash
    nmap --script vuln [alvo]
    ```
  - **Exemplo 2:** Verificar se um servidor HTTP é vulnerável a *Heartbleed*:  
    ```bash
    nmap --script ssl-heartbleed [alvo]
    ```
  
  #### **2. Exportar Resultados**  
  - **Formato normal:** `-oN resultado.txt`  
  - **Formato XML (para importar em ferramentas):** `-oX resultado.xml`  
  ```bash
  nmap -sV -O [alvo] -oN scan.txt
  ```
  
  #### **3. Evitar Detecção**  
  - **Fragmentar pacotes:** `-f`  
  - **Usar decoys (IPs fantasmas):** `-D RND:10`  
  ```bash
  nmap -sS -f -D 192.168.1.100,192.168.1.101 [alvo]
  ```
  
  ---
  
  ### **🛡️ Scripts NSE Mais Úteis**  
  | Categoria | Comando |
  |-----------|---------|
  | **Segurança** | `http-sql-injection`, `ftp-anon` |
  | **Descoberta** | `dns-brute`, `smb-enum-shares` |
  | **Exploração** | `http-shellshock`, `smb-vuln-ms17-010` |
  
  **Exemplo:** Verificar compartilhamentos SMB abertos:  
  ```bash
  nmap --script smb-enum-shares -p 445 [alvo]
  ```
  
  ---
  
  ### **⚠️ Considerações Legais**  
  - **SEMPRE obtenha permissão** antes de escanear redes.  
  - Use apenas em redes que você possui ou tem autorização explícita.  
  - Nmap em redes alheias sem consentimento é **crime** em vários países.
