# Daiso Fiscal RTC — Cockpit de Auditoria e Simulação Tributária

Sistema web open-source desenvolvido para **Analistas Fiscais Sêniores** operarem a transição da Reforma Tributária do Consumo (**CBS, IBS e Imposto Seletivo — LC nº 214/2025**), preparado para integração com a API oficial da Receita Federal ([ReceitaFederal/calculadora-rtc-regime-regular](https://github.com/ReceitaFederal/calculadora-rtc-regime-regular)).

## Funcionalidades Principais

- **Auditor XML em Lote (NF-e / NFC-e):** Upload de múltiplos arquivos `.xml`, pastas inteiras ou pacotes `.zip` processados localmente no navegador, com auditoria item a item seguindo o contrato `POST /observabilidade/regime-geral` (um erro em um item não interrompe o restante da nota).
- **Relatórios Consolidados em CSV:** Exportação do lote completo ou **somente das divergências** para correção rápida no ERP/PDV.
- **Memória de Cálculo & Compliance:** Visualização de `memoriaCalculo`, fundamentação legal, prévia do grupo XML `<IBSCBS>` e JSON Pointers de erro (`REG-011`, `REG-024`, `CST-002`).
- **Saneamento de SKUs & NCM:** Importação e exportação em CSV, edição direta na tabela, correção de CSTs em lote e alertas de incidência de Imposto Seletivo (IS).
- **Simulador de Precificação & Transição (2026–2033):** Compara carga tributária e margem líquida entre o sistema legado e o IVA Dual por fora em diferentes UFs e faixas de preço.
- **Motor Offline ADR003:** Funciona 100% sem servidor com arredondamento bancário `HALF_EVEN` quando a API oficial não estiver conectada.

## Como publicar no GitHub Pages (acesso em qualquer dispositivo)

1. Suba o arquivo `index.html` (e opcionalmente `README.md`, `docker-compose.yml` e `LICENSE`) na raiz da branch `main`.
2. No repositório, acesse **Settings → Pages**.
3. Em **Build and deployment**, selecione **Branch: `main`** e pasta **`/ (root)`**, depois clique em **Save**.
4. Em 1 a 2 minutos, o sistema ficará disponível em:
   `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`

## Como conectar à API Oficial da Receita Federal (Docker)

Caso a equipe de TI deseje rodar o motor Java oficial localmente junto com o Cockpit:

```bash
git clone https://github.com/ReceitaFederal/calculadora-rtc-regime-regular.git
docker compose up -d
```

Depois, acesse `http://localhost:8088` e valide a conexão na aba **API RFB & Governança**.

## Privacidade e Sigilo Fiscal

Todos os arquivos `.xml`, `.zip` e planilhas `.csv` carregados no Cockpit são processados exclusivamente na memória do navegador do usuário. Nenhum dado fiscal é enviado ao GitHub ou a servidores externos.

## Licença

Distribuído sob a licença **MIT** (compatível com a Portaria Cotec nº 342/2026 da Receita Federal). Consulte o arquivo `LICENSE` para mais detalhes.