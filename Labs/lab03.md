# Lab03 – Inter-VLAN Routing

## Objetivo
Implementar a comunicação entre dispositivos de diferentes VLANs utilizando um **switch Layer 3 (SW1)** como roteador, conectado a dois switches de acesso (SW2 e SW3). Validar o funcionamento do **Inter-VLAN Routing** por meio de testes de conectividade.

---

## Conceitos Trabalhados
- Inter-VLAN Routing
- Switch Layer 3
- SVI (Switch Virtual Interface)
- Trunk 802.1Q
- IP Routing

---

## Topologia
<img width="448" height="268" alt="topologia" src="https://github.com/user-attachments/assets/59427504-e8c1-499c-bb20-5a732357965c" />

---

## Endereçamento IP

| Dispositivo | VLAN | Endereço IP | Gateway |
|-------------|------|-------------|---------|
| PC0 | 10 (RH) | 192.168.10.10/24 | 192.168.10.1 |
| PC1 | 10 (RH) | 192.168.10.20/24 | 192.168.10.1 |
| PC2 | 20 (Financeiro) | 192.168.20.10/24 | 192.168.20.1 |
| PC3 | 20 (Financeiro) | 192.168.20.20/24 | 192.168.20.1 |
| PC4 | 10 (RH) | 192.168.10.30/24 | 192.168.10.1 |
| PC5 | 10 (RH) | 192.168.10.40/24 | 192.168.10.1 |
| PC6 | 20 (Financeiro) | 192.168.20.30/24 | 192.168.20.1 |
| PC7 | 20 (Financeiro) | 192.168.20.40/24 | 192.168.20.1 |
| SW1 (L3) | VLAN 10 | 192.168.10.1/24 | — |
| SW1 (L3) | VLAN 20 | 192.168.20.1/24 | — |

---

## Configurações Realizadas

### SW2 e SW3 (Switches de Acesso)
- Criação das VLANs 10 e 20
- Associação das portas dos hosts às VLANs (modo access)
- Configuração da porta Gi0/1 como trunk para o SW1

### SW1 (Switch Layer 3)
- Criação das VLANs 10 e 20
- Configuração das interfaces VLAN (SVI) com IPs
- Configuração das portas Gi0/1 e Gi0/2 como trunk
- Habilitação do `ip routing`

---

## Comandos Utilizados

### SW1
```cisco
interface vlan 10
 ip address 192.168.10.1 255.255.255.0
 no shutdown

interface vlan 20
 ip address 192.168.20.1 255.255.255.0
 no shutdown

ip routing 
```

### SW2/SW3
```cisco
vlan 10
 name RH

vlan 20
 name Financeiro

interface range fa0/1 - 2
 switchport mode access
 switchport access vlan 10

interface range fa0/3 - 4
 switchport mode access
 switchport access vlan 20

interface gi0/1
 switchport mode trunk
 ```
## Comandos de Validação
```
show vlan brief
show ip interface brief
show ip route
show interfaces trunk
 ```

 ## Evidências

### Configuração das VLANs
<img width="949" height="502" alt="show vlan brief" src="https://github.com/user-attachments/assets/a926428a-ed7c-4b7c-8dce-e26ba1b98b6d" />

### Configuração dos Trunks
<img width="525" height="502" alt="interface trunk" src="https://github.com/user-attachments/assets/629accc7-978e-42b8-abce-e75383e7d610" />

### Configuração das SVIs no SW1
<img width="527" height="503" alt="ip interfaces" src="https://github.com/user-attachments/assets/c5d0ecba-2f60-4d9a-9a83-bb5a98004d5c" />
<img width="520" height="506" alt="ip route" src="https://github.com/user-attachments/assets/9210aa2c-6380-4ffd-9ef3-8457ad54f0bd" />


### Testes de Ping
pings na mesma VLAN
<img width="956" height="500" alt="pings mesma vlan" src="https://github.com/user-attachments/assets/5e8c65c3-e45c-4d49-b4d2-0e02e060c8da" />

 pings entre VLANs
 <img width="949" height="502" alt="ping inter vlan" src="https://github.com/user-attachments/assets/8550d841-104b-4561-8390-18a10fd996e4" />

## Resultado
- Comunicação entre hosts da mesma VLAN validada ✅
- Comunicação entre hosts de VLANs diferentes validada via SW1 ✅
- Roteamento entre VLANs funcionando corretamente ✅

## Conclusão

A configuração do **Inter-VLAN Routing** foi realizada com sucesso utilizando o switch SW1 em camada 3.

Os testes demonstraram que:

- A **VLAN 10 (RH)** foi criada e configurada corretamente nos switches de acesso.
- A **VLAN 20 (Financeiro)** foi criada e configurada corretamente nos switches de acesso.
- Dispositivos pertencentes à mesma VLAN conseguiram se comunicar mesmo estando conectados a switches diferentes.
- Dispositivos pertencentes a VLANs diferentes conseguiram se comunicar através do **roteamento no SW1 Layer 3**.
- O comando **ip routing** habilitado no SW1 permitiu a comunicação entre redes distintas.

---

## Arquivos

| Arquivo | Descrição |
|----------|-----------|
| arquivo packet tracer lab3 | Topologia do laboratório desenvolvida no Cisco Packet Tracer. |
| arquivo txt sw1 | Configuração final do switch SW1 (Layer 3). |
| arquivo txt sw2 | Configuração final do switch SW2. |
| arquivo txt sw3 | Configuração final do switch SW3. |


## Conhecimentos Adquiridos
- Configuração de SVIs em switches Layer 3
- Diferença entre switches de acesso e switches de camada 3
- Importância dos trunks para transportar múltiplas VLANs
- Funcionamento do Inter-VLAN Routing em cenários reais

## Troubleshooting
-  Sem comunicação entre VLANs → verificar se ip routing está habilitado no SW1
- Hosts não pingam o gateway → conferir se o gateway padrão está configurado corretamente nos PCs
- Trunk não ativo → usar show interfaces trunk para validar
- VLAN não aparece → confirmar se foi criada em todos os switches 

## Próximo Laboratório

*Lab 04 - DHCP*

