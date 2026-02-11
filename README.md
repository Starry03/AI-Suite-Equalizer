# AI 

Version 1.0.3

## About

This project is an experiment that aims to create a suite of high-quality audio plugins using AI.
We want to provide producers the tools to create music, because we believe that knowledge, art and everything else should be free and accessible to everyone.

## Disclaimer

I studied computer science and I produce music, however, my knowledge about audio processing is very limited to music production and sound design in practice.

## Installation

As there could be non programmers reading this, I will go straight to the point. There is not a "ready" version of this program yet. Usually you would have an installer (.exe, .dmg, .deb, etc) that you can download and install on your computer. However, this project is still in development and there is no installer available yet (or precompiled binaries).

### Dependencies

- cmake
- c compiler (gcc, clang, etc)

### Steps to install

Open a terminal (cmd, powershell, bash, etc) and run the following commands

1. Clone the repository

   ```bash
   git clone --recursive https://github.com/Starry03/AI-Suite-Equalizer.git
   ```

2. Build the project using cmake and install it (in most common folders based on OS)

   ```bash
   cd AI-Suite-Equalizer
   mkdir build
   cmake --build build --target AnalogEQ_VST3
   ```

## 