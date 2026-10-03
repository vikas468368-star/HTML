# 🪪 EWT Identity Card — HTML Project

<div align="center">

<h1>✨ EWT Identity Card Template</h1>

<p>
A modern, elegant and print-ready Identity Card design built using
<strong>HTML5</strong>, <strong>CSS3</strong> and <strong>SVG</strong>.
</p>

<p>
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
  <img src="https://img.shields.io/badge/SVG-FFB13B?style=for-the-badge&logo=svg&logoColor=black">
  <img src="https://img.shields.io/badge/Responsive-Yes-22C55E?style=for-the-badge">
</p>

<br>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=8B5CF6&center=true&vCenter=true&width=600&lines=Modern+Identity+Card+Design;HTML+%2B+CSS+%2B+SVG;Clean+%26+Professional+UI;Print-Ready+CR80+Card" alt="Typing Animation">

</div>

---

## 🌟 About The Project

**EWT Identity Card** is a clean and professional identity-card template created using pure frontend technologies.

The project demonstrates how **HTML, CSS and SVG** can be combined to create a visually polished ID card without requiring a frontend framework.

The design includes:

- 🎨 Modern navy, gold and cream color palette
- 🪪 Front and back identity card layouts
- ✨ SVG-based graphical elements
- 🔤 Custom typography
- 📱 Responsive screen preview
- 🖨️ Print-ready card dimensions
- 💎 Elegant shadows and borders
- 🧩 Reusable CSS design tokens
- 📐 CR80 standard card sizing for printing

---

## 🚀 Live Preview

<div align="center">

### 🔗 View the Project

**[👉 Open EWT Identity Card](https://vikas468368-star.github.io/HTML/card.html)**

</div>

> If GitHub Pages is not enabled yet, go to  
> **Repository → Settings → Pages → Deploy from branch → main**

---

## 🎯 Project Preview

The project creates a professional identity-card interface containing:

```text
┌─────────────────────────────────────────────┐
│                                             │
│   EWT       OFFICIAL IDENTITY CARD     📷   │
│                                             │
│   ◉        NAME                             │
│   EWT      Full Name                        │
│                                             │
│            POSITION                          │
│            Student / Employee               │
│                                             │
│            ID NUMBER                         │
│            EWT-000001                        │
│                                             │
└─────────────────────────────────────────────┘
```

---

## ✨ Features

### 🎨 Modern Visual Design

The interface uses a carefully selected visual system:

| Element | Style |
|---|---|
| Primary Color | Navy |
| Accent | Gold |
| Background | Cream |
| Secondary Accent | Teal |
| Typography | Fraunces + Inter |
| Data Font | IBM Plex Mono |

The original card implementation defines reusable design tokens for colors, typography and layout.

---

### 🪪 Front & Back Card

The project contains separate designs for:

- **Front of Identity Card**
- **Back of Identity Card**

The cards are presented together on the webpage for easy preview.

---

### 📐 Print Ready

The project includes dedicated print CSS.

The card uses the standard:

```text
3.375 × 2.125 inches
```

CR80-style dimensions, making the design suitable for physical ID-card printing.

---

### 🧬 SVG Graphics

The card uses SVG to create graphical elements such as:

- Logo / monogram
- Borders
- Decorative lines
- Background patterns
- Watermarks
- Photo placeholder
- Card structure

This keeps the graphics sharp at different resolutions.

---

## 🛠️ Technologies Used

<div align="center">

| Technology | Purpose |
|---|---|
| 🟠 HTML5 | Page structure |
| 🔵 CSS3 | Styling and layout |
| 🟡 SVG | Card graphics and illustrations |
| 🔤 Google Fonts | Typography |
| 🖨️ CSS Print Media | Physical card printing |

</div>

---

## 📂 Project Structure

```text
HTML/
│
├── 📄 card.html
│
└── 📄 README.md
```

### `card.html`

The main webpage containing:

- Identity card layout
- HTML structure
- CSS styling
- SVG graphics
- Responsive layout
- Print configuration

### `README.md`

Project documentation and setup instructions.

---

## 💻 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/vikas468368-star/HTML.git
```

### 2️⃣ Open the Project

```bash
cd HTML
```

### 3️⃣ Run the Project

Simply open:

```text
card.html
```

in your browser.

No backend or package installation is required.

---

## 🎨 Customization

You can easily customize the identity card by modifying the CSS design tokens.

For example:

```css
:root {
    --ink: #16233F;
    --ink-soft: #233457;
    --gold: #B8863B;
    --gold-light: #D9B677;
    --cream: #F4EFE3;
    --white: #FFFFFF;
    --slate: #5B6472;
    --teal: #2F6F62;
}
```

### Change Colors

For example:

```css
--gold: #7C3AED;
```

or:

```css
--gold: #0EA5E9;
```

You can create your own color theme without redesigning the complete card.

---

## ✏️ Personalize the Card

You can replace the placeholder information:

```text
Full Name
Position
ID Number
Institution Name
Photo
```

with your own information.

You can also replace the placeholder logo with your own organization or college logo.

---

## 🖨️ Printing

To print the card:

1. Open `card.html`
2. Press:

```text
Ctrl + P
```

3. Select your printer or **Save as PDF**
4. Check the print preview
5. Print the card

The project contains print-specific CSS that hides unnecessary webpage elements and preserves the card dimensions.

---

## 🌈 Design Philosophy

The design follows a minimal professional identity-card aesthetic.

### Visual hierarchy

```text
          LOGO
           ↓
     CARD TITLE
           ↓
        PHOTO
           ↓
        NAME
           ↓
       POSITION
           ↓
       ID NUMBER
```

The combination of dark navy, metallic-gold accents and cream backgrounds gives the card a premium institutional appearance.

---

## 🔮 Future Improvements

Possible improvements include:

- [ ] Add a real profile-photo upload
- [ ] Add QR-code generation
- [ ] Add barcode support
- [ ] Add downloadable PDF generation
- [ ] Add editable form fields
- [ ] Add multiple card templates
- [ ] Add dark/light themes
- [ ] Add organization logo upload
- [ ] Add automatic ID generation
- [ ] Add JavaScript-based card customization
- [ ] Add animated webpage background
- [ ] Add live card preview

---

## 🤝 Contributing

Contributions are welcome!

If you have an idea to improve the project:

1. Fork the repository
2. Create a new branch

```bash
git checkout -b feature/improvement
```

3. Make your changes
4. Commit your changes

```bash
git commit -m "Add new improvement"
```

5. Push the branch

```bash
git push origin feature/improvement
```

6. Open a Pull Request

---

## 📜 License

This project is available for learning and personal development purposes.

If you reuse or modify the project, consider giving credit to the original repository.

---

## 👨‍💻 Author

<div align="center">

### **Vikas Madheshiya**

💻 Web Development & Programming  
🚀 Building practical software projects  
🌱 Continuously learning and experimenting with new technologies

<br>

<a href="https://github.com/vikas468368-star">
<img src="https://img.shields.io/badge/GitHub-vikas468368--star-181717?style=for-the-badge&logo=github">
</a>

</div>

---

<div align="center">

### ⭐ If you found this project useful, consider giving it a star!

<br>

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20,24&height=120&section=footer">

</div>
