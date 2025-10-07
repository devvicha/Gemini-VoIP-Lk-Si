<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Run and deploy your AI Studio app

This contains everything you need to run your app locally.

View your app in AI Studio: https://ai.studio/apps/drive/1mpjIet9QTnkQgjhnEHco_jBOqRIuhK7j

## Run Locally

**Prerequisites:** Anaconda or Miniconda

### Quick Start (Recommended)

1. **Set up conda environment and dependencies**:
   ```bash
   ./setup-env.sh
   ```

2. **Set your Gemini API key** in [.env.local](.env.local)

3. **Run the app**:
   ```bash
   ./run-dev.sh
   ```

### Manual Setup

If you prefer manual setup:

1. **Create and activate conda environment**:
   ```bash
   conda env create -f environment.yml
   conda activate sampath-bank-env
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set the `GEMINI_API_KEY`** in [.env.local](.env.local) to your Gemini API key

4. **Run the app**:
   ```bash
   npm run dev
   ```

For detailed conda environment setup instructions, see [CONDA_SETUP.md](CONDA_SETUP.md).

### Legacy Setup (Node.js only)

If you prefer to use Node.js without conda:

1. **Prerequisites:** Node.js
2. Install dependencies: `npm install`
3. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
4. Run the app: `npm run dev`

## Streamlit Deployment

Use the new Python entry point when you want to host the assistant on Streamlit Cloud.

1. Ensure the Conda environment is active: `conda activate sampath-bank-env`
2. Install the Python requirements: `pip install -r requirements.txt`
3. Provide your Gemini key via `export GEMINI_API_KEY="your-key"` (or Streamlit secrets)
4. Start the app locally: `streamlit run streamlit_app.py`

When deploying on Streamlit Cloud:
- Select the `main` branch and set `streamlit_app.py` as the main file.
- Add `GEMINI_API_KEY` under *App secrets* instead of committing it.

### Voice Mode (Sinhala/Tamil)

The Streamlit chat supports Sinhala/Tamil speech input and spoken responses.

1. Install FFmpeg (needed by Whisper). Example: macOS `brew install ffmpeg`; Ubuntu `sudo apt install ffmpeg`.
2. Reinstall the Python requirements (`pip install -r requirements.txt`) to pull the new voice libraries. If automatic install fails, manually run `pip install streamlit-mic-recorder==0.0.8 faster-whisper gTTS`.
3. Run `streamlit run streamlit_app.py` and enable **Voice mode** in the sidebar.
4. Record your question in Sinhala/Tamil; replies are spoken back using gTTS.

If the Gemini API reports that a model is unavailable (404), list the models your key can access and update `streamlit_app/gemini_client.py` to point at one of them:

```python
import google.generativeai as genai
genai.configure(api_key="YOUR_KEY")
for model in genai.list_models():
    print(model.name, model.supported_generation_methods)
```
