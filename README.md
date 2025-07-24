# PortScan Detector com iptables + psad

Projeto de detecção e resposta a tentativas de varredura de portas (port scanning) utilizando `iptables` e `psad`, voltado para ambientes Linux com foco em cibersegurança (Blue Team).

---

## 💪 Funcionalidades
- Detecção de port scans com `iptables`
- Análise de logs e resposta automática com `psad`
- Bloqueio automático de IPs maliciosos
- Log de eventos suspeitos via `syslog`
- Fácil configuração e personalização

---

## ⚙️ Requisitos
- Ubuntu/Debian (ou derivados)
- iptables
- psad

Instalação:
```bash
sudo apt update
sudo apt install iptables psad -y
```

---

## 📂 Estrutura do Projeto
```
portscan-detector/
├── portscan-detector.sh
├── README.md
```

---

## ⚡ Execução Rápida
```bash
chmod +x portscan-detector.sh
sudo ./portscan-detector.sh
```

---

## 🔧 Configuração Adicional
Editar o arquivo `/etc/psad/psad.conf`:

```ini
ENABLE_AUTO_IDS          Y;
ENABLE_AUTO_IDS_EMAILS   Y;
EMAIL_ADDRESSES          root@localhost;
HOSTNAME                 Defender;
AUTO_IDS_DANGER_LEVEL    3;
```

Reinicie o psad:
```bash
sudo systemctl restart psad
```

---

## 🔋 Teste
Execute um port scan de outra máquina:
```bash
nmap -sS -p 1-1000 <ip_da_máquina>
```

Verifique os alertas:
```bash
sudo psad --Status
```

---

## Ὢb Salvando regras de firewall (Ubuntu)
```bash
sudo iptables-save > /etc/iptables/rules.v4
```
Se necessário:
```bash
sudo apt install iptables-persistent
```

## 📅 Data do projeto
24/07/2025

---

## ✍️ Autor
Guilherme

---

