# Ex.08 Design of Interactive Image Gallery
# Date:16/11/2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
imagegallery.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Fullscreen Gallery</title>
    <link rel="stylesheet" href="fullscreen-styles.css">
    <script defer src="fullscreen-script.js"></script>
</head>
<body>
    <header>
        <h1>Interactive Gallery</h1>
        <nav>
            <ul>
                <li><a href="#" id="filter-all">All</a></li>
                <li><a href="#" id="filter-nature">Nature</a></li>
                <li><a href="#" id="filter-architecture">Architecture</a></li>
                <li><a href="#" id="filter-people">People</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <div class="gallery" id="gallery">
            
        </div>
    </main>

    <footer>
        <p>&copy; 2024 Interactive  Gallery</p>
    </footer>

    <div id="fullscreen-modal" class="fullscreen-modal">
        <span id="close-modal">&times;</span>
        
    </div>
</body>
</html>

fullscreen-styles.css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f8f9fa;
}

header {
    background-color: #343a40;
    color: white;
    padding: 1rem;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
    display: flex;
    justify-content: center;
    gap: 1rem;
}

nav a {
    color: white;
    text-decoration: none;
}

.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
    padding: 1rem;
}

.gallery img {
    width: 100%;
    height: auto;
    border-radius: 5px;
    cursor: pointer;
    transition: transform 0.3s;
}

.gallery img:hover {
    transform: scale(1.05);
}

footer {
    background-color: #343a40;
    color: white;
    text-align: center;
    padding: 1rem;
    position: fixed;
    bottom: 0;
    width: 100%;
}
fullscreen-script.js
const galleryData = [
    { src: "images/nature1.jpg", category: "nature" },
    { src: "images/architecture1.jpg", category: "architecture" },
    { src: "images/people1.jpg", category: "people" },
    { src: "images/nature2.jpg", category: "nature" },
    { src: "images/architecture2.jpg", category: "architecture" },
    { src: "images/people2.jpg", category: "people" }
];

document.addEventListener("DOMContentLoaded", () => {
    const gallery = document.getElementById("gallery");
    const filterAll = document.getElementById("filter-all");
    const filterNature = document.getElementById("filter-nature");
    const filterArchitecture = document.getElementById("filter-architecture");
    const filterPeople = document.getElementById("filter-people");

    const renderGallery = (filter = null) => {
        gallery.innerHTML = "";
        galleryData
            .filter(item => !filter || item.category === filter)
            .forEach(item => {
                const img = document.createElement("img");
                img.src = item.src;
                img.alt = item.category;
                img.addEventListener("click", () => {
                    const newWindow = window.open("", "_blank");
                    newWindow.document.write(
                        `<html><head><title>Image View</title></head><body style='margin:0;display:flex;justify-content:center;align-items:center;background-color:black;'>` +
                        `<img src='${item.src}' style='max-width:100%;max-height:100%;'>` +
                        `</body></html>`
                    );
                });
                gallery.appendChild(img);
            });
    };

    renderGallery();

    filterAll.addEventListener("click", () => renderGallery());
    filterNature.addEventListener("click", () => renderGallery("nature"));
    filterArchitecture.addEventListener("click", () => renderGallery("architecture"));
    filterPeople.addEventListener("click", () => renderGallery("people"));
});


```
# OUTPUT:
![image gallery 1](https://github.com/user-attachments/assets/5e067633-9aaa-42aa-861f-5c72e99f5c39)
![image gallery2](https://github.com/user-attachments/assets/9bcc225b-fd3b-4575-b67c-ef422f66d541)
![image gallery 2](https://github.com/user-attachments/assets/954de3ce-f081-407b-ad35-f7e6a8e64690)



# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
