# 🔍 Nmap - Network Mapper

## Instalação

```bash
sudo apt install nmap
Comandos úteis
nmap -sS -sV -T4 -p- -Pn 192.168.1.1
-sS: scan TCP stealth
-sV: detectar versões
-T4: velocidade otimizada
-p-: escanear todas as portas
-Pn: ignora ping
Casos de uso
Identificar portas abertas e serviços
Verificar vulnerabilidades conhecidas (script NSE)

### 3. **Exemplo de writeup (labs/tryhackme/basic-pentesting.md)**

```markdown
# 💣 Writeup: Basic Pentesting (TryHackMe)

## Objetivo

Ganhar acesso root à máquina vulnerável.

## Etapas

- Reconhecimento com Nmap
- Enumeração SMB com enum4linux
- Exploração SSH com credenciais fracas
- Escalada de privilégios com SUID

## Lições aprendidas

- Sempre verificar portas baixas e SMB
- `linpeas.sh` ajuda na escalada de privilégios
