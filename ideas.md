# Ideas de Diseño - IAMET Website

## Requisitos del Cliente
- Sitio corporativo minimalista premium estilo Apple
- Empresa integradora de TI enfocada en continuidad operativa
- Mucho espacio en blanco, tipografía moderna, jerarquía visual clara
- Animaciones sutiles, responsive mobile-first

---

<response>
## Idea 1: Swiss Precision Tech
<probability>0.08</probability>

### Design Movement
Inspirado en el **Diseño Suizo (International Typographic Style)** combinado con estética de arquitectura industrial moderna.

### Core Principles
1. **Grid matemático riguroso** - Cada elemento alineado a una cuadrícula de 8px
2. **Contraste tipográfico extremo** - Títulos ultra-bold vs texto light
3. **Monocromatismo con acento único** - Escala de grises con un solo color de acento (azul eléctrico)
4. **Espacios negativos como elemento activo** - El vacío comunica tanto como el contenido

### Color Philosophy
- **Base**: Blanco puro (#FFFFFF) como lienzo de precisión
- **Texto principal**: Negro carbón (#0A0A0A) para máxima legibilidad
- **Grises funcionales**: #F5F5F5 (fondos), #E0E0E0 (bordes), #6B6B6B (texto secundario)
- **Acento**: Azul eléctrico (#0066FF) - representa tecnología, confianza, precisión
- **Intención emocional**: Transmitir exactitud, profesionalismo técnico, confiabilidad

### Layout Paradigm
- **Estructura asimétrica de dos columnas** - 60/40 o 70/30
- **Texto alineado a la izquierda** con márgenes generosos a la derecha
- **Secciones de altura completa** (100vh) para impacto visual
- **Líneas divisorias sutiles** en lugar de cards

### Signature Elements
1. **Números grandes decorativos** - Numeración de secciones en tipografía display
2. **Líneas horizontales de acento** - Separadores minimalistas de 2px
3. **Tipografía escalonada** - Títulos que "caen" en cascada

### Interaction Philosophy
- Transiciones lineales y precisas (no ease-out suaves)
- Hover states que revelan información adicional
- Scroll-triggered animations con timing matemático

### Animation
- **Entrada**: Fade-in con translate-y de 20px, duration 600ms, ease-linear
- **Hover**: Scale 1.02 con transición de 200ms
- **Scroll**: Parallax sutil en imágenes (0.1x velocidad)
- **Números**: Counter animation en estadísticas

### Typography System
- **Display**: Inter Black (900) para H1
- **Headings**: Inter Bold (700) para H2-H3
- **Body**: Inter Regular (400) para párrafos
- **Accent**: Inter Light (300) para subtítulos y citas
- **Escala**: 64px / 48px / 32px / 24px / 18px / 14px
</response>

---

<response>
## Idea 2: Ethereal Cloud Architecture
<probability>0.06</probability>

### Design Movement
Inspirado en **Glassmorphism evolucionado** combinado con estética de interfaces de control de misión espacial.

### Core Principles
1. **Capas de profundidad atmosférica** - Elementos flotantes con blur y transparencia
2. **Gradientes sutiles direccionales** - Luz que viene de arriba-izquierda
3. **Bordes luminosos** - Contornos que brillan sutilmente
4. **Jerarquía por elevación** - Elementos importantes más "cerca" del usuario

### Color Philosophy
- **Base**: Gris nube (#F8F9FA) con gradiente sutil hacia blanco
- **Superficies**: Blanco con 80% opacidad + backdrop-blur
- **Texto principal**: Gris grafito (#1A1A2E) - sofisticado, no negro puro
- **Acento primario**: Azul profundo (#1E3A5F) - autoridad, estabilidad
- **Acento secundario**: Cyan suave (#4ECDC4) - innovación, tecnología
- **Intención emocional**: Transmitir sofisticación, innovación controlada, visión futurista

### Layout Paradigm
- **Cards flotantes** con sombras difusas y blur
- **Espaciado generoso** entre elementos (mínimo 48px)
- **Contenido centrado** con ancho máximo de 1200px
- **Secciones con fondos degradados** muy sutiles

### Signature Elements
1. **Glass cards** - Fondos semi-transparentes con blur de 20px
2. **Glow effects** - Halos sutiles en elementos interactivos
3. **Iconografía lineal** - Iconos stroke de 1.5px con esquinas redondeadas

### Interaction Philosophy
- Transiciones suaves y orgánicas (ease-out)
- Elementos que "respiran" con micro-animaciones
- Feedback visual inmediato con cambios de opacidad

### Animation
- **Entrada**: Fade-in con scale de 0.95 a 1, duration 800ms, ease-out
- **Hover**: Elevación (translate-y -4px) + intensificación de sombra
- **Cards**: Tilt sutil siguiendo el cursor (3D transform)
- **Fondos**: Gradientes animados muy lentos (20s cycle)

### Typography System
- **Display**: SF Pro Display Bold para H1 (o system-ui)
- **Headings**: SF Pro Display Semibold para H2-H3
- **Body**: SF Pro Text Regular para párrafos
- **Accent**: SF Pro Text Light para metadata
- **Escala**: 56px / 40px / 28px / 20px / 16px / 13px
</response>

---

<response>
## Idea 3: Brutalist Tech Minimalism
<probability>0.04</probability>

### Design Movement
Inspirado en **Neo-Brutalism digital** con influencias de diseño editorial japonés y arquitectura Bauhaus.

### Core Principles
1. **Honestidad estructural** - Elementos que muestran su función sin decoración
2. **Tipografía como arquitectura** - Letras que construyen el espacio
3. **Contraste dramático** - Blanco y negro con mínimo gris
4. **Asimetría intencional** - Layouts que desafían la expectativa

### Color Philosophy
- **Base**: Blanco hueso (#FAFAFA) - cálido, no clínico
- **Texto**: Negro absoluto (#000000) para máximo contraste
- **Acento único**: Amarillo señalético (#FFD700) - atención, acción
- **Sin grises intermedios** - Solo blanco, negro y acento
- **Intención emocional**: Transmitir audacia, claridad absoluta, confianza sin adornos

### Layout Paradigm
- **Bloques masivos de texto** alternando con espacios vacíos
- **Alineación a la izquierda radical** - Sin centrado
- **Overlapping elements** - Texto que cruza secciones
- **Full-bleed images** sin padding

### Signature Elements
1. **Bordes gruesos** - 3px solid black en elementos clave
2. **Tipografía oversized** - H1 que ocupa 30% de la pantalla
3. **Marcadores visuales** - Puntos, líneas, números como decoración funcional

### Interaction Philosophy
- Transiciones instantáneas (150ms máximo)
- Estados hover con inversión de colores
- Click feedback con "snap" visual

### Animation
- **Entrada**: Clip-path reveal de izquierda a derecha, 400ms
- **Hover**: Inversión de colores (bg-black, text-white), 100ms
- **Scroll**: Elementos que aparecen con "stamp" effect
- **CTA**: Pulse animation en botones principales

### Typography System
- **Display**: Space Grotesk Bold para H1 (impacto geométrico)
- **Headings**: Space Grotesk Medium para H2-H3
- **Body**: IBM Plex Sans Regular para párrafos
- **Mono**: IBM Plex Mono para datos técnicos
- **Escala**: 72px / 48px / 32px / 20px / 16px / 12px
</response>

---

## Decisión Final

**Selecciono: Idea 1 - Swiss Precision Tech**

### Justificación
Esta propuesta es la más alineada con los requisitos del cliente (estilo Apple, minimalista premium) mientras ofrece una identidad visual distintiva. El enfoque suizo transmite:
- **Precisión técnica** - Ideal para una empresa de infraestructura TI
- **Confiabilidad** - El grid riguroso comunica orden y control
- **Profesionalismo** - Sin elementos decorativos innecesarios
- **Modernidad atemporal** - Un diseño que no envejecerá rápidamente

El uso de números grandes como elemento decorativo añade personalidad sin comprometer el minimalismo, y el acento azul eléctrico proporciona el toque tecnológico necesario sin saturar.
