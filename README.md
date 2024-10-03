# Audio Watermarking using `plaintext` watermark

This Python script implements a watermarking technique to embed and detect a **plaintext** watermark in an audio file. The watermark can be any text string, which is converted into a binary format and embedded into a host audio signal. The script uses a pseudo-random sequence for watermark embedding and includes functionality to detect the watermark after it has been embedded.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Functions](#functions)
- [Results](#results)
- [License](#license)

## Requirements

- Python 3.x
- Jupyter Notebook
- NumPy
- SciPy (for WAV file handling)
- Pydub (for audio processing)

You can install the required packages using pip:

```bash
pip install numpy scipy pydub
```

## Installation

1. Clone the repository or download the Jupyter Notebook file.

2. Ensure you have the required `.mp3` file at the root directory, which will be preproccessed to get a `.files/preproccessed.wav` file for watermarking. 
   **Alternatively**: place a mono channel `.wav` audio file in the `./files` directory and name it `preprocessed.wav`, this won't require preprocessing. 

3. Open a terminal and navigate to the directory containing the notebook.

4. Launch Jupyter Notebook:

   ```
   jupyter notebook
   ```

## Usage
To run the script, simply execute it in your terminal or command prompt:

To run the watermarking process:

1. Make sure that the audio file (`raw.mp3` or `preprocessed.wav`) is available in the specified directory.
Update the `WATERMARK_TEXT` variable in the notebook with your desired watermark.
2. Run the cells sequentially.

## Configuration

You can customize the watermarking process by adjusting the following configuration variables in the notebook:

- `HOST_SIGNAL_FILE`: Path to the host audio file (default: `./files/preprocessed.wav`).
- `WATERMARK_TEXT`: The text to be embedded as a watermark (default: `'This is your watermark'`).
- `WATERMARK_SIGNAL_FILE`: Output path for the watermarked audio (default: `wmark_signal.wav`).
- `PSEUDO_RAND_FILE`: File to store the generated pseudo-random sequence (default: `pseudo_rand.dat`).
- `WATERMARK_ORIGINAL_FILE`: File to store the original watermark data (default: `watermark_binary.dat`).
- `WATERMARK_EXTENDED_FILE`: File to store the extended watermark data (default: `watermark_extended.dat`).
- `REP_CODE`: Boolean to enable/disable repetition coding for watermark robustness (default: `True`).
- FRAME_LENGTH: Length of each frame for analysis (default: `1024`).
- `CONTROL_STRENGTH`: Embedding strength controlling watermark intensity (default: `0.03`).
- `OVERLAP`: Overlap percentage between frames (default: `0.0`, no overlap).
- `NUM_REPS`: Number of repetitions per watermark bit if `REP_CODE` is enabled (default: `3`).

### Functions

`fix(xs)`
Emulates MATLAB's fix function, which rounds towards zero.

`embed()`
Embeds the watermark into the host audio signal. Generates a pseudo-random sequence, saves the original and extended watermark, and modifies the host signal accordingly.

`detect()`
Detects the watermark from the watermarked audio signal. It uses correlation with the pseudo-random sequence to recover the watermark and calculates the Bit Error Rate (BER) and Signal-to-Noise Ratio (SNR).

`main()`
The main function that orchestrates the embedding and detection processes.

## Results
After running the notebook, the original and recovered watermark texts will be printed, along with the Bit Error Rate (BER) and Signal-to-Noise Ratio (SNR) of the watermarked audio.

Example Output:
```plaintext
Copy code
ORIGINAL WATERMARK:  This is your watermark  
RECOVERED WATERMARK: This is your watermark  
bit error rate = 0.0 %  
SNR = 30.5dB
```  

## License

This project is licensed under the [Do What The **** You Want To Public License (WTFPL)](https://choosealicense.com/licenses/wtfpl/).

