# TNK Mobile — Releases

Canal público de download do APK do app **TNK Mobile** (força de vendas do Master Key),
publicado em **https://mobile.tnksystem.com.br/** (GitHub Pages deste repositório).

A página busca a release marcada como *latest* (API pública do GitHub) e o botão
**Baixar aplicativo** aponta para o `.apk` anexado a ela. Serve para a **primeira
instalação**: depois disso o app se atualiza pelo servidor TNK Mobile da loja
(`app\mk_sync.apk` + `app\versao.json` na pasta do servidor), com bloqueio até atualizar.

O código-fonte não fica aqui.

## Como publicar uma nova versão

1. Gere o APK no projeto (`flutter build apk --release`) e confira a assinatura
   (SHA256 `B4:8C:E2:CE…AA:8C:85`) — a mesma chave de sempre, senão o Android não instala
   por cima.
2. Crie a release com a tag `v<versão>` (a mesma do `pubspec.yaml`, sem o `+build`)
   e anexe **um** arquivo `.apk`:

   ```bash
   gh release create v0.23.1 tnk-mobile-0.23.1.apk -R tnksystem/tnk-mobile-releases \
     --title "TNK Mobile 0.23.1" --notes "- novidade 1
   - novidade 2"
   ```

## Regras

- Uma release = um `.apk`. A mais recente (não rascunho / não pré-release) é a que a página mostra.
- As notas da release (linhas com `-`) aparecem em "Novidades desta versão".
- Não publique aqui `appsettings.json` nem nada com senha.
