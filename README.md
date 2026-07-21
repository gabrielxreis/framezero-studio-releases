# FrameZero Studio — canal de atualizações

Este repositório distribui as atualizações do **FrameZero Studio**.
Ele guarda apenas os *releases* (o app empacotado) — o código-fonte fica noutro lugar.

## Como o app usa isto

Toda vez que o FrameZero Studio abre, ele consulta o release mais recente daqui.
Se a versão for maior que a instalada, oferece atualizar — baixa, troca o app e reabre.
Sem internet, o app abre normalmente: a atualização nunca trava a abertura.

## Publicar uma atualização

Na máquina de desenvolvimento:

```bash
./DOCS/publicar-atualizacao.sh 1.0.2 "o que mudou nesta versão"
```

O script compila em Release, empacota com `ditto` (preservando a assinatura do app)
e cria o release aqui. As outras máquinas recebem na próxima abertura.

## Voltar uma versão (rollback)

Antes de atualizar, o app guarda a versão anterior. Em **Ajustes → Atualizações**
aparece *"Voltar para a versão X"*.

Projetos, cortes e configurações **não são afetados** — ficam fora do app,
em `~/Movies/FrameZero Projetos` e `~/Library/Application Support/FrameZero Studio`.

## Formato esperado do release

- **Tag:** `v<versão>` — ex.: `v1.0.2`
- **Anexo:** um `.zip` contendo o `FrameZero Clips.app`
- A versão da tag precisa bater com a `CFBundleShortVersionString` do bundle
