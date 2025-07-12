Granular Synthesizer using Teensy 4.1 or Grynth

firmware and documentation for a real-time granular synthesizer implemented on the Teensy 4.1 microcontroller. 
Designed as an engineering capstone project, the system demonstrates real-time digital audio synthesis with integrated signal processing, hardware interfacing, and embedded control.

Project Objectives:
Implement a standalone embedded synthesizer using granular synthesis techniques
Achieve real-time audio processing with low latency and acceptable THD+N
Enable live parameter manipulation via physical controls and dual-display UI
Integrate onboard sampling, delay, and reverb within performance constraints
Evaluate performance according to engineering audio standards

System Overview
| Component |      |Description |
| Microcontroller  | Teensy 4.1, 600 MHz ARM Cortex-M7 |
| Audio Engine     | Teensy Audio Library (modular DSP graph) |
| Input Devices    | Rotary encoders, tactile switches |
| Displays         | OLED (parameter UI) + TFT (waveform visualization) |
| Audio I/O        | SGTL5000-based Teensy Audio Shield |

/src → Main source files (modular C++)
├── main.cpp → Main setup/loop, state machine, control routing
├── audio_engine.cpp → Audio signal chain (VCO, granular, FX, output)
├── ui.cpp → Display updates, control mode, knob interactions
├── effects.cpp → Reverb, delay parameters, dry/wet mix
└── sampler.cpp → Sampling logic, freeze mode, granular loading

/hardware → Schematics, pinout, wiring diagrams
/docs → Latency tests, oscilloscope plots, FFT screenshots
/firmware → Precompiled Teensy .hex files

Performance Metrics
Parameter    Measured Value    Reference Standard
Latency    ~20 ms    Acceptable: < 60 ms
THD    0.01% (–80 dB)    AES17, IEC 60268-3
THD+N    >60% (under review)    High noise suspected
Audio Fidelity    44.1 kHz / 16-bit    CD-quality standard
Max Grain Voices    4 simultaneous grains    Teensy DSP capacity
Audio Memory    60 blocks allocated    Real-time safe margin

🧪 Test Methodology
Latency: Measured using Audacity, recording the mechanical click and output waveform, then calculating Δt.
THD / THD+N: Measured using Visual Analyzer with FFT while playing sine waves.
Frequency Response: Tested using white noise sweep and FFT plots.

Design Constraints
Cost Limit: ≤ 10,000 THB total system cost
Latency: ≤ 60 ms
Audio Quality: ≥ 44.1 kHz, 16-bit
Power: USB 5V or external battery (300–500 mA max)

References
AES17-2020: Measurement of Audio Equipment – Audio Engineering Society
IEC 60268-3: Sound System Equipment – Amplifiers – International Electrotechnical Commission
MIDI 1.0 Specification – MIDI Manufacturers Association
Teensy Audio Library Documentation – PJRC

🛠️ Setup & Compilation
Dependencies:
Teensyduino 1.58+
Adafruit SSD1306 + GFX libraries
ILI9341_t3 or TFT_eSPI (for TFT display)
