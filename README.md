😀 Face Detection — Image & Live Video

Detect faces from an image or a live camera using OpenCV (Haar Cascade).

---

**Project files**

- Source: [FaceDetection.cpp](FaceDetection.cpp#L1-L400)
- Demo images: [Images/Avengers.jpg](Images/Avengers.jpg), [Images/FF.jpg](Images/FF.jpg), [Images/HP.jpg](Images/HP.jpg), [Images/TC.jpg](Images/TC.jpg)

---

## 🔧 What it does

- Runs face detection using OpenCV's Haar cascade (`haarcascade_frontalface_alt.xml`).
- Two modes:
  - Live Face Detection (camera)
  - Image Face Detection (single image)

The program draws red rectangles around detected faces and can save the output image.

---

## ✅ Prerequisites

- OpenCV (built for your Visual Studio version)
- Microsoft Visual Studio (any recent edition)

---

## 🛠 Setup (Visual Studio)

1. Install OpenCV and note the paths (example used in code):
   - Include headers: `C:\OpenCV\opencv\build\include`
   - Libraries: `C:\OpenCV\opencv\build\x64\vc14\lib`
   - Binary (optional, add to PATH): `C:\OpenCV\opencv\build\x64\vc14\bin`

2. Create a new Visual C++ Console project and add `FaceDetection.cpp` to the project.

3. In Project Properties:
   - C/C++ → General → Additional Include Directories: add the OpenCV include path above.
   - Linker → General → Additional Library Directories: add the OpenCV lib path.
   - Linker → Input → Additional Dependencies: add the appropriate `opencv_world*.lib` (e.g., `opencv_world452.lib` or `opencv_world452d.lib` for debug).

4. Ensure runtime DLLs are available (either add the OpenCV `bin` folder to PATH or copy required DLLs next to the executable).

---

## ▶ How to run

1. Build the project in Visual Studio.
2. Run the produced executable.
3. Choose an option at the menu:
   - `1` — Live Face Detection (requires camera)
   - `2` — Image Face Detection (the code uses a hardcoded path by default)
   - `3` — Exit

Notes on defaults in the source:

- Cascade path (loaded at startup):
  - `C:\OpenCV\opencv\sources\data\haarcascades\haarcascade_frontalface_alt.xml` — update this to your `haarcascades` location if different.
- Image mode default path (change inside `imgdetect()`):
  - `D:\College\KIT\Projects\2nd Year\4th Sem\Mini Project\Image\tc.jpg`
- Output paths (change inside `livedetect()` / `imgdetect()`):
  - `D:\College\KIT\Projects\2nd Year\4th Sem\Mini Project\Output\...`

Replace those hardcoded paths or modify the code to accept command-line arguments for better portability.

---

## 🧩 Code notes & suggestions

- The project uses `CascadeClassifier::detectMultiScale` for face detection.
- Hardcoded paths make the program fragile; consider:
  - Accepting command-line args or a config file for cascade, input image, and output directories.
  - Using `cv::CommandLineParser` or simple `argv` parsing.
  - Checking and creating the output directory before saving images.

Small example change (concept):
Replace hardcoded cascade load with a path variable passed via `argv` or environment.

---

## 📷 Sample Results

Below are two example outputs from `Images/` (click to open full-size):

<p align="center">
  <a href="Images/Avengers.jpg"><img src="Images/Avengers.jpg" alt="Avengers" height="240" style="margin-right:12px;"/></a>
  <a href="Images/TC.jpg"><img src="Images/TC.jpg" alt="TC" height="240"/></a>
</p>

---

## ⚠️ Known limitations

- Program exits when no face is found in image mode.
- Uses blocking infinite loops with `waitKey` and `exit(0)`; for production you'd want cleaner shutdown logic.

---

## 🙏 Credits

- Built with OpenCV — great thanks to the OpenCV community.
