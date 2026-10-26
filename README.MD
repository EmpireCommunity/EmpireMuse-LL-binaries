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

O plugin Soundy foi compilado a partir do commit oficial [`e2c5da8e96661d2a9eb96ee53e3d5b95903bc194`](https://github.com/lowkwrs/soundy/commit/e2c5da8e96661d2a9eb96ee53e3d5b95903bc194) do repositório [`lowkwrs/soundy`](https://github.com/lowkwrs/soundy) (licença MIT), que incorpora o suporte a streaming fMP4 HLS do SoundCloud:

- **JDK**: Eclipse Temurin 17 (`JavaVersion.VERSION_17`)
- **Comando**: `./gradlew build`
- **Artefato Gerado**: `plugin/build/libs/soundy-plugin-1.1.0.jar`
- **Workflow de Build**: [`.github/workflows/build-soundy.yml`](.github/workflows/build-soundy.yml)
- **SHA-256**: `9568b5930969346b1afba89df8c0c6d373c2b553e087af09fb3c190f252a3cc9`

---

## Verificação de Integridade

```bash
sha256sum -c SHA256SUMS
```
