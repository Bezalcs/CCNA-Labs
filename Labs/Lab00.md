# Lab00 - Configuração Inicial de Switch e Roteador

## Objetivo

Realizar a configuração inicial de um roteador e um switch Cisco utilizando boas práticas de configuração, preparando os equipamentos para administração e gerenciamento em uma rede.

---

## Tarefas Executadas

- Configuração do hostname
- Configuração da senha do modo privilegiado (`enable secret`)
- Configuração da senha de acesso via console
- Configuração do acesso remoto (VTY)
- Configuração do banner MOTD
- Ativação do `service password-encryption`
- Configuração da interface GigabitEthernet0/0 do roteador
- Configuração da interface VLAN 1 do switch
- Configuração do gateway padrão do switch
- Salvamento da configuração (`copy running-config startup-config`)
- Validação utilizando comandos `show`
- Testes de conectividade com `ping` e `traceroute`

---

## Comandos de Validação

### Roteador

- `show ip interface brief`
- `show running-config`
- `show startup-config`
- `show version`

### Switch

- `show ip interface brief`
- `show running-config`
- `show startup-config`
- `show vlan brief`

---

## Evidências

> Nesta seção serão adicionados:
>
> - Topologia da rede
> - Prints dos comandos de validação
> - Testes de conectividade
> - Arquivos de configuração (`running-config`)

---

## Conclusão

Este laboratório permitiu praticar a configuração inicial de um roteador e de um switch Cisco, abordando os principais procedimentos necessários para disponibilizar os equipamentos em um ambiente de rede.

Durante a atividade foram configurados o hostname, a senha do modo privilegiado, os acessos via console e VTY, o banner MOTD, a criptografia das senhas, o endereçamento das interfaces de gerenciamento e o gateway padrão do switch. Após a aplicação das configurações, foram realizados testes de validação utilizando comandos `show`, além de testes de conectividade com `ping` e `traceroute`, confirmando o funcionamento esperado da topologia.
