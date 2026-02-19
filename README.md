<p align="center"><img src="public/images/favicon-no-bg.svg" width="80"></p>
<h1 align="center">PDF Tools</h1>
<p align="center">
  <a href="https://www.digitalocean.com/?refcode=d93c189ef6d0&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge">
    <img src="https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%203.svg" alt="DigitalOcean Referral Badge">
  </a>
</p>

**PDF Tools** is based on **BentoPDF**, "a powerful, privacy-first, client-side PDF toolkit that is self hostable and allows you to manipulate, edit, merge, and process PDF files directly in your browser. No server-side processing is required, ensuring your files remain secure and private.""

**PDF Tools** adds some customizations, namely the ability to set use GitHub pages and a custom subdomain versus the standard subfolder method that **BentoPDF** uses. It also adds Japanese translations and the Google Translate bar to support other languages.

Please read **BentoPDF**'s documentation if you want to set up your own version of **BentoPDF**.

[![BuyMeACoffee](https://img.shields.io/badge/Buy%20me%20a%20Coffee-yellow?logo=buymeacoffee&style=flat-square)](https://buymeacoffee.com/tgmgroup) ![Ko-fi](https://img.shields.io/badge/Buy%20me%20a%20Coffee-yellow?logo=kofi&style=flat-square)](https://ko-fi.com/tgmgroup) ![GitHub Stars](https://img.shields.io/github/stars/tgmgroup/pdftools?style=social)
[![Sponsor me on GitHub](https://img.shields.io/badge/Sponsor-%E2%9D%A4-ff69b4)](https://github.com/sponsors/tgmgroup)

![BentoPDF Tools](public/images/bentopdf-tools.png)

---

## Table of Contents

- [Documentation](#-documentation)
- [Static Hosting](#-static-hosting-using-github-pages)
- [Customization](#-custom-branding-and-other-options)
- [Translation](#-translations)
- [Special Thanks](#special-thanks)

---

## 📚 Documentation

[![Documentation](https://img.shields.io/badge/Docs-VitePress-646cff?style=for-the-badge&logo=vite&logoColor=white)](https://bentopdf.com/docs/)

Visit **BentoPDF**'s [Documentation](https://bentopdf.com/docs/) for:

- **Getting Started** guide
- **Tools Reference** (50+ tools)
- **Self-Hosting** guides (Docker, Vercel, Netlify, Cloudflare, AWS, Hostinger, Nginx, Apache)
- **Contributing** guide
- **Commercial License** details

---

## 🚀 Static Hosting using Github Pages

**BentoPDF** makes it easy to host things statically. However, it prefers to use subdirectories off a base domain (www.domain.com/bentopdf) instead of subdomains. This **PDF Tools** fork fixes the regexp code to allow hosting on sub or base domains. (pdftools.domain.com). The main change is this code:
`// Original Code // return (process.env.BASE_URL || '/').replace(/\/$/, '');`
`// Modified Code // return (process.env.BASE_URL || '/').replace(/\/+$/, '') || '/';`
Search for BaseURL and you'll find multiple instances of this kind of code. You will have to edit `vite.config.ts` and `i18n.ts` at the least.

Also, there are some issues with using Github's environment variables. You will have to do a CTRL+F search to replace all the BentoPDF branding. See the original documentation ([Static Hosting](https://github.com/alam00000/bentopdf/blob/main/STATIC-HOSTING.md)) for the basic procedures.

---

## 🎨 Custom Branding and Other Options

Use environment variables to add your own custom branding or edit the other options.

| Variable                | Description                                           | Default                                            |
| ----------------------- | ----------------------------------------------------- | -------------------------------------------------- |
| `VITE_BRAND_NAME`       | Brand name shown in header and footer                 | `BentoPDF`                                         |
| `VITE_BRAND_LOGO`       | Path to logo file relative to `public/`               | `images/favicon-no-bg.svg`                         |
| `VITE_FOOTER_TEXT`      | Custom footer/copyright text                          | `© 2026 BentoPDF. All rights reserved.`            |
| `SIMPLE_MODE`           | Remove much of the "marketing fluff"                  | `Testimonials, extra tools, etc.`                  |
| `BASE_URL`              | Set a subdirectory, or use `/` for the base/subdomain | `www.example.com/pdftools or pdftools.example.com` |
| `VITE_DEFAULT_LANGUAGE` | Not everyone is an English speaker.                   | `www.example.com/ja/`                              |

You will also probably want to edit the base HTML files to change the branding to something you'd prefer. The base environment variables do affect branding in many places, but there remain many places that they don't touch.

## 🌍 Translations

**BentoPDF** is available in multiple languages: `en|ar|fr|es|de|zh|zh-TW|vi|tr|id|it|pt|nl|be|da`
**PDF Tools** adds `ja` to this. Edit the files in `public/locales` and the `i18n.ts` file in `src/js/i18n` to add more languages.

---

## Special Thanks

A big thanks to [Alam00000](https://github.com/alam00000/bentopdf/) and his **BentoPDF**. Also, thanks to all the work he's built on to make this happen:

**Bundled Libraries:**

- **[PDFLib.js](https://pdf-lib.js.org/)** – For enabling powerful client-side PDF manipulation.
- **[PDF.js](https://mozilla.github.io/pdf.js/)** – For the robust PDF rendering engine in the browser.
- **[PDFKit](https://pdfkit.org/)** – For creating and editing PDFs with ease.
- **[EmbedPDF](https://github.com/embedpdf/embed-pdf-viewer)** – For seamless PDF editing in pure JS.
- **[Cropper.js](https://fengyuanchen.github.io/cropperjs/)** – For intuitive image cropping functionality.
- **[Vite](https://vitejs.dev/)** – For lightning-fast development and build tooling.
- **[Tailwind CSS](https://tailwindcss.com/)** – For rapid, flexible, and beautiful UI styling.
- **[qpdf](https://github.com/qpdf/qpdf)** and **[qpdf-wasm](https://github.com/neslinesli93/qpdf-wasm)** – For inspecting, repairing, and transforming PDF files.
- **[LibreOffice](https://www.libreoffice.org/)** – For powerful document conversion capabilities.

**AGPL Libraries (Pre-configured via CDN):**

- **[CoherentPDF (cpdf)](https://www.coherentpdf.com/)** – For content-preserving PDF operations. _(AGPL-3.0)_
- **[PyMuPDF](https://github.com/pymupdf/PyMuPDF)** – For high-performance PDF manipulation and data extraction. _(AGPL-3.0)_
- **[Ghostscript (GhostPDL)](https://github.com/ArtifexSoftware/ghostpdl)** – For PDF/A conversion and font outlining. _(AGPL-3.0)_

> [!NOTE]
> AGPL-licensed libraries are not bundled in PDF Tools' (and the base BentoPDF's) source code. They are loaded at runtime from CDN (pre-configured) and can be overridden via environment variables or Advanced Settings.
