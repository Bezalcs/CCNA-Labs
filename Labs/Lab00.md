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

> Inserir imagem da topologia.

![Topologia](imagens/topologia.png)

---

## Endereçamento

| Equipamento | Interface | Endereço IP |
|-------------|-----------|-------------|
| R1 | GigabitEthernet0/0 | 192.168.1.1/24 |
| SW1 | VLAN 1 | 192.168.1.2/24 |
| PC1 | FastEthernet0 | 192.168.1.10/24 |

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

- `imagens/topologia.png`

### Configuração do Roteador

- `imagens/show-ip-interface-brief-r1.png`
- `imagens/show-running-config-r1.png`

### Configuração do Switch

- `imagens/show-ip-interface-brief-sw1.png`
- `imagens/show-vlan-brief-sw1.png`

### Testes de Comunicação

- `imagens/ping-r1-sw1.png`
- `imagens/traceroute-pc-r1.png`

---

## Arquivos

| Arquivo | Descrição |
|----------|-----------|
| `Lab00.pkt` | Topologia do laboratório desenvolvida no Cisco Packet Tracer. |
| `R1-running-config.txt` | Configuração final do roteador. |
| `SW1-running-config.txt` | Configuração final do switch. |

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
