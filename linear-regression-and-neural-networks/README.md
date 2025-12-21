## GUIDING DOCUMENT:
https://www.youtube.com/watch?v=Y7DsfKyBF7g&list=PL2L83ZcMO-5O7zNycUkS5WLgr33J3QxMK&index=4

## WORKING WITH KERNELS IN VSCODE:
https://www.youtube.com/watch?v=suAkMeWJ1yE

## Using virtual environment: 
Create virtual environment: python -m venv ./.venv
Activate virtual environment: source ./.venv/bin/activate
Install packages: pip install pandas numpy matplotlib scikit-learn

## TensorFlow Setup for Apple M-Series (M1/M2/M3):

**Problem:** TensorFlow hangs/slow on M-series Macs if using x86_64 Python (Rosetta emulation).
**Solution:** Use native ARM64 Python for 10-20x faster performance + GPU acceleration.

### Quick Setup:
```bash
# 1. Check if you're running x86_64 (bad) or arm64 (good)
python -c "import platform; print(platform.machine())"

# 2. Create ARM64 virtual environment
arch -arm64 /usr/bin/python3 -m venv venv-arm64

# 3. Install packages
./venv-arm64/bin/pip install --upgrade pip
./venv-arm64/bin/pip install pandas numpy matplotlib scikit-learn seaborn ipykernel jupyter
./venv-arm64/bin/pip install tensorflow==2.16.1 tensorflow-metal==1.1.0

# 4. Register Jupyter kernel
./venv-arm64/bin/python -m ipykernel install --user --name=ml-arm64 --display-name="Python 3.9 (ML ARM64)"

# 5. Test TensorFlow + GPU
./venv-arm64/bin/python -c "import tensorflow as tf; print('TF:', tf.__version__); print('GPU:', len(tf.config.list_physical_devices('GPU')))"
```

### In Jupyter:
- Click kernel selector (top-right)
- Select "Python 3.9 (ML ARM64)"
- First import: ~2 min (builds cache)
- Subsequent imports: ~8 sec ✅

**Result:** Native M-series performance with Metal GPU acceleration.

## Machine Learning workflow:
* Task understanding
* Data haandling and preprocessing
* Modeling
* Error Measurement
* Training and Optimization
* Performance Measurement
* Validating and Testing
* Corrective Measures