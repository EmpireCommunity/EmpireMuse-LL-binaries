# EmpireMuse-LL-binaries

Espelho oficial e repositório de distribuição de binários do Lavalink e plugins homologados para o [EmpireMuse](https://github.com/EmpireCommunity/EmpireMuse).

Todos os artefatos possuem integridade auditada e verificada via checksum SHA-256 (`SHA256SUMS`).

---

## Componentes da Release 0.0.4

| Arquivo | Versão / Commit | Origem / Upstream | Licença |
| :--- | :--- | :--- | :--- |
| `Lavalink.jar` | `4.2.2` | [lavalink-devs/Lavalink](https://github.com/lavalink-devs/Lavalink) | MIT |
| `youtube-plugin-2be8e542d3f6f178e048dca565892684c2e40177.jar` | `2be8e54` | [lavalink-devs/youtube-source](https://github.com/lavalink-devs/youtube-source) | MIT |
| `lavasrc-plugin-4.8.3.jar` | `4.8.3` | [topi314/LavaSrc](https://github.com/topi314/LavaSrc) | Apache-2.0 |
| `lavalink-2.6.1.jar` | `2.6.1` | [DuncteBot/skybot-lavalink-plugin](https://github.com/DuncteBot/skybot-lavalink-plugin) | Apache-2.0 |
| `soundy-plugin-1.1.0.jar` | `1.1.0` (`e2c5da8`) | [lowkwrs/soundy](https://github.com/lowkwrs/soundy) | MIT |
| `application.yml` | `0.0.4` | Configuração oficial do servidor | GPL-2.0 |

---

## Compilação do Plugin Soundy

O plugin Soundy foi compilado a partir do commit oficial [`e2c5da8e96661d2a9eb96ee53e3d5b95903bc194`](https://github.com/lowkwrs/soundy/commit/e2c5da8e96661d2a9eb96ee53e3d5b95903bc194) do repositório [`lowkwrs/soundy`](https://github.com/lowkwrs/soundy) (licença MIT), que incorpora o suporte a streaming fMP4 HLS do SoundCloud. Não usamos JitPack nem JARs de forks.

- **Commit**: `e2c5da8e96661d2a9eb96ee53e3d5b95903bc194`
- **JDK**: Eclipse Temurin 17 (imagem `eclipse-temurin:17-jdk`)
- **Comando**: `./gradlew :plugin:jar`
- **Artefato**: `plugin/build/libs/soundy-plugin-1.1.0.jar`
- **SHA-256 publicado**: `9568b5930969346b1afba89df8c0c6d373c2b553e087af09fb3c190f252a3cc9`
- **Workflow**: [`.github/workflows/build-soundy.yml`](.github/workflows/build-soundy.yml) (manual, anexa o JAR como artefato do run)

### Recompilar e comparar

```bash
git clone https://github.com/lowkwrs/soundy && cd soundy
git checkout e2c5da8e96661d2a9eb96ee53e3d5b95903bc194
docker run --rm -v "$PWD":/src -w /src eclipse-temurin:17-jdk ./gradlew :plugin:jar
sha256sum plugin/build/libs/soundy-plugin-1.1.0.jar
```

O hash do JAR recompilado **pode não coincidir** com o publicado: o `plugin.properties` embutido leva um comentário com a data da compilação (e o ZIP guarda timestamps). A comparação confiável é pelo conteúdo:

```bash
mkdir novo oficial
unzip -q plugin/build/libs/soundy-plugin-1.1.0.jar -d novo
curl -fsSL https://github.com/EmpireCommunity/EmpireMuse-LL-binaries/releases/download/0.0.4/soundy-plugin-1.1.0.jar -o oficial.jar
unzip -q oficial.jar -d oficial
diff -r novo oficial   # esperado: só a linha de data (comentário) em plugin.properties
```

Todas as classes (`*.class`) devem ser idênticas byte a byte. Qualquer outra diferença invalida a release.

---

## Verificação de Integridade

```bash
sha256sum -c SHA256SUMS
```
