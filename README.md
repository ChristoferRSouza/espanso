# espanso

Configuração pessoal do [Espanso](https://espanso.org), um expansor de texto open-source multiplataforma (Windows, macOS e Linux). Ele roda em segundo plano e substitui pequenos gatilhos de texto (como `:like` ou `:hoje`) por trechos maiores, textos dinâmicos (data, scripts) ou snippets multilinha, economizando digitação repetitiva.

## Instalação (Windows)

A forma recomendada de instalar o Espanso no Windows é via [winget](https://learn.microsoft.com/windows/package-manager/winget/):

```bash
winget install --id Espanso.Espanso
```

Após a instalação, registre o serviço e inicie o Espanso:

```bash
espanso service register
espanso start
```

Para verificar se está rodando corretamente:

```bash
espanso status
```

## Estrutura deste repositório

- [`match/base.yml`](match/base.yml) — arquivo principal de matches (gatilhos de texto e suas expansões).

## Como verificar os caminhos de configuração

O Espanso usa pastas específicas para guardar sua configuração, os matches e o runtime. Para descobrir onde cada uma está na sua máquina, rode:

```bash
espanso path
```

Esse comando lista três caminhos:

- **Config**: onde ficam `config/default.yml` e outros perfis de configuração.
- **Packages**: onde ficam os pacotes/módulos instalados via `espanso install`.
- **Runtime**: arquivos temporários usados pelo processo em execução (logs, PID, etc).

No Windows, o caminho de configuração padrão normalmente é:

```
%APPDATA%\espanso
```

Para que o Espanso use os matches deste repositório, copie (ou crie um link simbólico para) a pasta `match/` deste projeto dentro da pasta de **Config** retornada por `espanso path`. Depois de qualquer alteração nos arquivos `.yml`, reinicie o serviço para aplicar as mudanças:

```bash
espanso restart
```
