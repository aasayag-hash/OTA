# OTA — Firmware del Medidor Acústico ESP32-S3

Repositorio **público** que distribuye los binarios de firmware para actualización
por aire (OTA). El código fuente está en un repositorio privado aparte.

## Estructura

```
medidor/medidor_acustico.bin   <- firmware del Medidor Acústico ESP32-S3
```

## Cómo actualiza el equipo

El medidor (en modo WiFi **Directo / STA**, conectado a internet) descarga el
binario desde:

```
https://raw.githubusercontent.com/aasayag-hash/OTA/main/medidor/medidor_acustico.bin
```

con verificación TLS (cert bundle) y rollback automático: si el firmware nuevo no
arranca bien, el equipo vuelve solo al anterior.

## Publicar una nueva versión

1. Compilar el firmware en el repo privado (`idf.py build`).
2. Copiar `build/medidor_acustico.bin` a `medidor/medidor_acustico.bin` aquí.
3. `git add medidor/medidor_acustico.bin && git commit -m "fw vX.YY" && git push`.

El equipo tomará la versión nueva la próxima vez que se toque **Actualizar firmware**
en Ajustes → WiFi.
