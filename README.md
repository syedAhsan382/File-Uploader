# Image Uploader
 
A drag-and-drop image uploader built with plain HTML, CSS and JavaScript. Drop images in (or browse your files), see a preview with a progress bar, and your images are still there when you reload the page.
 
**Live demo:** [add your Vercel or Netlify link here]
 
![Image Uploader screenshot](screenshot.png)
 
## Features
 
- Drag and drop images onto the drop zone, or click it to browse your files
- Upload multiple images at once
- Only JPG, PNG and GIF are accepted. Each file is checked by its MIME type and by its file extension
- Files larger than 2 MB are rejected with a clear error message
- Error messages appear for invalid files and disappear automatically after 5 seconds
- Image preview cards showing the thumbnail, file name and file size
- A progress bar and status text for each image (the upload is simulated, see below)
- Remove a single image with the X button, or remove everything with "Clear all" (asks for confirmation first)
- Images are saved in the browser, so they are still there after a page reload
- The drop zone highlights while you drag a file over it
- Responsive layout that works on phones and desktops
## Built with
 
- HTML5
- CSS3 (CSS variables, Grid, Flexbox, transitions, keyframe animations)
- Vanilla JavaScript, with no libraries or frameworks
## How it works
 
1. **Getting the files.** The drop zone listens for `dragenter`, `dragover`, `dragleave` and `drop` events. A click on the zone triggers a hidden `<input type="file">`. Both ways send the files to the same function, `handleFiles`.
2. **Validating.** Each file is checked for type, extension and size before anything else happens.
3. **Reading the image.** `FileReader.readAsDataURL()` turns the file into a data URL, which is used as the `src` of the preview image.
4. **Progress bar.** The upload is simulated, since there is no server. A function using `setTimeout` adds a random amount to the progress on every tick until it reaches 100%, then marks the card as done.
5. **Saving.** When the progress reaches 100%, the image (name, size and data URL) is saved in `localStorage` as JSON. On page load, the saved images are read back and their cards are rebuilt.
## Run it locally
 
No install or build step is needed.
 
1. Download or clone the project:
```
   git clone https://github.com/your-username/your-repo-name.git
```
2. Open `index.html` in your browser.
## Project structure
 
```
image-uploader/
├── index.html    # page structure
├── style.css     # all the styling
├── script.js     # drag and drop, validation, previews, progress bar, storage
└── README.md
```
 
## Limitations
 
- The upload is a simulation. Images are not sent to a server, they are only stored in the browser
- `localStorage` has a limit of about 5 MB, so only a few images fit. That is why each file is limited to 2 MB, and the page shows an error if the storage is full
- Images are saved per browser, so they will not appear on another device
## What I learned
 
- Handling drag and drop events and why `preventDefault()` is needed so the browser does not open the dropped file
- Reading files with `FileReader` and showing them using data URLs
- How `setTimeout` can be used to build a progress bar step by step
- Saving and loading data with `localStorage` and `JSON.stringify` / `JSON.parse`
- Validating user input and showing helpful error messages
- Rebuilding the page from saved data when it loads
## Possible improvements
 
- Upload the files to a real server or a cloud service instead of simulating it
- Add an image preview modal when a thumbnail is clicked
- Show a total count of uploaded images
- Use IndexedDB instead of `localStorage` to store larger files
## Author
 
Syed Muhammad Ahsan, Front-end developer
[GitHub](https://github.com/your-username) | [LinkedIn](https://www.linkedin.com/in/your-profile)
 
