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
