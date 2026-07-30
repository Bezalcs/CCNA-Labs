# Lab00 - Configuração Inicial de Switch e Roteador

## Objetivo

Realizar a configuração inicial de um roteador e um switch Cisco utilizando boas práticas de configuração, preparando os equipamentos para administração e gerenciamento em uma rede.

---

## Conceitos Trabalhados

- Cisco IOS
- CLI Cisco
- IPv4
- Interface de Gerenciamento
- Gateway Padrão
- Console
- VTY
- Banner MOTD
- Running Configuration
- Startup Configuration

---

## Topologia

> <img width="948" height="502" alt="topologia lab0" src="https://github.com/user-attachments/assets/d8915bdb-df06-4f84-a459-303e480a3242" />

---

## Endereçamento

| Equipamento | Interface | Endereço IP |
|-------------|-----------|-------------|
| R1 | GigabitEthernet0/0 | 192.168.1.1/24 |
| SW1 | VLAN 1 | 192.168.1.2/24 |

---

## Configurações Realizadas

- Configuração do hostname
- Configuração do `enable secret`
- Configuração da senha de console
- Configuração das linhas VTY
- Configuração do banner MOTD
- Ativação do `service password-encryption`
- Configuração da interface GigabitEthernet0/0 do roteador
- Configuração da interface VLAN 1 do switch
- Configuração do gateway padrão do switch
- Salvamento da configuração

---

## Comandos de Validação

### Roteador

```text
show ip interface brief
show running-config
show startup-config
show version
```

### Switch

```text
show ip interface brief
show running-config
show startup-config
show vlan brief
show version
```

---

## Evidências

### Topologia

- <img width="948" height="502" alt="topologia lab0" src="https://github.com/user-attachments/assets/7ccd7042-f07e-4447-883e-5a58f4271dd9" />

### Configuração do Roteador

- <img width="532" height="458" alt="show ip interface r1" src="https://github.com/user-attachments/assets/bd89e4b6-92f7-4560-8632-86dd4f97c78a" />

- <img width="523" height="502" alt="show running config r1" src="https://github.com/user-attachments/assets/51319f1e-c083-4738-b22f-cbb3bbe9155e" />


### Configuração do Switch

- <img width="522" height="498" alt="show ip interface sw1" src="https://github.com/user-attachments/assets/222e0e55-8dc3-47a8-9ad9-e8fe9c28ad99" />

- <img width="526" height="501" alt="show vlan brief sw1" src="https://github.com/user-attachments/assets/bbf663b0-0c91-4f0d-87af-11a65dfbe3d5" />


### Testes de Comunicação

- <img width="950" height="499" alt="lab0 teste de ping" src="https://github.com/user-attachments/assets/89c0db14-1089-49ec-a603-9b6f3e0653c3" />

- <img width="958" height="503" alt="lab0 traceroute" src="https://github.com/user-attachments/assets/514066be-02ee-460f-9693-1f074355486c" />

---

## Arquivos

| Arquivo | Descrição |
|----------|-----------|
| https://drive.google.com/file/d/1Fameype0ytcc-ibhqRkrgV1zyNOkc4RZ/view?usp=sharing | Topologia do laboratório desenvolvida no Cisco Packet Tracer. |
| https://drive.google.com/file/d/1MTWou9c3OkEussBkee-x_NidATJyKtJi/view?usp=sharing | Configuração final do roteador. |
| https://drive.google.com/file/d/1zKSG1kQPP4hF76RDKxAhYVj9fXGasiAg/view?usp=sharing | Configuração final do switch. |

---

## Resultado

Todos os objetivos do laboratório foram concluídos com sucesso.

- Equipamentos configurados.
- Interfaces ativas.
- Configurações salvas.
- Comunicação validada.
- Testes de conectividade realizados com sucesso.

---

## Lições Aprendidas

- Diferença entre `running-config` e `startup-config`.
- Diferença entre a configuração de um roteador e de um switch Layer 2.
- Importância do comando `no shutdown`.
- Utilização dos principais comandos `show` para validação.
- Configuração dos acessos administrativo, console e remoto (VTY).

---

## Próximo Laboratório

**Lab01 - Criação de VLANs**
https://github.com/Bezalcs/CCNA-Labs/blob/main/Labs/lab01.md
