<!DOCTYPE html>
<html>
<head>
<title>Image Captioning</title>
</head>
<body>
  <input type="file" id="imageUpload" accept="image/*">
  <button onclick="generateCaption()">Generate Caption</button>
  <p id="caption"></p>

  <script>
    async function generateCaption() {
      const file = document.getElementById('imageUpload').files[0];
      const formData = new FormData();
      formData.append('image', file);

      try {
        const response = await fetch('/caption', {
          method: 'POST',
          body: formData,
        });
        const data = await response.json();
        document.getElementById('caption').textContent = data.caption;
      } catch (error) {
        console.error(error);
        document.getElementById('caption').textContent = 'Error generating caption';
      }
    }
  </script>
</body>
</html>
