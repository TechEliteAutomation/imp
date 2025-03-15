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
   - Go to GitHub and create a new repository named `techeliteautomation.com`.
   - Initialize with a README if desired (optional).

2. **Clone the Repository:**
   ```bash
   git clone https://github.com/TechEliteAutomation/web.git
   cd web
   ```

---

#### **2. Install Jekyll and Dependencies**

1. **Install Ruby and Bundler (if not already installed):**
   - Follow the instructions here: [Jekyll Installation Guide](https://jekyllrb.com/docs/installation/).

2. **Install Jekyll:**
   ```bash
   gem install jekyll bundler
   ```

3. **Initialize Jekyll Site:**
   In the root of your project folder, initialize a new Jekyll site:
   ```bash
   jekyll new .
   ```

   This will create the basic Jekyll folder structure.

4. **Install Dependencies:**
   Run the following command to install Jekyll dependencies:
   ```bash
   bundle install
   ```

---

#### **3. Update the Directory Structure**

Structure the repository as follows:

```plaintext
techeliteautomation.com/
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

1. **assets/**: Contains static files like CSS, JS, and images.
2. **_includes/**: Contains reusable HTML fragments (header, footer, navbar).
3. **_layouts/**: Contains layout templates (default layout for all pages).
4. **_posts/**: Directory for blog posts (if you add a blog later).
5. **index.md**: Landing page for your site.
6. **services.md**: Page listing your services.
7. **portfolio.md**: A page linking to your GitHub profile.
8. **contact.md**: Page with a contact form (separate from landing page).
9. **_config.yml**: Configuration for your Jekyll site.
10. **README.md**: (Optional) Describes your project.

---

#### **4. Configure Jekyll and GitHub Pages**

1. **Edit `_config.yml`:**
   Modify the Jekyll configuration file to customize your website:
   
   ```yaml
   title: TechEliteAutomation
   description: AI-powered automation and custom solutions for businesses.
   url: https://techeliteautomation.com
   baseurl: ""
   theme: minima  # or a custom theme if desired

   # GitHub Pages-specific settings
   github:
     repository: your-username/techeliteautomation.com
   ```

2. **Enable GitHub Pages:**
   - Go to your GitHub repository's **Settings**.
   - Scroll down to the **GitHub Pages** section.
   - Set the **Source** to `main` (or `master`) and select the `/ (root)` directory.
   - Your site will be accessible via `https://your-username.github.io/techeliteautomation.com/`.

---

#### **5. Add Custom HTML Components**

1. **Header (`_includes/header.html`):**
   Contains the website's header, including the navigation bar and logo.
   
   ```html
   <header>
     <img src="/assets/images/logo.png" alt="TechEliteAutomation Logo">
     <nav>
       <ul>
         <li><a href="/">Home</a></li>
         <li><a href="/services">Services</a></li>
         <li><a href="/portfolio">Portfolio</a></li>
         <li><a href="/contact">Contact</a></li>
       </ul>
     </nav>
   </header>
   ```

2. **Footer (`_includes/footer.html`):**
   Contains footer information.
   
   ```html
   <footer>
     <p>&copy; 2025 TechEliteAutomation</p>
   </footer>
   ```

3. **Navbar (`_includes/navbar.html`):**
   Can be included within the header or a separate file for navigation.
   
   ```html
   <nav>
     <ul>
       <li><a href="/">Home</a></li>
       <li><a href="/services">Services</a></li>
       <li><a href="/portfolio">Portfolio</a></li>
       <li><a href="/contact">Contact</a></li>
     </ul>
   </nav>
   ```

---

#### **6. Content for Pages**

1. **Landing Page (`index.md`):**
   - Include a brief introduction to your services and a CTA (e.g., "Request a Free Consultation").
   - Link to the services page and contact page.

   Example:
   ```markdown
   ---
   layout: default
   title: Home
   ---
   # Welcome to TechEliteAutomation

   We specialize in AI-powered automation and custom software solutions to optimize business processes.

   [Request a Free Consultation](#contact)

   ## Our Services
   - Custom AI Solutions
   - AI-powered Workflow Automation
   - AI Consulting

   [Learn More About Our Services](services)
   ```

2. **Services Page (`services.md`):**
   - List and describe the services you offer (AI solutions, consulting, automation).
   
   Example:
   ```markdown
   ---
   layout: default
   title: Services
   ---
   # Our Services

   ## Custom AI Solutions
   We design and develop custom AI agents tailored to your business needs.

   ## AI Workflow Automation
   Automate business processes and workflows with AI-driven systems.

   ## Consulting & Strategy
   Expert guidance to integrate AI into your business for long-term success.
   ```

3. **Portfolio Page (`portfolio.md`):**
   - Directly link to your GitHub or any other portfolio repositories.
   
   Example:
   ```markdown
   ---
   layout: default
   title: Portfolio
   ---
   # My Portfolio

   Visit my [GitHub Profile](https://github.com/your-username) to explore my projects and AI solutions.
   ```

4. **Contact Page (`contact.md`):**
   - Include a contact form or an email link for inquiries.
   
   Example:
   ```markdown
   ---
   layout: default
   title: Contact
   ---
   # Contact Us

   For inquiries or to discuss your project, please reach out:

   - Email: [your-email@domain.com](mailto:your-email@domain.com)
   ```

---

#### **7. Deploy the Site to GitHub Pages**

1. **Push to GitHub:**
   - Add all your files to the repository and push them.
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Enable Custom Domain:**
   - In the GitHub repository **Settings**, under **GitHub Pages**, add `techeliteautomation.com` as your custom domain.
   - Add a `CNAME` file to the root of the repository with the following content:
   ```plaintext
   techeliteautomation.com
   ```

3. **Update DNS Records:**
   - Go to your domain registrar (e.g., Namecheap, GoDaddy) and update the DNS settings.
     - Set a CNAME record for `www` pointing to `your-username.github.io`.
     - If using an apex domain (without `www`), configure an A record pointing to GitHub Pages' IPs:  
       `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.

---

#### **8. Final Testing**

1. **Verify the site**: Access `https://techeliteautomation.com` to ensure everything is deployed correctly.
2. **Test navigation**: Ensure all links between the pages work as expected.

---

### **Conclusion**

Once the steps above are completed, your website will be live at **techeliteautomation.com**. GitHub Pages ensures a free and reliable hosting solution, and with Jekyll, you have an efficient platform for managing and deploying the content.
