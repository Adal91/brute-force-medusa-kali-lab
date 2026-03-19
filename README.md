Simulação de Ataque Brute Force com Medusa no Kali Linux

Este projeto demonstra um cenário de auditoria de segurança utilizando ferramentas do Kali Linux para simular ataques de força bruta em serviços vulneráveis.

O objetivo é compreender como esses ataques funcionam e apresentar medidas de mitigação para proteger sistemas contra esse tipo de vulnerabilidade.

**Objetivos:**
Compreender ataques de Brute Force
Utilizar ferramentas de auditoria de segurança
Demonstrar comandos da ferramenta Medusa
Identificar vulnerabilidades comuns
Propor medidas de mitigação

**Ferramentas Utilizadas:**
Kali Linux
Medusa
Metasploitable 2
Damn Vulnerable Web Application
Nmap

**Ambiente do Laboratório**
O ambiente simulado consiste em duas máquinas:
| Máquina          | Função             |
| ---------------- | ------------------ |
| Kali Linux       | Máquina atacante   |
| Metasploitable 2 | Máquina vulnerável |

**Configuração de rede:**
Rede Host-Only
IP atacante: 192.168.56.102
IP alvo: 192.168.56.101

**Descoberta de Serviços com Nmap**

Antes de iniciar os ataques, é importante identificar quais serviços estão ativos.

Comando utilizado:
nmap -sV 192.168.56.101
**Exemplo de serviços encontrados:**
FTP
SSH
SMB
HTTP
Explicação dos parâmetros:

Parâmetro	Função
-h	IP do alvo
-u	usuário
-P	lista de senhas
-M	serviço alvo
**Ataque em Formulário Web (DVWA)**

Neste cenário, o ataque é direcionado ao formulário de login de uma aplicação web vulnerável.

**Comando utilizado:**
medusa -h 192.168.56.101 -u admin -P passwords.txt -M http
O objetivo é testar múltiplas combinações de senha para encontrar credenciais válidas.

**Password Spraying em SMB**

Neste ataque são testadas senhas comuns em vários usuários para identificar acessos válidos.

Comando utilizado:

medusa -h 192.168.56.101 -U users.txt -P passwords.txt -M smbnt

Arquivos utilizados:

users.txt

admin
root
user
test
msfadmin

passwords.txt

123456
admin
password
12345678
qwerty
msfadmin

**Riscos de Ataques de Força Bruta**

Ataques desse tipo podem permitir:
acesso não autorizado
vazamento de dados
controle de servidores
comprometimento de sistemas

**Medidas de Mitigação**

Para evitar ataques de força bruta, recomenda-se:
✔ utilização de senhas fortes
✔ autenticação em dois fatores (2FA)
✔ limitação de tentativas de login
✔ bloqueio temporário de IP
✔ monitoramento de logs
✔ utilização de CAPTCHA em formulários

**Conclusão**

Este projeto demonstrou como ferramentas de segurança podem ser utilizadas para identificar vulnerabilidades em ambientes controlados.
A compreensão desses ataques é fundamental para profissionais de segurança da informação, pois permite implementar medidas eficazes de proteção.
