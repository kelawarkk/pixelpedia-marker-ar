# PixelPedia — Option 1: real marker AR

This separate project uses A-Frame 1.6.0 and AR.js 3.4.8 to anchor the original 3D PixelBot mascot to a real Hiro marker in the camera image. This replaces the earlier simulated room experience.

## Try it

Open the project through HTTPS on your phone, choose a game, then select Launch real marker AR. Tap Start camera and allow camera permission. Print marker.html (or display it on another device), then point the camera at the whole Hiro marker in good light. A tracked robot appears when the marker is found, disappears when it is lost, and follows its pose. Rotate and Size controls adjust the robot. Stop camera releases the camera.

The same Hiro marker is used for all games. Selecting a game changes the UI label only; this is not automatic game recognition. It does not recognise arbitrary game posters. Natural-image tracking would require a different tracking dataset.

## Option-specific files

- scanner.html / scanner.js: live camera session, marker tracking events, controls and camera cleanup.
- marker.html: printable high-contrast Hiro marker.
- assets/hiro.png, patt.hiro, camera_para.dat: image, tracking pattern and calibration from AR.js.
- assets/pixelbot.glb: original 3D test mascot.

Camera video is processed by the page. No recording or upload endpoint is implemented. Close other apps using the camera if it cannot start. In Safari, check the website camera permission if it was previously denied.

## Open and edit on Windows

1. Extract the ZIP completely. Open the extracted folder in Visual Studio Code.
2. For desktop testing, use VS Code Live Server, or run `python dev_server.py` if Python 3 is installed, then open http://127.0.0.1:5173. Do not double-click the HTML: real camera/3D asset loading requires a server.
3. Edit index.html (shell), style.css (layout), app.js (screens and game data), and the option-specific files listed below.
4. For iPhone testing, upload the entire extracted folder to an HTTPS static host, such as GitHub Pages. Open that HTTPS address directly in Safari. Do not test inside a chat preview or embedded iframe.
5. Your phone's localhost refers to the phone, not your Windows PC. An ordinary HTTP link to the PC's LAN IP is not enough for camera/WebXR security requirements.

No Mac or native app build is required for these web AR implementations. Phone AR still depends on device and browser support.

## Assets and libraries

Original PixelBot mascot: assets/pixelbot.glb. It is a block-style mint and purple robot, about 35 cm tall at its original scale. It is not an official game character. Original game imagery remains replaceable illustrated placeholders.

The relevant AR libraries are bundled in vendor/ with licenses; see THIRD-PARTY-NOTICES.md. Most core files load locally, although native AR services may need internet.

## Shared PixelPedia screens

Home, Explore/search, game details, Saved, About and the demo contact form are retained. Saved games use browser-local storage. The contact form does not send or store messages. Each version starts on its AR page.

## Verification limits

Source JavaScript syntax and local assets checked. The test browser disables WebGL, so it could not render the model or verify camera tracking. Physical marker tracking, iPhone Quick Look and real room placement require testing on a compatible phone; they are not claimed as device-verified.
