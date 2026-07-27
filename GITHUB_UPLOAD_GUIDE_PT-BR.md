# Guia rápido para publicar no GitHub

## Antes de publicar

1. Abra `firmware/AQM_FW_v0.1.0.yaml` e confirme que não há senha real.
2. Confirme que `firmware/display_oled_ssd1306.yaml` está na mesma pasta do firmware principal.
2. Não copie seu `secrets.yaml` real para o repositório.
3. O arquivo público deve ser somente `secrets.example.yaml`.

## Criar o repositório pelo site

1. Entre no GitHub e selecione **New repository**.
3. Nome sugerido: `aqm-air-quality-monitor`.
3. Descrição sugerida: `ESP32-based portable environmental data acquisition station for indoor CO2, temperature, humidity and pressure monitoring.`
4. Escolha **Public** ou **Private**.
5. Não marque a criação automática de README, `.gitignore` ou licença, pois estes arquivos já estão no pacote.
6. Crie o repositório.

## Enviar pelo terminal

Dentro da pasta do projeto:

```bash
git init
git add .
git commit -m "Release AQM v0.1.0"
git branch -M main
git remote add origin URL_DO_SEU_REPOSITORIO
git push -u origin main
```

## Criar a primeira release

- Tag: `v0.1.0`
- Título: `AQM v0.1.0 — First functional prototype`
- Resumo: ESP32, SCD41, BME280, OLED, web server, fixed IP and OTA validated on Hardware Architecture A03.
