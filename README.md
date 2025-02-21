# 📌 **How to Embed an Interactive Sidebar & Navigation Bar in Power BI**  

This guide explains how to integrate an **interactive sidebar and top navigation bar** into Power BI using an **HTML Content Visualization** with hosted JavaScript and CSS files. The approach ensures full interactivity and responsiveness.  

---

## **🛠️ Step 1: Prepare Your HTML, CSS, and JavaScript Files**  

Before embedding the interactive sidebar in Power BI, you need the following files:  
1. **HTML** – The structure of your sidebar and navigation bar.  
2. **CSS** – The styles that control the design and layout.  
3. **JavaScript** – The script that enables interactions (such as sidebar toggling).  

### **📂 File Structure**
Here’s how your project files should be structured before hosting:  
```
/PowerBI_Scripts
  ├── index.html
  ├── style.css
  ├── script.js
```

---

## **🌍 Step 2: Host Your Files Using GitHub Pages**  

Since Power BI does not allow direct script execution, you must **host your JavaScript and CSS** externally. GitHub Pages is an easy and free way to do this.

### **1️⃣ Create a GitHub Repository**
1. Go to [GitHub](https://github.com/) and log in.  
2. Click on **New Repository**.  
3. Name it something like `PowerBI_Scripts_Interactive-Sidebar-Navigation-Bar` and set it to **Public**.  
4. Click **Create Repository**.  

### **2️⃣ Upload Your Files**
1. Navigate to your new repository.  
2. Click the **Add file** button → **Upload files**.  
3. Drag and drop your `index.html`, `style.css`, and `script.js` files.  
4. Click **Commit changes**.  

### **3️⃣ Enable GitHub Pages**
1. Go to **Settings** in your repository.  
2. Click **Pages** in the left sidebar.  
3. Under **Branch**, select `main` and click **Save**.  
4. GitHub will generate a link for your hosted files:  
   ```
   https://YOUR_GITHUB_USERNAME.github.io/PowerBI_Scripts/
   ```
   (For you, it’s **`https://nicholaspannun.github.io/PowerBI_Scripts_Interactive-Sidebar-Navigation-Bar/`**)

---

## **📌 Step 3: Use DAX to Reference Your Hosted Files**  

Once your files are hosted, you can embed them in **Power BI’s HTML Content Visualization** using **DAX code**.

### **1️⃣ Open Power BI and Add an HTML Content Visualization**
1. Open your Power BI report.  
2. Go to **Visualizations** → Add an **HTML Content Visualization**.  
3. Create a **new measure** (or column) for your HTML code.

### **2️⃣ Use DAX to Reference Your Hosted Files**  
Create a new measure in Power BI and add this DAX code:  
```DAX
HtmlContent = "
<!DOCTYPE html>
<html lang='en'>
<head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>Responsive Sidebar in Power BI</title>
    <style>
        /* Ensure the iframe fits the Power BI report and is responsive */
        iframe {
            width: 100%;
            height: 100vh; /* Adjust height to the full screen view */
            border: none;
        }

        /* Additional custom CSS to make the content responsive */
        @media (max-width: 768px) {
            iframe {
                height: 90vh; /* Reduce height on smaller screens */
            }
        }

        @media (max-width: 480px) {
            iframe {
                height: 80vh; /* Further reduce height for very small screens */
            }
        }
    </style>
</head>
<body>
    <!-- Embed the hosted content in the iframe -->
    <iframe src='https://nicholaspannun.github.io/PowerBI_Scripts_Interactive-Sidebar-Navigation-Bar/'></iframe>
</body>
</html>
"
```
- This embeds your hosted sidebar and navigation bar into Power BI.  
- The CSS inside the `<style>` tag ensures responsiveness on different screen sizes.  

---

## **🎨 Step 4: Ensure Responsiveness for Power BI**  

To make sure the embedded sidebar adjusts properly to different screen sizes in Power BI:  
- The **DAX code already includes responsive CSS** using `@media` queries.  
- Test it in **Power BI Desktop and Power BI Service** to check how it resizes.  
- Modify the `height` values in the DAX code if needed.  

---

## **🛠️ Troubleshooting Guide**  

If something doesn’t work, check these common issues:  

### ❌ **1. Sidebar or Menu Clicks Don’t Work**
✅ Make sure your JavaScript is loading correctly in `script.js`.  
✅ Check the **console** in the browser (press `F12` → Console tab).  

### ❌ **2. Styles Don’t Apply**
✅ Verify that the `style.css` file is correctly linked in `index.html`.  
✅ Try opening `https://nicholaspannun.github.io/PowerBI_Scripts/style.css` in a browser—if it doesn’t load, your file isn’t hosted properly.  

### ❌ **3. Sidebar Looks Too Big or Small in Power BI**
✅ Adjust the height inside the `<iframe>` in your DAX code (`height: 100vh;`).  
✅ Use media queries in your CSS to make it **fully responsive**.  

---

## **✅ Final Thoughts**  

By following this guide, you can **fully integrate a sidebar and top navigation bar** in Power BI with all interactions working correctly. Hosting files on GitHub Pages allows for easy updates—just modify the files in GitHub, and Power BI will reflect the changes automatically.  
