# FIXED ChatterboxToolkitUI 🎙️🧠
WINDOWS ONLY!

ChatterboxToolkitUI is a comprehensive web application built with Gradio that provides a user-friendly interface for advanced audio generation and workflow management using resemble-ai's Chatterbox model.
This repo tries to "dirty-fix" it because it doesn't run in the state it is now. 
I also modified stuff for my taste: 

- Output folder is now named after the project name and it creates it in "Downloads" folder.
- The app is not creating any more subfolders in the output folder, all output files are put in the root of the output folder instead.
- The app now removes the temp folder that is created while processing files (inside output folder)
- The app now launches the browser with the app ready to be used automatically on launch.
  

  

## Key Features

-   **Centralized Project Management**: Create, select, and manage dedicated workspaces. All inputs, processed files, and generated outputs are automatically organized into a clean folder structure within the active project or a base directory.

-   **Single Generation**:
    -   **Text-to-Speech (TTS)**: Generate high-quality speech from text using a reference audio file to clone the speaker's voice.
    -   **Voice Conversion (VC)**: Transfer the vocal characteristics of a reference speaker onto a source audio recording.
    -   **Parameter Sweeping**: Generate multiple variations of a single output at once by sweeping across a range of values for any generation parameter (e.g., Temperature, Pace, etc.).

-   **Batch Processing**:
    -   Process entire folders of prepared text or audio files in bulk with a single click.
    -   Optionally concatenate all generated files from a batch run into a single, continuous audio file.

-   **Data Preparation Suite**:
    -   **Text Splitter**: Automatically chunk long text documents into smaller, model-friendly segments based on sentence boundaries and a configurable character limit.
    -   **Audio Splitter**: Intelligently split long audio recordings into shorter clips by making cuts during periods of silence, with configurable duration and silence detection parameters.

-   **Workflow-Integrated Editing & Refinement**:
    -   **Regenerate Audio**: The "Regenerate" workflow allows you to review individual audio files from a batch run, send them back to the Single TTS tab with their original text and voice pre-loaded, tweak parameters, and replace the old file with the new-and-improved version.
    -   **Live Text Editor**: Directly edit the content of your processed text files within the UI and save the changes, perfect for making small script adjustments without leaving the application.

[[Full Feature Rundown Video]](https://www.youtube.com/watch?v=fA8QWmG30no)

## Prerequisites

Before you begin, ensure you have the following installed on your system:

1.  **Python**: Version **3.10** is **required** anything __higher__ than 3.10 will fail to compile!!!!.
2.  **Git**: For cloning the repository.
3.  **CUDA Compatible GPU**: For acceptable performance, a GPU is highly recommended. The underlying models will be extremely slow on a CPU.
4.  **FFmpeg**: This is a critical dependency for performing various audio processing tasks.

## Installation Instructions

Follow these steps to set up and run the ChatterboxToolkitUI on your local machine or use the ChatterboxToolkitUI.ipynb to run it in a colab environment.

### 1. Clone the Repository

Create a folder, CMD into it, and clone the repository.

```cmd
git clone https://github.com/masterofobzene/ChatterboxToolkitUI.git
```

```cmd
cd ChatterboxToolkitUI
```

### 2. Set Up a Python Virtual Environment

Create a virtual environment using python 3.10 to avoid dependency conflicts.

```cmd
pyenv install 3.10.11
```

```cmd
call pyenv local 3.10.11
```

```cmd
python -m venv %USERPROFILE%\chatterbox
```


Activate the virtual environment.

```cmd
[...]\chatterbox\Scripts\activate.bat
```



### 3. Install the Project and Dependencies

Users with 10 series NVidia cards or AMD GPUs need to manually install the proper torch 2.6.0 versions.
Otherwise just install from requirements.txt

```bash
pip install -r requirements.txt
```


## Running the Application

With your virtual environment still active, run the script:

```bash
python ChatterboxToolkitUI.py
```

Once running, you will see output in your terminal like this:

```
* Running on local URL:  http://127.0.0.1:7860
```
Your browser should open with the app ready to be used.


## A Typical Workflow

1.  **Create a Project**: Navigate to the "Projects" tab and create a new project.
2.  **Prepare Data**:
    -   Upload a long text file to the project's `input_files` folder using the "Project Utilities" uploader or manually move it there.
    -   Go to the "Data Preparation" tab to split the text into manageable chunks. The outputs will be saved to the configured output folder.
3.  **Generate Audio**:
    -   Go to the "Batch Generation" tab.
    -   Load your processed files from the project.
    -   Select a reference voice and your desired parameters.
    -   Run the batch generation.
4.  **Review & Refine**:
    -   Go to the "Edit Project Data" tab.
    -   Use the "Regenerate" sub-tab to listen to your outputs. If one is imperfect, send it to the Single TTS tab, tweak the parameters, and replace it.
    -   Use the "Edit Text" sub-tab to fix any pronounciation issues you find in your source text chunks.
    -   Concatenate all audio files into one.
