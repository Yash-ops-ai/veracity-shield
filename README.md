Veracity Shield
An AI-powered deepfake detection system that lets anyone upload a video, image or audio file and get an instant verdict on whether it is real or fake.

What It Does
Veracity Shield analyzes uploaded media using multiple independent AI signals and combines them into a single confident verdict. It works on video, image and audio files and explains exactly why it flagged something as fake.

How It Works
The system routes each uploaded file to the correct pipeline based on file type. Each pipeline runs several detection checks and sends scores to an ensemble engine that makes the final decision.

Video Pipeline
-FFmpeg extracts frames and separates the audio track
-OpenCV detects and crops faces from each frame
-EfficientNet CNN scores each frame from 0.0 (real) to 1.0 (fake)
-Dlib tracks 68 facial landmarks to check blink patterns and lip movement
-Librosa analyzes the audio and predicts expected lip movement from speech sounds
-A sync check compares actual lip movement against predicted lip movement

Image Pipeline
-OpenCV detects and crops the face
-EfficientNet CNN classifies the image
-FFT frequency analysis detects GAN generation artifacts
-Dlib checks eye reflection consistency

Audio Pipeline
-FFmpeg converts audio to .wav format
-Librosa extracts MFCC voice fingerprint
-Voice Activity Detection maps speech vs silence patterns
-SVM classifier predicts real vs AI generated voice

Ensemble Decision Engine
All pipeline scores are combined using weighted voting:
CNN (40%) + Audio-Video Sync (25%) + Temporal Consistency (15%) + Blink Pattern (10%) + Voice Spectral (10%)
Score above 0.5 = FAKE. Score below 0.5 = REAL.

Tech Stack
Category           Tools
Language           Python 3.10+
AI Frameworks      TensorFlow, PyTorch, Scikit-learn
Computer Vision    OpenCV, Dlib, NumPy
Audio Processing    FFmpeg, Librosa, PyDub
Backend             Flask
Frontend            HTML, CSS, JavaScript
Pre-trained Model   EfficientNet-B0

Datasets Used
-FaceForensics++ — Rossler et al. ICCV 2019
-DFDC — Dolhansky et al. Facebook AI 2020
-Celeb-DF — Li et al. CVPR 2020

Research Papers
-FaceForensics++: Learning to Detect Manipulated Facial Images — ICCV 2019
-The DeepFake Detection Challenge Dataset — 2020
-Celeb-DF: A Large Scale Challenging Dataset for DeepFake Forensics — CVPR 2020

Team
Veracity Shield — FISTA India Innovates Hackathon 2026
