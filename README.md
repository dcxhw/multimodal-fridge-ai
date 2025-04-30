# 🧊 Smart Fridge Sensor App

This is a full-stack application that **simulates a smart fridge sensor**. Using your **webcam**, it detects items going **in and out of the fridge** and updates the **fridge inventory** accordingly.

Behind the scenes, the app captures a camera frame and uses a powerful **LLM** (Large Language Model) to identify the item shown. Based on user input (`Add` or `Delete`), the inventory is updated in **Firebase**. Additionally, it generates personalized recipes based on the user's preferences and fridge inventory using **recipe generation models**.

## 🧠 Overview

* **LLM:** `ollama-llama3.2-vision-11b`
* **Recipe Generation:** Uses **FAISS** for recipe search and **Hugging Face's LLM** `all-MiniLM-L6-v2` and `Mistral-7B-Instruct-v0.1` for personalized recipe generation
* **Frontend:** Built with **Next.js + Tailwind + Material UI**
* **Backend:** **Flask** server handles LLM requests, Firebase updates, and recipe generation
* **Database:** **Firebase Firestore** stores inventory data and recipe metadata

## 🌐 Web Pages

| Route | Description |
|-------|-------------|
| `/` | Landing page with introduction and description |
| `/fridge` | Live fridge simulation with webcam, item detection, and inventory tracking |
| `/recipe` | Generates personalized recipe based on preference and fridge inventory |

## ⚙️ Features

- ✅ Simulates a fridge sensor using your webcam
- ✅ Uses an **LLM to identify items visually**
- ✅ Captures frame when **Add** or **Delete** is clicked
- ✅ Dynamically **updates Firebase inventory**
- ✅ **Generates personalized recipes** based on fridge items and user preferences
- ✅ Clean UI built with Material UI + Tailwind
- ✅ Auto-refresh and status popups for detected items

## 🛠️ Setup Guide

### 🔌 Backend (Flask API)

1. `cd flask-backend`

2. Create a virtual environment:
   * **Mac/Linux**:
     ```bash
     python -m venv venv
     source venv/bin/activate
     ```
   * **Windows**:
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file and add the following variables:
   ```env
   REPLICATE_API_TOKEN=<Your Replicate API Token>
   HUGGINGFACE_HUB_TOKEN=<Your HuggingFace Hub API Token>
   FAISS_PATH=<Your FAISS file path>
   RECIPE_METADATA_PATH=<Your recipe_metadata file path>
   ```

5. Run the Flask server:
   ```bash
   python app.py
   ```

### 💻 Frontend (Next.js)

1. `cd ts-frontend`

2. Install dependencies:
   ```bash
   npm i
   ```

3. Start the dev server:
   ```bash
   npm run dev
   ```

## 📂 Files to Add in `/scripts` Folder

Ensure that the following files are in the `flask-backend/scripts` folder for the backend to function properly:

* `recipe_faiss.index`: FAISS index file used for fast recipe searches based on the available fridge ingredients.
* `recipe_metadata.csv`: A CSV file containing metadata for all available recipes (e.g., ingredients, steps, tags).

These files are essential for the backend to search recipes based on your fridge items and preferences.

## 📸 Example Workflow

1. Go to `/fridge`
2. Your webcam activates
3. Hold an item in front of the camera
4. Click **Add** ➕ or **Delete** 🗑️
5. The LLM identifies the object (e.g., "Tofu")
6. The inventory is updated in Firebase!

Once inventory is updated, go to `/recipe` to generate a personalized recipe based on your fridge items and dietary preferences.

## 📦 Technologies Used

* **React / Next.js**
* **Material UI**
* **Tailwind CSS**
* **Flask**
* **Firebase Firestore**
* **Replicate (LLM API)** for item detection
* **FAISS** for recipe search
* **Hugging Face (LLM)** for recipe generation

## 🧪 Credits

Built with ❤️ for a fridge that's smarter than your roommate. Made for CS614 ✨

## 💠 Credit

This project was originally developed as part of a team collaboration.  
> Special thanks to [@gohweihan1](https://github.com/gohweihan1) for the initial architecture and implementation.

---
## 👩‍💻 My Contributions

- Designed and implemented the **Retrieval-Augmented Generation (RAG) pipeline**, including:
  - Semantic embedding with SentenceTransformers
  - Vector indexing and top-k retrieval using FAISS
  - Custom scoring logic based on ingredient overlap, user preference alignment, and semantic similarity
- Engineered a **prompt construction system** using structured templates and prompt techniques:
  - Instructional framing, hard constraints, format specifications, and reference context injection
- Built **data preprocessing pipelines** for large-scale recipe datasets:
  - Cleaning, semantic formatting, and reduction from ~495k to 50k entries for efficiency and accuracy
- Integrated **user preference filters** (meal type, dietary needs, cuisine type) into the generation flow
- Collaborated on **backend integration and system-level testing** for seamless end-to-end functionality

---