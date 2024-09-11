<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Homework Upload</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f0f0f0;
        }
        .upload-container {
            margin: 0 auto;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            max-width: 500px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .upload-container h1 {
            text-align: center;
        }
        .upload-container form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .upload-container input {
            margin-bottom: 15px;
        }
        .homework-photos {
            margin-top: 30px;
        }
        .homework-photo {
            border: 1px solid #ddd;
            padding: 10px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="upload-container">
        <h1>Upload Your Homework</h1>
        <form id="uploadForm" enctype="multipart/form-data">
            <input type="file" name="photo" accept="image/*" required>
            <button type="submit">Upload</button>
        </form>
    </div>

    <div class="homework-photos">
        <h2>Homework Gallery</h2>
        <div id="gallery"></div>
    </div>

    <script>
        document.getElementById('uploadForm').addEventListener('submit', async function(event) {
            event.preventDefault();
            
            const formData = new FormData(this);
            const response = await fetch('/upload', {
                method: 'POST',
                body: formData
            });

            if (response.ok) {
                const uploadedPhoto = await response.json();
                displayPhoto(uploadedPhoto);
            }
        });

        function displayPhoto(photo) {
            const gallery = document.getElementById('gallery');
            const photoDiv = document.createElement('div');
            photoDiv.classList.add('homework-photo');
            photoDiv.innerHTML = `
                <img src="${photo.url}" alt="Homework Photo" style="max-width: 100%;">
                <p>Uploaded on: ${new Date(photo.uploadDate).toLocaleString()}</p>
            `;
            gallery.appendChild(photoDiv);
        }
    </script>
</body>
</html>
