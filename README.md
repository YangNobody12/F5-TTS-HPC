F5-TTS-HPC
================

F5-TTS-HPC is a version of F5-TTS optimized for use on Supercomputers / HPC Clusters by turning off automatic model download (auto-download).
It allows users to manage their own model downloads.

ORIGINAL: https://github.com/SWivid/F5-TTS

✅ Suitable for environments that cannot directly connect to the internet.
✅ Users can control the version of the model themselves.
✅ Support both Inference and Training / Fine-tuning.

📂 File Structure
-----------------

After installing the code, the following directory structure should be created:

F5-TTS-HPC/
├── pretrain_checkpoint/    # for storing pretrain model (from HuggingFace)
│   └── F5TTS_v1_Base.pth
├── vocoder/                # for storing vocoder (e.g., Vocos)
│   └── config.yaml and pytorh_model.bin
└── src/
    └── f5_tts/             # source code

📥 Manual Download
-------------------

1. Pretrain Model (F5-TTS)

Download from HuggingFace:
👉 https://huggingface.co/SWivid/F5-TTS/tree/main

Place the .pth or checkpoint file in the following directory:

F5-TTS-HPC/pretrain_checkpoint/

2. Vocoder (Vocos)

Download from HuggingFace:
👉 https://huggingface.co/charactr/vocos-mel-24khz/tree/main

🚀 Installation
---------------

# Create a Python 3.11 environment
conda create -n f5-tts-hpc python=3.11
conda activate f5-tts-hpc

# Install PyTorch according to the GPU/Device used (CUDA, ROCm, Intel, Apple MPS)
# Example: NVIDIA CUDA 11.8
pip install torch==2.3.0+cu118 torchaudio==2.3.0+cu118 --extra-index-url https://download.pytorch.org/whl/cu118

# Clone the repo
git clone https://github.com/yourname/F5-TTS-HPC.git
cd F5-TTS-HPC
pip install -e .

📌 Notes for HPC
------------------

No automatic file download.

Users must prepare their own models and place them in the directory according to the specified structure.

Suitable for running jobs on LANTA Supercomputers and other HPC Clusters.

🙏 Credit
---------

Thank you to HPC-Ignite for supporting the testing of this model on the LANTA Supercomputer.
