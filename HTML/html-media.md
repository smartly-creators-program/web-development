# HTML Media: Audio, Video & iFrame

> Bring your web pages to life with embedded media — sound, video, and external content.

---

## 📌 What is HTML Media?

HTML provides built-in elements to embed **media content** directly into web pages — without needing plugins like Flash. The three core media elements are:

| Element | Purpose |
|---|---|
| `<audio>` | Embed sound / music / podcasts |
| `<video>` | Embed video clips |
| `<iframe>` | Embed external web content (YouTube, maps, etc.) |

---

## 🔊 The `<audio>` Element

The `<audio>` element lets you embed sound files directly into a webpage.

### Basic Syntax

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

> 💡 The fallback text between the tags is displayed only if the browser doesn't support `<audio>`.

### Key Attributes

| Attribute | Description |
|---|---|
| `controls` | Shows play, pause, and volume controls |
| `autoplay` | Starts playing automatically on page load |
| `loop` | Repeats the audio when it ends |
| `muted` | Starts the audio muted |
| `preload` | Hints how much data to load (`auto`, `metadata`, `none`) |

### Example

```html
<!-- Audio player with controls, won't autoplay -->
<audio controls preload="metadata">
  <source src="podcast-episode.mp3" type="audio/mpeg">
  Sorry, your browser doesn't support audio playback.
</audio>
```

### Supported Audio Formats

| Format | File Extension | MIME Type |
|---|---|---|
| MP3 | `.mp3` | `audio/mpeg` |
| OGG Vorbis | `.ogg` | `audio/ogg` |
| WAV | `.wav` | `audio/wav` |
| AAC | `.aac` | `audio/aac` |
| WebM | `.webm` | `audio/webm` |

> ✅ **Best Practice:** Always provide **multiple formats** using `<source>` tags. Browsers pick the first format they support.

---

## 🎬 The `<video>` Element

The `<video>` element is used to embed video content on a webpage.

### Basic Syntax

```html
<video controls width="640" height="360">
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Your browser does not support the video element.
</video>
```

### Key Attributes

| Attribute | Description |
|---|---|
| `controls` | Shows play, pause, seek, and volume controls |
| `autoplay` | Plays video automatically (usually requires `muted`) |
| `loop` | Loops the video continuously |
| `muted` | Starts the video without sound |
| `poster` | Image shown before the video plays (like a thumbnail) |
| `width` / `height` | Sets the video player dimensions |
| `preload` | Controls how much is loaded before playback (`auto`, `metadata`, `none`) |
| `playsinline` | Plays inline on mobile instead of fullscreen |

### Example with Poster

```html
<video controls poster="thumbnail.jpg" width="720">
  <source src="intro.mp4" type="video/mp4">
  <source src="intro.webm" type="video/webm">
  Your browser does not support HTML video.
</video>
```

### Supported Video Formats

| Format | File Extension | MIME Type |
|---|---|---|
| MP4 (H.264) | `.mp4` | `video/mp4` |
| WebM (VP8/VP9) | `.webm` | `video/webm` |
| OGG Theora | `.ogv` | `video/ogg` |

> ✅ **Best Practice:** Use **MP4 as the primary format** (widest browser support) and include **WebM as a fallback**.

### Adding Subtitles with `<track>`

```html
<video controls>
  <source src="lesson.mp4" type="video/mp4">
  <track src="subtitles-en.vtt" kind="subtitles" srclang="en" label="English">
  <track src="subtitles-fr.vtt" kind="subtitles" srclang="fr" label="French">
</video>
```

The `<track>` element links a **WebVTT** subtitle/caption file to the video.

---

## 🖼️ The `<iframe>` Element

The `<iframe>` (inline frame) element embeds an **entirely separate HTML document or external webpage** inside your current page. It's the standard way to embed YouTube videos, Google Maps, Figma designs, and more.

### Basic Syntax

```html
<iframe src="https://example.com" width="600" height="400"></iframe>
```

### Key Attributes

| Attribute | Description |
|---|---|
| `src` | URL of the content to embed |
| `width` / `height` | Dimensions of the frame |
| `title` | Describes the iframe content (important for accessibility) |
| `allowfullscreen` | Allows the iframe to go fullscreen |
| `loading` | `lazy` defers loading until iframe is in view |
| `sandbox` | Restricts what the embedded content can do |
| `allow` | Grants specific permissions (e.g., camera, microphone) |

### Embedding a YouTube Video

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID"
  title="YouTube video player"
  allowfullscreen
  loading="lazy">
</iframe>
```

> 💡 Always use the **embed URL** (`/embed/VIDEO_ID`) from YouTube — not the regular watch URL.

### Embedding Google Maps

```html
<iframe
  src="https://www.google.com/maps/embed?pb=YOUR_MAP_PARAMS"
  width="600"
  height="450"
  style="border:0;"
  allowfullscreen
  loading="lazy"
  title="Our Location">
</iframe>
```

### The `sandbox` Attribute (Security)

The `sandbox` attribute restricts iframe capabilities to prevent malicious content from harming your site:

```html
<!-- Most restrictive: blocks everything -->
<iframe src="untrusted.html" sandbox></iframe>

<!-- Allow only scripts -->
<iframe src="widget.html" sandbox="allow-scripts"></iframe>

<!-- Allow scripts and form submissions -->
<iframe src="form.html" sandbox="allow-scripts allow-forms"></iframe>
```

Common `sandbox` values:

| Value | Allows |
|---|---|
| `allow-scripts` | JavaScript execution |
| `allow-forms` | Form submission |
| `allow-same-origin` | Content treated as same origin |
| `allow-popups` | Popups and new tabs |
| `allow-fullscreen` | Fullscreen API |

---

## ⚡ Audio vs Video vs iFrame — Quick Comparison

| Feature | `<audio>` | `<video>` | `<iframe>` |
|---|---|---|---|
| Use Case | Sound files | Video clips | External content |
| Self-hosted | ✅ Yes | ✅ Yes | ✅ / 🌐 Both |
| External URLs | ❌ Limited | ❌ Limited | ✅ Yes |
| Subtitles | ❌ No | ✅ Via `<track>` | Depends on source |
| Security concerns | Low | Low | ⚠️ Use `sandbox` |
| SEO friendly | Medium | Medium | Low |

---

## ♿ Accessibility Tips

- Always add the **`controls`** attribute so keyboard users can operate media.
- Include **`title`** on every `<iframe>` — screen readers use it to describe the frame.
- Add **captions/subtitles** using `<track>` for video content.
- Avoid **`autoplay`** without `muted` — it can be disorienting and inaccessible.
- Provide **fallback text** inside `<audio>` and `<video>` tags for unsupported browsers.

```html
<!-- ✅ Accessible video example -->
<video controls poster="cover.jpg" aria-label="Introduction to HTML">
  <source src="intro.mp4" type="video/mp4">
  <track src="captions.vtt" kind="captions" srclang="en" label="English" default>
  <p>Your browser doesn't support video. <a href="intro.mp4">Download it here</a>.</p>
</video>
```

---

## 🧠 Key Takeaways

- Use **`<audio>`** for music, podcasts, or any sound — always include `controls` and multiple `<source>` formats.
- Use **`<video>`** for embedded clips — add a `poster`, subtitles via `<track>`, and multiple formats.
- Use **`<iframe>`** to embed external content like YouTube or maps — always add a `title` and consider `sandbox` for untrusted sources.
- Provide **fallback content** inside all media elements for older or unsupported browsers.
- Keep **accessibility** in mind: captions, titles, and keyboard-accessible controls matter.

---
