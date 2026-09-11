#### 🎯 PROJECT: Audio Instrument Organizer (ML-Powered Web Tool)

---

### 🧠 One-line Pitch

> A web application that classifies uploaded audio files by instrument, organizes them into structured folders, detects unknown/non-musical inputs, and returns a downloadable ZIP with results and metadata.

---

### 🧱 Core Idea

* Not just a classifier
* A **usable tool** that organizes messy audio into structured data

---

### 🖥️ User Experience

#### 🎧 Input

* Upload multiple audio files (`.wav`, `.mp3`)
* Drag & drop interface (Streamlit)

---

#### ⚙️ Processing Pipeline

1. Load audio
2. Normalize + trim
3. Extract features (MFCC + spectral)
4. Predict instrument
5. Compute confidence
6. Decide:

   * Instrument OR
   * Unknown

---

#### 📦 Output (Downloadable ZIP)

```
output.zip
│
├── guitar/
├── piano/
├── violin/
├── drums/
├── unknown/
│
└── report.csv
```

---

#### 📊 report.csv

```
filename, prediction, confidence
audio1.wav, guitar, 0.91
audio2.wav, piano, 0.82
audio3.wav, unknown, 0.34
```

---

### ⚙️ System Architecture

```
Upload → Preprocess → Feature Extraction → Model → Confidence Filter → Folder Assignment → ZIP Export
```

---

### 🧠 Model Design

#### 🎯 Classes

* guitar
* piano
* violin
* drums
* (optional) flute

---

#### 🤖 Model

* SVM (primary)
* Random Forest (optional)

---

#### 📊 Features

* MFCC (13 × mean + std)
* Spectral centroid
* Spectral bandwidth
* Zero-crossing rate
* RMS energy

---

### 🚨 Unknown Input Handling

#### Why?

Users may upload:

* Car sounds
* Speech
* Noise

---

#### ✅ Solutions

**1. Confidence Threshold**

```python
if confidence < 0.6:
    label = "unknown"
```

**2. Unknown Folder**

```
unknown/
```

**3. Optional Checks**

* Low RMS → silence
* High noise → reject

---

### 🧩 Components

#### 1. Feature Extraction

```
features.py
```

#### 2. Model

```
model.py
```

#### 3. Prediction Pipeline

```
predict.py
```

#### 4. ZIP Generator

```
zip_utils.py
```

#### 5. Web App

```
app.py
```

---

### 🗓️ 4-Day Plan

#### Day 1

* Dataset
* Feature extraction
* CSV creation

#### Day 2

* Train SVM
* Add confidence logic
* Evaluate

#### Day 3

* Build Streamlit UI
* File upload + prediction

#### Day 4

* ZIP generation
* report.csv
* Unknown handling
* Polish

---

### ⚠️ Edge Cases

* Short audio → reject
* Silence → reject
* Multiple instruments → assume dominant instrument

---

### 🧠 Why This Project is Strong

* Feature engineering
* ML model usage
* System design
* File handling
* Edge case handling
* Usable interface

---

### 📄 README Must Include

* Problem statement
* Input assumptions
* Model details
* Limitations
* Example output

---

### 🧪 Demo Flow

1. Upload audio files
2. Show predictions
3. Download ZIP
4. Verify organized folders

---

### ⚔️ Final Mission

> Turn messy audio into structured, trustworthy, downloadable data using ML
