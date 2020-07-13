# How to run?

## Linux/macOS
```
# Setup a Python virtual enviroment inside venv directory
python -mvenv venv  

# Enter the virtual environment
source venv/bin/activate  

# Update pip (just for the sake of removing update warnings)
pip install --upgrade pip  

# Install dependencies
pip install -r requirements.txt  
or  
pip install tensorflow==1.14.0 opencv-python pyyaml git+https://github.com/JiahuiYu/neuralgym  

# Create trained models directory
mkdir model_logs  

# Download pre-trained Places model
Download and unzip pre-trained model in model_logs/release_places2_256 directory: https://drive.google.com/drive/folders/1M3AFy7x9DqXaI-fINSynW7FJSXYROfv-  

# Remove checkpoint extension
mv model_logs/release_places2_256/checkpoint.txt model_logs/release_places2_256/checkpoint  

# Run with wooden image input and mask
## CPU (make sure to comment `ng.get_gpus(1)` line in test.py beforehand.
TF_XLA_FLAGS=--tf_xla_cpu_global_jit python test.py --image examples/places2/wooden_input.png --mask examples/places2/wooden_mask.png --output examples/output.png --checkpoint_dir model_logs/release_places2_256  

## GPU
python test.py --image examples/places2/wooden_input.png --mask examples/places2/wooden_mask.png --output examples/output.png --checkpoint_dir model_logs/release_places2_256  

# Check output in examples/output.png
```

## Windows

TBD

## Google Codelab
https://drive.google.com/open?id=1mSQrO8o-o5GSQWjlico7O_gpT3YrkDRG
https://drive.google.com/open?id=1BXiUSiRizUG9HxFWH43iYkc3KiPnXrRI
https://drive.google.com/open?id=186h4Kk7W8CkmrdbPwbp2JAssFA1VfzCJ
https://drive.google.com/open?id=18rFtQyyQ3iWvBG43nDnFb9WnMHoGco0C