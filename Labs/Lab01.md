# Lab01 - Criação de VLANs

## Objetivo

Implementar a segmentação lógica da rede por meio da criação de VLANs em um switch Cisco, atribuindo portas de acesso a cada VLAN e validando o isolamento entre elas.

---

## Conceitos Trabalhados

- VLAN
- Segmentação de Redes
- Domínio de Broadcast
- Access Ports
- Switching
- IEEE 802.1Q (Introdução)

---

## Topologia

> <img width="384" height="258" alt="topologia" src="https://github.com/user-attachments/assets/08074def-3157-43c1-97d0-bc1b6b87ad3a" />

---

## Endereçamento

| Equipamento | Interface | Endereço IP |
|-------------|-----------|-------------|
| PC1 | FastEthernet0 | 192.168.10.10/24 |
| PC2 | FastEthernet0 | 192.168.10.20/24 |
| PC3 | FastEthernet0 | 192.168.20.10/24 |
| PC4 | FastEthernet0 | 192.168.20.20/24 |

> Neste laboratório não foi configurado gateway padrão, pois não haverá comunicação entre VLANs.

---

## Configurações Realizadas

- Criação da VLAN 10 (Financeiro)
- Criação da VLAN 20 (RH)
- Associação das portas Fa0/1 e Fa0/2 à VLAN 10
- Associação das portas Fa0/3 e Fa0/4 à VLAN 20
- Salvamento da configuração

---

## Comandos Utilizados

```text
enable
configure terminal

vlan 10
 name Financeiro

vlan 20
 name RH

interface range fa0/1 - 2
 switchport mode access
 switchport access vlan 10

interface range fa0/3 - 4
 switchport mode access
 switchport access vlan 20

end

copy running-config startup-config
```

---

## Comandos de Validação

```text
show vlan brief
show running-config
```

---

## Evidências

### Topologia

- <img width="384" height="258" alt="topologia" src="https://github.com/user-attachments/assets/3e9449f8-28f1-48d0-abfa-b70e7c1580a3" />


### Configuração

- <img width="504" height="135" alt="show vlan brief" src="https://github.com/user-attachments/assets/9ef34d3f-4d5b-431f-8394-b3788b7423e3" />


### Testes de Comunicação

- <img width="521" height="481" alt="ping pc1 - pc2" src="https://github.com/user-attachments/assets/96b82bd9-6bd9-4b2c-94af-b09a7b40e75d" />

- <img width="527" height="501" alt="ping pc3 - pc4" src="https://github.com/user-attachments/assets/fd0f7049-b4f0-447d-9705-69cafc843cc5" />

- <img width="525" height="500" alt="ping pc1 - pc3" src="https://github.com/user-attachments/assets/a5a8d47f-2c8d-4b81-8419-0acc6d387b9a" />

- <img width="524" height="503" alt="ping pc2 - pc4" src="https://github.com/user-attachments/assets/c2168ca9-7a49-4279-b77d-1775c328166a" />

---

## Arquivos

| Arquivo | Descrição |
|----------|-----------|
| https://drive.google.com/file/d/1DNM2U5gFz_t0cdOHps-GK4_1skd1OCAL/view?usp=sharing | Topologia do laboratório desenvolvida no Cisco Packet Tracer. |
| https://drive.google.com/file/d/14e5-JnKeRfdrDt-L6Ao1MWLPprFc0m9e/view?usp=sharing | Configuração final do switch. |

---

## Resultado

Todos os objetivos do laboratório foram concluídos com sucesso.

- VLANs criadas.
- Portas atribuídas às VLANs corretas.
- Configuração salva.
- Comunicação entre dispositivos da mesma VLAN validada.
- Comunicação entre VLANs bloqueada conforme esperado.

---

## Conhecimentos Adquiridos

- Conceito de VLAN e sua utilização para segmentação lógica de redes.
- Diferença entre uma rede física e uma rede lógica.
- Associação de portas de acesso (Access Ports) a VLANs.
- Funcionamento dos domínios de broadcast.
- Necessidade de um dispositivo de Camada 3 para permitir comunicação entre VLANs.

---

## Próximo Laboratório

**Lab02 - Configuração de Trunks (802.1Q)** https://github.com/Bezalcs/CCNA-Labs/blob/main/Labs/Lab02.md
