# Ito
it use TrispoSR

import os

# 1. Cloner ou aller dans le dossier
if not os.path.exists('TripoSR'):
    !git clone https://github.com/VAST-AI-Research/TripoSR.git
%cd TripoSR

# 2. Installer manuellement TOUTES les vraies dépendances requises (sans passer par requirements.txt)
!pip install --upgrade pip
!pip install "Pillow>=10.2.0" omegaconf einops torchvision trimesh rembg moderngl huggingface_hub

# 3. Installer torchmcubes proprement
!pip uninstall -y torchmcubes
!pip install git+https://github.com/tatsy/torchmcubes.git

# 1. Forcer les versions exactes de Hugging Face et transformers attendues par TripoSR
!pip install --upgrade transformers==4.38.2 huggingface-hub==0.22.2

# 2. Relancer le script de test
!python run.py /content/images --output-dir output/

!pip install --upgrade onnxruntime

!pip install xatlas

!python run.py examples/chair.png --output-dir output/ --device cuda
