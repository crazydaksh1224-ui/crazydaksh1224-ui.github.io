<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shared Notes Widget</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script type="module">
        // Firebase Imports
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getFirestore, collection, addDoc, onSnapshot, query, orderBy } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { getStorage, ref, uploadBytes, getDownloadURL } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-storage.js";
        import { getAuth, signInAnonymously } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";

        // CONFIGURATION: Replace with your actual Firebase config
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_PROJECT_ID.appspot.com",
            messagingSenderId: "YOUR_ID",
            appId: "YOUR_APP_ID"
        };

        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const storage = getStorage(app);
        const auth = getAuth(app);

        // App State
        let notes = [];
        const notesContainer = document.getElementById('notes-container');
        const uploadModal = document.getElementById('upload-modal');

        // Auth
        signInAnonymously(auth);

        // Real-time listener
        const q = query(collection(db, "notes"), orderBy("createdAt", "desc"));
        onSnapshot(q, (snapshot) => {
            notes = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
            renderNotes();
        });

        function renderNotes() {
            notesContainer.innerHTML = notes.map(note => `
                <div class="bg-white p-6 rounded-3xl border border-gray-100 shadow-sm hover:shadow-xl transition-all duration-300 ease-[cubic-bezier(.2,.8,.2,1)]">
                    <img src="${note.imageUrl}" class="w-full h-48 object-cover rounded-2xl mb-4" />
                    <h3 class="font-semibold text-lg text-gray-900">${note.title}</h3>
                    <p class="text-sm text-gray-500">${note.day}</p>
                </div>
            `).join('');
        }

        // Upload Logic
        window.handleUpload = async () => {
            const fileInput = document.getElementById('file-input');
            const titleInput = document.getElementById('title-input');
            const file = fileInput.files[0];
            
            if(!file) return;

            const storageRef = ref(storage, 'notes/' + Date.now() + file.name);
            const snapshot = await uploadBytes(storageRef, file);
            const downloadURL = await getDownloadURL(snapshot.ref);

            await addDoc(collection(db, "notes"), {
                title: titleInput.value,
                day: new Date().toLocaleDateString('en-US', { weekday: 'long' }),
                imageUrl: downloadURL,
                createdAt: new Date()
            });

            uploadModal.classList.add('hidden');
        };
    </script>
</head>
<body class="bg-gray-50 text-gray-900 font-sans p-8 md:p-16">

    <header class="max-w-5xl mx-auto flex justify-between items-center mb-16">
        <h1 class="text-3xl font-bold tracking-tight">Shared Notes</h1>
        <button onclick="document.getElementById('upload-modal').classList.remove('hidden')" 
                class="bg-black text-white px-6 py-3 rounded-full hover:scale-105 transition-transform">
            + Upload Note
        </button>
    </header>

    <main id="notes-container" class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <!-- Notes will be injected here -->
    </main>

    <!-- Upload Modal -->
    <div id="upload-modal" class="hidden fixed inset-0 bg-white/80 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-2xl w-full max-w-md">
            <h2 class="text-2xl font-bold mb-6">New Note</h2>
            <input type="text" id="title-input" placeholder="Note Title" class="w-full p-4 border rounded-xl mb-4">
            <input type="file" id="file-input" class="mb-6">
            <div class="flex gap-4">
                <button onclick="handleUpload()" class="flex-1 bg-black text-white py-3 rounded-xl">Submit</button>
                <button onclick="document.getElementById('upload-modal').classList.add('hidden')" class="flex-1 bg-gray-100 py-3 rounded-xl">Cancel</button>
            </div>
        </div>
    </div>
</body>
</html>
