# anchored-video-export
Marca de creación inmutable para archivos de video, anclada en la blockchain de Bitcoin



> anchored-video-export
"Marca de creación inmutable para archivos de video, anclada en la blockchain de Bitcoin."



Este README integra todo: descripción, problema, solución, SDK, ejemplos de integración, y documentación técnica para APIs y desarrolladores.


---

# 🎬 anchored-video-export

> 🟧 Sistema de firma, anclaje y certificación de videos exportados, con verificación pública e inmutable en la blockchain de Bitcoin.

---

## ❓ ¿Cuál es el problema

Hoy en día cualquier persona puede crear, exportar, convertir o manipular videos sin dejar ninguna huella de origen verificable.  
No existe un estándar técnico ni criptográfico que certifique públicamente **quién creó un video, cuándo lo hizo y con qué contenido exacto**.

### Las consecuencias:
- ❌ Suplantación y falsificación de autoría
- ❌ Manipulación de fechas de creación
- ❌ Videos generados por IA sin trazabilidad
- ❌ Derechos de propiedad intelectual vulnerables
- ❌ Certificaciones centralizadas fácilmente manipulables

---

## ✅ Nuestra solución

**`anchored-video-export`** introduce un sistema de firma digital, hashing criptográfico y anclaje a la red Bitcoin que permite:

1. Generar un **hash SHA256** del archivo de video exacto.
2. (Opcional) Firmar ese hash con una clave privada (PGP o Bitcoin).
3. **Anclar el hash en la blockchain de Bitcoin** mediante `OP_RETURN` o OpenTimestamps.
4. Emitir un **certificado de creación** verificable con información de bloque, fecha, autoría y más.
5. Incluir el certificado en los metadatos del video o como archivo adjunto (`.json`, `.ots`, `.txt`).

---

## 🛠️ Requisitos

- Python 3.8+
- ffmpeg instalado
- Conexión a un nodo Bitcoin o API externa (ej: Blockstream, Mempool)
- OpenTimestamps (si se usa vía OTS)
- Clave privada (opcional) para firmar autoría

---

## 📦 Instalación

```bash
git clone https://github.com/tuusuario/anchored-video-export.git
cd anchored-video-export
pip install -r requirements.txt


---

🚀 Flujo de uso básico

# 1. Calcular hash
python hash_video.py --file exportado.mp4

# 2. (Opcional) Firmar con clave privada
python sign_hash.py --hash <HASH> --key clave.asc

# 3. Anclar en la red Bitcoin
python anchor_hash.py --hash <HASH> --method ots

# 4. Generar certificado de autenticidad
python generate_certificate.py --hash <HASH> --txid <TXID>


---

🧱 Certificado generado (ejemplo .json)

{
  "filename": "exportado.mp4",
  "hash_sha256": "ae72f3c41e8d6eabcbbf924c3ee66f11...",
  "anchored_txid": "b9fa32ee22c7c8c63a6e12...",
  "blockchain": "Bitcoin",
  "block_height": 842771,
  "timestamp_utc": "2025-07-07T18:34:12Z",
  "signed_by": "LAEV",
  "sdk_version": "1.0.0"
}


---

🔗 SDK embebible – AnchoredVideoSDK

Integra esta solución en cualquier conversor o exportador de video:

🔧 Lenguajes soportados

Python (base)

C++ (FFmpeg plugins)

Node.js (API REST)

Rust (CLI)

OBS Plugin (en desarrollo)


🧩 Ejemplo de integración (Python)

from anchored_video_sdk import Hasher, BitcoinAnchor, MetadataWriter

hash_value = Hasher.hash_file("video_final.mp4")
tx_id = BitcoinAnchor.anchor(hash_value, method="ots")

MetadataWriter.generate_certificate(
    filepath="video_final.mp4",
    hash=hash_value,
    txid=tx_id,
    blockchain="bitcoin",
    signed_by="LAEV"
)


---

🛜 API REST opcional (para nodos centralizados o proxies)

POST /anchor
{
  "hash": "3a7c8...dfee"
}

{
  "txid": "b6f7ddc6...",
  "block_height": 842771,
  "timestamp": "2025-07-07T18:31:00Z"
}


---

📂 Estructura del repositorio

anchored-video-export/
│
├── hash_video.py             # Cálculo del hash
├── sign_hash.py              # Firma opcional del hash
├── anchor_hash.py            # Anclaje en Bitcoin
├── generate_certificate.py   # Emisión del certificado
├── /anchored_video_sdk       # SDK modular para integración
├── /docs                     # Documentación técnica extendida
├── requirements.txt
└── README.md


---

📚 Documentación técnica

Disponible en el directorio /docs/. Incluye:

SDK_USAGE.md – Cómo integrar el SDK en editores de video

API_REFERENCE.md – Endpoints REST para anclaje remoto

FORMAT.md – Especificación de los certificados .json, .ots, .txt

INTEGRATIONS.md – Casos de uso reales con FFmpeg, OBS, Node, etc.



---

📈 Casos de uso reales

📰 Periodismo con evidencia de fecha y origen

🎞️ Cineastas o editores que certifican autoría

🎨 Artistas IA que sellan sus creaciones automáticamente

👮 Videos legales o judiciales sellados criptográficamente

📺 Plataformas que exigen trazabilidad en contenido



---

📜 Licencia

MIT License — Libre uso, distribución y modificación con atribución.


---

👤 Autor y contacto

Lerry Alexander Elizondo Villalobos (LAEV)
GitHub: @lerryalexanderelizondo
Correo: laev.lab@proton.me


---

✊ Frase de guerra

"El contenido ya no se presume auténtico. Se prueba con la blockchain."


---

⭐ Contribuciones

Pull requests, ideas, mejoras y forks son bienvenidos.
Especial interés en desarrolladores que deseen construir:

Plugins oficiales para Adobe, DaVinci o Final Cut.

Firmas colectivas multiusuario.

Extensiones para sistemas judiciales y notarios digitales.




