<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DRD DOMAIN</title>
    <style>
        /* CSS Variables for Genuine Notion-Style Theme */
        :root {
            /* Notion Light Theme Colors */
            --bg-color: #ffffff;
            --text-primary: #37352f;
            --text-secondary: #787774;
            --card-bg: #f1f1ef;
            --input-bg: #f4f5f6;
            --glass-border: 1px solid rgba(55, 53, 47, 0.09);
            --accent-color: #2383e2;
            --accent-hover: #1a6ab4;
            --danger-color: #eb5757;
            --shadow: 0px 1px 2px rgba(15, 15, 15, 0.1);
            --modal-overlay: rgba(15, 15, 15, 0.4);
            --lightbox-bg: rgba(15, 15, 15, 0.95);
            --radius-lg: 12px; /* Notion uses subtler radiuses */
            --radius-md: 6px;
            --transition: all 0.2s ease-in-out;
        }

        /* Notion Dark Theme Colors */
        body.dark-theme {
            --bg-color: #191919;
            --text-primary: #e3e3e3;
            --text-secondary: #9b9b9b;
            --card-bg: #202020;
            --input-bg: #252525;
            --glass-border: 1px solid rgba(255, 255, 255, 0.09);
            --accent-color: #2eaadc;
            --accent-hover: #1c8cb9;
            --danger-color: #ff7369;
            --shadow: 0px 1px 2px rgba(0, 0, 0, 0.4);
            --modal-overlay: rgba(0, 0, 0, 0.6);
            --lightbox-bg: rgba(0, 0, 0, 0.98);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-primary);
            -webkit-font-smoothing: antialiased;
            padding: 40px 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        .widget-container { width: 100%; max-width: 900px; }

        header { text-align: center; margin-bottom: 40px; }
        header h1 { font-size: 32px; font-weight: 700; letter-spacing: -0.015em; margin-bottom: 8px; }
        header p { font-size: 16px; color: var(--text-secondary); font-weight: 400; }

        /* Upload Section */
        .upload-section {
            background: var(--card-bg);
            border: var(--glass-border);
            border-radius: var(--radius-lg);
            padding: 24px;
            box-shadow: var(--shadow);
            margin-bottom: 40px;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .input-group { display: flex; flex-direction: column; gap: 6px; }
        .input-group label { font-size: 12px; font-weight: 500; color: var(--text-secondary); text-transform: uppercase; letter-spacing: 0.5px; }
        
        input[type="text"], input[type="file"] {
            width: 100%; padding: 10px 14px; border-radius: var(--radius-md);
            border: var(--glass-border); background: var(--input-bg);
            color: var(--text-primary); font-size: 15px; font-family: inherit; transition: var(--transition);
        }
        input[type="text"]::placeholder { color: var(--text-secondary); opacity: 0.6; }
        input[type="text"]:focus { outline: none; border-color: var(--accent-color); }
        
        input[type="file"]::file-selector-button {
            background-color: var(--bg-color); border: var(--glass-border);
            color: var(--text-primary); border-radius: 4px; padding: 6px 12px; margin-right: 12px;
            cursor: pointer; font-weight: 500; transition: var(--transition);
        }
        input[type="file"]::file-selector-button:hover { background-color: var(--card-bg); }
        
        .btn-submit {
            background-color: var(--accent-color); color: white; border: none;
            padding: 10px 20px; border-radius: var(--radius-md); font-size: 15px;
            font-weight: 500; cursor: pointer; transition: var(--transition); align-self: flex-end;
        }
        .btn-submit:hover { background-color: var(--accent-hover); }
        .btn-submit:disabled { opacity: 0.5; cursor: not-allowed; }

        /* Gallery Grid */
        .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 20px; }
        
        .empty-state { text-align: center; grid-column: 1 / -1; color: var(--text-secondary); padding: 40px; font-size: 16px; }

        .card {
            background: var(--card-bg); border: var(--glass-border); border-radius: var(--radius-lg);
            overflow: hidden; box-shadow: var(--shadow); transition: var(--transition);
            cursor: pointer; position: relative;
            animation: fadeIn 0.4s ease forwards;
        }
        .card:hover { transform: translateY(-2px); box-shadow: 0 4px 12px rgba(15, 15, 15, 0.15); }

        .card-image { width: 100%; height: 200px; object-fit: cover; background-color: var(--input-bg); }
        .photo-count {
            position: absolute; top: 12px; right: 12px;
            background: rgba(15, 15, 15, 0.6); color: white; font-size: 11px; font-weight: 600; padding: 4px 10px; border-radius: 4px;
        }
        .card-content { padding: 16px; display: flex; justify-content: space-between; align-items: center; }
        .card-text { display: flex; flex-direction: column; }
        .card-title { font-size: 16px; font-weight: 600; margin-bottom: 4px; }
        .card-date { font-size: 13px; color: var(--text-secondary); }
        
        .btn-delete {
            background: none; border: none; color: var(--danger-color); font-size: 18px;
            cursor: pointer; padding: 6px; border-radius: 4px; transition: background 0.2s;
        }
        .btn-delete:hover { background: rgba(235, 87, 87, 0.1); }

        /* Album Modal */
        .modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: var(--modal-overlay); display: flex; justify-content: center; align-items: flex-end; 
            opacity: 0; pointer-events: none; transition: opacity 0.3s ease; z-index: 100;
        }
        .modal.active { opacity: 1; pointer-events: auto; }
        
        .modal-content {
            background: var(--bg-color); width: 100%; max-width: 900px; height: 85vh;
            border-radius: 12px 12px 0 0; padding: 24px; overflow-y: auto;
            transform: translateY(100%); transition: transform 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
            box-shadow: 0 -4px 24px rgba(0,0,0,0.15); position: relative;
            border-top: var(--glass-border);
        }
        .modal.active .modal-content { transform: translateY(0); }
        
        .close-btn {
            position: sticky; top: 0; float: right; background: var(--card-bg); border: var(--glass-border);
            color: var(--text-primary); width: 32px; height: 32px; border-radius: 4px; font-size: 16px; cursor: pointer;
            display: flex; align-items: center; justify-content: center; z-index: 2; margin-bottom: -32px;
        }

        .modal-title { font-size: 24px; font-weight: 700; margin-bottom: 20px; padding-top: 10px;}
        .album-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 12px; }
        .album-item {
            width: 100%; aspect-ratio: 1; object-fit: cover; border-radius: 6px;
            cursor: pointer; transition: transform 0.2s; background-color: var(--input-bg);
        }
        .album-item:hover { transform: scale(1.02); }

        /* Lightbox */
        .lightbox {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: var(--lightbox-bg); display: flex; justify-content: center; align-items: center;
            opacity: 0; pointer-events: none; transition: opacity 0.3s ease; z-index: 200;
            overflow: hidden;
        }
        .lightbox.active { opacity: 1; pointer-events: auto; }
        
        .lightbox-img {
            max-width: 90%; max-height: 90vh; border-radius: 6px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            transition: transform 0.1s ease-out;
            transform-origin: center center;
            cursor: grab;
            user-select: none;
            -webkit-user-drag: none;
        }
        .lightbox-img:active { cursor: grabbing; }

        .lb-controls { 
            position: absolute; color: white; background: rgba(255,255,255,0.15); border: 1px solid rgba(255,255,255,0.2); 
            width: 44px; height: 44px; border-radius: 6px; font-size: 20px; 
            cursor: pointer; display: flex; align-items: center; justify-content: center; transition: background 0.2s; 
            z-index: 210;
        }
        .lb-controls:hover { background: rgba(255,255,255,0.3); }
        .lb-prev { left: 20px; }
        .lb-next { right: 20px; }
        .lb-close { top: 20px; right: 20px; }
        
        @keyframes fadeIn { to { opacity: 1; } }

        @media (max-width: 600px) {
            .album-grid { grid-template-columns: repeat(2, 1fr); gap: 8px; }
            header h1 { font-size: 26px; }
            .modal-content { height: 90vh; padding: 16px; }
            .lb-controls { width: 38px; height: 38px; font-size: 16px; }
        }
    </style>
</head>
<body>

    <div class="widget-container">
        <header>
            <h1>DRD DOMAIN</h1>
            <p>Daksh, Rishit, Dhruv DOMAIN</p>
        </header>

        <div class="upload-section">
            <div class="input-group">
                <label for="albumTitle">Album Title</label>
                <input type="text" id="albumTitle" placeholder="E.g., The Boys in the Mountains..." required>
            </div>
            <div class="input-group">
                <label for="photoFiles">Select Photos</label>
                <input type="file" id="photoFiles" accept="image/*" multiple required>
            </div>
            <button class="btn-submit" id="submitBtn" onclick="handleUpload()">Create Album</button>
        </div>

        <div class="gallery-grid" id="galleryGrid">
            <div class="empty-state">Loading your saved albums...</div>
        </div>
    </div>

    <div class="modal" id="albumModal" onclick="closeModal(event)">
        <div class="modal-content" id="modalContent">
            <button class="close-btn" onclick="closeModal(event, true)">✕</button>
            <h2 class="modal-title" id="modalTitle">Album Title</h2>
            <div class="album-grid" id="albumGrid"></div>
        </div>
    </div>

    <div class="lightbox" id="lightbox">
        <button class="lb-controls lb-close" onclick="closeLightbox()">✕</button>
        <button class="lb-controls lb-prev" onclick="navigateLightbox(-1)">❮</button>
        <img src="" alt="" class="lightbox-img" id="lightboxImg">
        <button class="lb-controls lb-next" onclick="navigateLightbox(1)">❯</button>
    </div>

    <script>
        // ==========================================
        // 0. NOTION THEME ENGINE (Run Instantly)
        // ==========================================
        function initNotionTheme() {
            const urlParams = new URLSearchParams(window.location.search);
            const themeParam = urlParams.get('theme');
            const systemDark = window.matchMedia('(prefers-color-scheme: dark)');

            function applyTheme() {
                // If explicitly set via ?theme=dark, or if set to auto/unset and system is dark
                if (themeParam === 'dark' || (!themeParam && systemDark.matches)) {
                    document.body.classList.add('dark-theme');
                } else {
                    document.body.classList.remove('dark-theme');
                }
            }

            applyTheme();

            // Watch for system theme changes if no explicit URL param override exists
            if (!themeParam) {
                systemDark.addEventListener('change', applyTheme);
            }
        }
        initNotionTheme();

        // ==========================================
        // 1. DATABASE ARCHITECTURE (IndexedDB)
        // ==========================================
        let db;
        let albumsData = []; 
        let currentAlbumIndex = null;
        let currentPhotoIndex = null;

        const dbRequest = indexedDB.open("AppleGalleryDB", 1);

        dbRequest.onerror = function(event) {
            console.error("Database error: " + event.target.errorCode);
            document.getElementById('galleryGrid').innerHTML = '<div class="empty-state">Database error. Cannot load albums.</div>';
        };

        dbRequest.onupgradeneeded = function(event) {
            db = event.target.result;
            const objectStore = db.createObjectStore("albums", { keyPath: "id" });
            objectStore.createIndex("date", "date", { unique: false });
        };

        dbRequest.onsuccess = function(event) {
            db = event.target.result;
            loadAlbumsFromDB();
        };

        function loadAlbumsFromDB() {
            const transaction = db.transaction(["albums"], "readonly");
            const objectStore = transaction.objectStore("albums");
            const request = objectStore.getAll();

            request.onsuccess = function(event) {
                albumsData = event.target.result.sort((a, b) => b.id - a.id);
                renderGallery();
            };
        }

        function saveAlbumToDB(album) {
            const transaction = db.transaction(["albums"], "readwrite");
            const objectStore = transaction.objectStore("albums");
            objectStore.add(album);
        }

        function deleteAlbumFromDB(id, event) {
            event.stopPropagation(); 
            if(!confirm("Are you sure you want to delete this album permanently?")) return;

            const transaction = db.transaction(["albums"], "readwrite");
            const objectStore = transaction.objectStore("albums");
            const request = objectStore.delete(id);

            request.onsuccess = function() {
                albumsData = albumsData.filter(album => album.id !== id);
                renderGallery();
            };
        }

        // ==========================================
        // 2. UPLOAD LOGIC & PROCESSING
        // ==========================================
        async function handleUpload() {
            const titleInput = document.getElementById('albumTitle');
            const fileInput = document.getElementById('photoFiles');
            const submitBtn = document.getElementById('submitBtn');

            const title = titleInput.value.trim();
            const files = Array.from(fileInput.files); 

            if (!title) return alert("Please provide a title.");
            if (files.length === 0) return alert("Please select at least one photo.");

            submitBtn.disabled = true;
            submitBtn.textContent = "Processing & Saving...";

            try {
                const imagePromises = files.map(file => {
                    return new Promise((resolve) => {
                        const reader = new FileReader();
                        reader.onload = e => resolve(e.target.result);
                        reader.readAsDataURL(file);
                    });
                });

                const images = await Promise.all(imagePromises);

                const newAlbum = {
                    id: Date.now(),
                    title: title,
                    images: images,
                    date: new Date().toLocaleDateString('en-US', { month: 'long', day: 'numeric', year: 'numeric' })
                };

                albumsData.unshift(newAlbum);
                saveAlbumToDB(newAlbum);
                renderGallery();

                titleInput.value = '';
                fileInput.value = '';
            } catch (error) {
                alert("Error processing images. Files might be too large.");
                console.error(error);
            } finally {
                submitBtn.disabled = false;
                submitBtn.textContent = "Create Album";
            }
        }

        // ==========================================
        // 3. UI RENDERING & INTERACTION
        // ==========================================
        function renderGallery() {
            const grid = document.getElementById('galleryGrid');
            grid.innerHTML = '';

            if (albumsData.length === 0) {
                grid.innerHTML = '<div class="empty-state">No albums yet. Upload photos to get started!</div>';
                return;
            }

            albumsData.forEach((album, index) => {
                const coverImage = album.images[0];
                const count = album.images.length;
                
                const card = document.createElement('div');
                card.className = 'card';
                card.onclick = () => openAlbum(index);

                card.innerHTML = `
                    <div style="position:relative">
                        <img src="${coverImage}" alt="${album.title}" class="card-image">
                        <span class="photo-count">${count} ${count > 1 ? 'Photos' : 'Photo'}</span>
                    </div>
                    <div class="card-content">
                        <div class="card-text">
                            <h3 class="card-title">${album.title}</h3>
                            <span class="card-date">${album.date}</span>
                        </div>
                        <button class="btn-delete" onclick="deleteAlbumFromDB(${album.id}, event)" title="Delete Album">🗑️</button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // ==========================================
        // 4. ALBUM MODAL CONTROLS
        // ==========================================
        function openAlbum(index) {
            currentAlbumIndex = index;
            const album = albumsData[index];
            const modal = document.getElementById('albumModal');
            const title = document.getElementById('modalTitle');
            const grid = document.getElementById('albumGrid');

            title.textContent = album.title;
            grid.innerHTML = '';

            album.images.forEach((imgSrc, imgIndex) => {
                const imgEl = document.createElement('img');
                imgEl.src = imgSrc;
                imgEl.className = 'album-item';
                imgEl.onclick = () => openLightbox(imgIndex);
                grid.appendChild(imgEl);
            });

            document.body.style.overflow = 'hidden'; 
            modal.classList.add('active');
        }

        // Force parameter added to window event matching logic
        function closeModal(event, force = false) {
            if (force || event.target.id === 'albumModal') {
                document.getElementById('albumModal').classList.remove('active');
                document.body.style.overflow = '';
            }
        }

        // ==========================================
        // 5. ADVANCED LIGHTBOX (SCROLL ZOOM & PAN)
        // ==========================================
        const lightboxImg = document.getElementById('lightboxImg');
        let currentScale = 1;
        let translateX = 0;
        let translateY = 0;
        let isDragging = false;
        let startX, startY;

        function updateTransform() {
            lightboxImg.style.transform = `translate(${translateX}px, ${translateY}px) scale(${currentScale})`;
        }

        function resetZoom() {
            currentScale = 1;
            translateX = 0;
            translateY = 0;
            updateTransform();
        }

        // Zoom with Mouse Scroll Wheel
        lightboxImg.addEventListener('wheel', (e) => {
            e.preventDefault();
            const zoomSensitivity = 0.1;
            const delta = e.deltaY < 0 ? 1 : -1;
            
            currentScale += delta * zoomSensitivity;
            currentScale = Math.min(Math.max(1, currentScale), 5); // Limits zoom between 1x and 5x
            
            if (currentScale === 1) {
                translateX = 0;
                translateY = 0;
            }
            updateTransform();
        }, { passive: false });

        // Double-click to quick zoom
        lightboxImg.addEventListener('dblclick', () => {
            if (currentScale > 1) {
                resetZoom();
            } else {
                currentScale = 2.5;
                updateTransform();
            }
        });

        // Click and Drag to Pan Image
        lightboxImg.addEventListener('mousedown', (e) => {
            if (currentScale > 1) {
                isDragging = true;
                startX = e.clientX - translateX;
                startY = e.clientY - translateY;
            }
        });

        window.addEventListener('mousemove', (e) => {
            if (!isDragging) return;
            translateX = e.clientX - startX;
            translateY = e.clientY - startY;
            updateTransform();
        });

        window.addEventListener('mouseup', () => {
            isDragging = false;
        });

        // Basic Navigation
        function openLightbox(imgIndex) {
            currentPhotoIndex = imgIndex;
            updateLightboxImage();
            document.getElementById('lightbox').classList.add('active');
        }

        // Reset system hook cleanup
        function closeLightbox() {
            document.getElementById('lightbox').classList.remove('active');
            resetZoom();
        }

        function updateLightboxImage() {
            resetZoom();
            const album = albumsData[currentAlbumIndex];
            lightboxImg.src = album.images[currentPhotoIndex];
        }

        function navigateLightbox(direction) {
            const album = albumsData[currentAlbumIndex];
            currentPhotoIndex += direction;
            if (currentPhotoIndex < 0) currentPhotoIndex = album.images.length - 1;
            if (currentPhotoIndex >= album.images.length) currentPhotoIndex = 0;
            updateLightboxImage();
        }

        // Keyboard accessibility
        document.addEventListener('keydown', (e) => {
            const lightbox = document.getElementById('lightbox');
            if (lightbox.classList.contains('active')) {
                if (e.key === 'ArrowRight') navigateLightbox(1);
                if (e.key === 'ArrowLeft') navigateLightbox(-1);
                if (e.key === 'Escape') closeLightbox();
            } else if (document.getElementById('albumModal').classList.contains('active')) {
                if (e.key === 'Escape') closeModal(e, true);
            }
        });
    </script>
</body>
</html>
