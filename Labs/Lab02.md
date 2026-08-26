# Lab 02 - Configuração de Trunks

## Objetivo

Configurar um enlace **Trunk** entre dois switches Cisco, permitindo o transporte de múltiplas VLANs entre os equipamentos.

Validar a comunicação entre dispositivos pertencentes à mesma VLAN e verificar o isolamento entre VLANs diferentes.

---

## Topologia

<img width="451" height="200" alt="topologia" src="https://github.com/user-attachments/assets/45f8f538-1e36-46dc-a58d-e849d392d7f4" />


### Conexões

| Dispositivo | Switch | Interface | VLAN |
|---|---|---|---|
| PC1 | SW1 | Fa0/1 | VLAN 10 |
| PC2 | SW1 | Fa0/5 | VLAN 20 |
| PC3 | SW2 | Fa0/1 | VLAN 10 |
| PC4 | SW2 | Fa0/5 | VLAN 20 |

---

## VLANs

Foram configuradas duas VLANs nos switches:

| VLAN | Nome | Interfaces |
|---|---|---|
| 10 | Financeiro | Fa0/1 - Fa0/4 |
| 20 | RH | Fa0/5 - Fa0/8 |

As interfaces destinadas aos computadores foram configuradas como **portas de acesso**.

### VLAN 10 - Financeiro

```cisco
interface range fastEthernet 0/1 - 4
switchport mode access
switchport access vlan 10
```

### VLAN 20 - RH

```cisco
interface range fastEthernet 0/5 - 8
switchport mode access
switchport access vlan 20
```

As configurações foram realizadas nos dois switches.

---

## Endereçamento IP

| Dispositivo | VLAN | Endereço IP |
|---|---:|---|
| PC1 | 10 | 192.168.10.10 |
| PC2 | 20 | 192.168.20.10 |
| PC3 | 10 | 192.168.10.20 |
| PC4 | 20 | 192.168.20.10 |

---

## Configuração do Trunk

O enlace entre **SW1 e SW2** foi configurado como Trunk.

A interface utilizada foi a **GigabitEthernet 0/1** em ambos os switches.

### SW1

```cisco
interface gigabitEthernet 0/1
switchport mode trunk
```

### SW2

```cisco
interface gigabitEthernet 0/1
switchport mode trunk
```

O Trunk permite que múltiplas VLANs sejam transportadas através de um único enlace entre os switches.

---

## IEEE 802.1Q

Os switches utilizam **IEEE 802.1Q (dot1q)** para identificação das VLANs transportadas pelo enlace Trunk.

O padrão 802.1Q adiciona uma **tag VLAN ao quadro Ethernet**, permitindo que os switches identifiquem a qual VLAN o quadro pertence.

---

## Validação

Após a configuração das VLANs e do Trunk, foram realizados testes de comunicação utilizando o comando `ping`.

### PC1 → PC3

**Origem:** PC1 - `192.168.10.10`  
**Destino:** PC3 - `192.168.10.20`  
**VLAN:** 10

**Resultado:** Comunicação realizada com sucesso.

O PC1 conseguiu se comunicar com o PC3, demonstrando que a **VLAN 10 está sendo transportada corretamente através do Trunk** entre SW1 e SW2.

---

### PC2 → PC4

**Origem:** PC2 - `192.168.20.10`  
**Destino:** PC4 - `192.168.20.10`  
**VLAN:** 20

**Resultado:** Comunicação realizada com sucesso.

O PC2 conseguiu se comunicar com o PC4, demonstrando que a **VLAN 20 está sendo transportada corretamente através do Trunk** entre SW1 e SW2.

---

### PC1 → PC2

**Origem:** PC1 - `192.168.10.10`  
**Destino:** PC2 - `192.168.20.10`  
**VLANs:** 10 → 20

**Resultado:** Sem comunicação.

A comunicação não foi estabelecida porque os dispositivos pertencem a **VLANs diferentes** e não existe roteamento entre as VLANs neste laboratório.

---

### PC3 → PC4

**Origem:** PC3 - `192.168.10.20`  
**Destino:** PC4 - `192.168.20.10`  
**VLANs:** 10 → 20

**Resultado:** Sem comunicação.

Assim como no teste anterior, os dispositivos pertencem a VLANs diferentes e não existe roteamento de camada 3 configurado entre elas.

---

## Resultado dos Testes

| Origem | Destino | VLAN | Resultado |
|---|---|---|---|
| PC1 | PC3 | VLAN 10 | ✅ Sucesso |
| PC2 | PC4 | VLAN 20 | ✅ Sucesso |
| PC1 | PC2 | VLAN 10 → VLAN 20 | ❌ Sem comunicação |
| PC3 | PC4 | VLAN 10 → VLAN 20 | ❌ Sem comunicação |

- PC1 e PC3 se comunicaram com sucesso por pertencerem à VLAN 10.
- PC2 e PC4 se comunicaram com sucesso por pertencerem à VLAN 20.
- A comunicação entre VLANs diferentes não ocorreu devido à ausência de roteamento de camada 3.

---

## Conclusão

A configuração do **Trunk** foi realizada com sucesso entre os switches SW1 e SW2.

Os testes demonstraram que:

- A **VLAN 10** foi transportada corretamente entre os switches.
- A **VLAN 20** foi transportada corretamente entre os switches.
- Dispositivos pertencentes à mesma VLAN conseguiram se comunicar mesmo estando conectados a switches diferentes.
- Dispositivos pertencentes a VLANs diferentes permaneceram isolados.
- O Trunk permite o transporte de múltiplas VLANs, mas **não realiza o roteamento entre elas**.

A comunicação entre diferentes VLANs será abordada no próximo laboratório, através da configuração de **Inter-VLAN Routing**.

---

## Arquivos

| Arquivo | Descrição |
|----------|-----------|
| https://drive.google.com/file/d/1ea_ODr7690Ygy9KdB_BWrQDWK_7en88W/view?usp=sharing | Topologia do laboratório desenvolvida no Cisco Packet Tracer. |
| https://drive.google.com/file/d/1kpjFYJzRdy04rPHhjswAkgNbmiLpelbJ/view?usp=sharing | Configuração final do switch 1. |
| https://drive.google.com/file/d/1o3TNk9SaTXIXEUq3vDstV_jdM8LZxH6q/view?usp=sharing | Configuração final do switch 2. |

---

## Evidências

### Topologia

<img width="451" height="200" alt="topologia" src="https://github.com/user-attachments/assets/a5dde3ca-cd7f-4229-82a4-3f1572fb8493" />

### Configuração das VLANs

<img width="524" height="505" alt="SW1 VLAN BRIEF" src="https://github.com/user-attachments/assets/212beaff-0b25-4704-b8af-a996b8752ec3" />
<img width="524" height="500" alt="SW2 VLAN BRIEF" src="https://github.com/user-attachments/assets/4c10c4f3-76b6-41b5-8c8e-3849a734dae2" />


### Configuração do Trunk

<img width="866" height="445" alt="TRUNK sw1 e sw2" src="https://github.com/user-attachments/assets/82beda46-24be-46c3-a0b9-66686f6f7722" />


### Testes de ping 

<img width="658" height="357" alt="testes ping trunk" src="https://github.com/user-attachments/assets/0e0ea8b1-9c91-4a34-80e3-ef11abf0246e" />

---

## Resultado

O enlace Trunk foi configurado com sucesso entre SW1 e SW2.

Os testes demonstraram que:

- O padrão IEEE 802.1Q permitiu o transporte das VLANs entre os switches.
- Dispositivos pertencentes à mesma VLAN conseguiram se comunicar.
- VLANs diferentes permaneceram isoladas.
- O Trunk transporta VLANs, mas não realiza roteamento entre elas.

---

## Conhecimentos Adquiridos

- Criação e configuração de VLANs
- Configuração de portas Access
- Configuração de enlaces Trunk
- Funcionamento do padrão IEEE 802.1Q
- Segmentação lógica de redes
- Transporte de múltiplas VLANs entre switches
- Isolamento entre VLANs
- Validação utilizando comandos Cisco IOS
- Testes básicos de conectividade

---

## Próximo Laboratório

*Lab 03 - Inter-VLAN Routing*

