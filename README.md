# 🛠️ Tools

Colección de notas en español sobre **herramientas de ciberseguridad y pentesting**, organizadas por fase o tipo de ataque. Cada nota resume qué hace la herramienta y reúne los comandos más útiles para tenerlos a mano durante prácticas, laboratorios y CTFs.

> ⚠️ **Uso responsable:** este material es solo para fines educativos y para auditar sistemas propios o con autorización expresa. Usar estas herramientas contra sistemas ajenos sin permiso es ilegal.

## 📚 Contenido

| Categoría | Herramientas |
| --- | --- |
| **OSINT: Búsquedas DNS** | `dig`, `host`, `nslookup`, `whois` |
| **OSINT: Certificados SSL** | `sslscan` |
| **OSINT: Scanners OSINT** | `SpiderFoot`, `Recon-ng` |
| **OSINT: Reputación de la empresa y postura de seguridad** | `h8mail`, `ExifTool` |
| **Reconocimiento Activo** | `Nmap`, `Scapy`, `Feroxbuster`, `git-dumper` |
| **Ataques en la ruta (MitM)** | `Ettercap` |
| **Vulnerabilidades Basadas en la Red** | `smbclient`, `enum4linux` |
| **Vulnerabilidades Basadas en Aplicaciones** | `Nikto`, `GVM` (Greenbone / OpenVAS) |
| **Vulnerabilidades Basadas en la Autenticación** | `John the Ripper`, `Hashcat`, `RainbowCrack` |

## 🗂️ Estructura del repositorio

```
tools/
├── OSINT/
│   ├── Búsquedas DNS/
│   ├── Certificados SSL/
│   ├── Scaners OSINT/
│   └── Reputación de la empresa y postura de seguridad/
├── Reconocimiento Activo/
│   └── Tools - Tipos de enumeración/
├── Ataques en la ruta (MItM)/
├── Vulnerabilidades Basadas en la Red/
│   └── Programas-Herramientas/
├── Vulnerabilidades Basadas en Aplicaciones/
└── Vulnerabilidades Basadas en la Autenticación/
```

Las capturas de pantalla viven en carpetas `Adjuntos/` junto a las notas que las usan.

## 📝 Formato de las notas

Cada herramienta tiene su propio archivo `.md` con:

- Un **encabezado YAML** con la nota de tema relacionada (`relacionado`) y la `categoria`.
- Una **descripción breve** de qué hace y cuándo se usa.
- **Comandos y ejemplos** listos para copiar, con `*valor*` como marcador de lo que debes reemplazar.

Las notas usan enlaces tipo wiki (`[[...]]`) y rutas de imágenes con `![[...]]`, por lo que se leen mejor abriendo el repositorio como bóveda en [Obsidian](https://obsidian.md). En GitHub siguen siendo legibles, pero esos enlaces no se resuelven.

## 🚀 Cómo usarlo

```bash
git clone https://github.com/k3gar/tools.git
```

Luego busca la herramienta por categoría, o usa `grep -ri "palabra" .` para encontrar un comando rápidamente.

## 🧪 Entorno recomendado

Casi todas las herramientas vienen preinstaladas en [Kali Linux](https://www.kali.org/). Para practicar de forma legal y segura, usa laboratorios propios (máquinas virtuales, redes aisladas) o plataformas diseñadas para ello, como TryHackMe, Hack The Box u OverTheWire.

## 🤝 Contribuciones

Las notas son apuntes personales en constante crecimiento. Si encuentras un error o quieres sugerir una herramienta, abre un *issue* o un *pull request*.
