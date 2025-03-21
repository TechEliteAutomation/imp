## **Implementation Document for techeliteautomation.com**

### **Overview**

This document outlines the steps to set up and deploy your website to GitHub Pages, using the domain **techeliteautomation.com**. The website will consist of the following pages:
1. **Landing Page** (`index.md`)
2. **Services Page** (`services.md`)
3. **Portfolio Page** (`portfolio.md`)
4. **Contact Page** (`contact.md`)

The website will be deployed on GitHub Pages, leveraging a static site generator like **Jekyll** for easy management.

---

### **Steps for Deployment**

#### **1. Set Up GitHub Repository**

1. **Create a GitHub Repository:**
   - Go to GitHub and create a new repository named `tea`.
   - Initialize with a README if desired (optional).

2. **Clone the Repository:**
   ```bash
   git clone https://github.com/TechEliteAutomation/tea.git
   cd tea
   ```

---

#### **2. Install Jekyll and Dependencies on Arch Linux**

1. **Install Ruby and Bundler (if not already installed):**
   ```bash
   sudo pacman -S ruby
   gem install bundler
   ```

2. **Install Jekyll:**
   ```bash
   gem install jekyll
   ```

3. **Initialize Jekyll Site:**
   ```bash
   jekyll new .
   ```

4. **Install Dependencies:**
   ```bash
   bundle install
   ```

---

#### **3. Update the Directory Structure**

Structure the repository as follows:

```plaintext
tea/
├── assets/
│   ├── css/
│   │   └── main.css
│   ├── images/
│   │   ├── logo.png
│   │   └── banner.jpg
│   ├── js/
│   │   └── main.js
├── _includes/
│   ├── header.html
│   ├── footer.html
│   └── navbar.html
├── _layouts/
│   └── default.html
├── _posts/
│   └── (optional: blog posts if needed)
├── index.md
├── services.md
├── portfolio.md
├── contact.md
├── _config.yml
└── README.md
```

---

#### **4. Configure Jekyll and GitHub Pages**

1. **Edit `_config.yml`:**
   ```yaml
   title: TechEliteAutomation
   description: AI-powered automation and custom solutions for businesses.
   url: https://techeliteautomation.com
   baseurl: ""
   theme: minima

   # GitHub Pages-specific settings
   github:
     repository: TechEliteAutomation/tea
   ```

2. **Enable GitHub Pages:**
   - Go to your GitHub repository's **Settings**.
   - Scroll down to the **GitHub Pages** section.
   - Set the **Source** to `main` and select the `/ (root)` directory.
   - Your site will be accessible via `https://techeliteautomation.github.io/tea/`.

---

#### **5. Add Custom HTML Components**

1. **Header (`_includes/header.html`)**
2. **Footer (`_includes/footer.html`)**
3. **Navbar (`_includes/navbar.html`)**

---

#### **6. Content for Pages**

1. **Landing Page (`index.md`)**
2. **Services Page (`services.md`)**
3. **Portfolio Page (`portfolio.md`)**
4. **Contact Page (`contact.md`)**

---

#### **7. Deploy the Site to GitHub Pages**

1. **Push to GitHub:**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Enable Custom Domain:**
   - Add `techeliteautomation.com` as your custom domain in GitHub Pages settings.
   - Add a `CNAME` file:
   ```plaintext
   techeliteautomation.com
   ```

3. **Update DNS Records:**
   - Configure the CNAME and A records as needed.

---

#### **8. Final Testing**

1. **Verify the site** at `https://techeliteautomation.com`
2. **Test navigation**

---

### **Conclusion**

Once completed, your website will be live at **techeliteautomation.com** using the `tea` repository on GitHub Pages.

