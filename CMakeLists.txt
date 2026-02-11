cmake_minimum_required(VERSION 3.15)

project(AnalogEQ VERSION 1.0.3 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add JUCE framework
add_subdirectory(JUCE)

# Define plugin formats
juce_add_plugin(AnalogEQ
    COMPANY_NAME "Starry"
    PLUGIN_MANUFACTURER_CODE Stry
    PLUGIN_CODE AneQ
    FORMATS AU VST3 Standalone
    PRODUCT_NAME "Analog EQ"
    
    # Version (semantic versioning: MAJOR.MINOR.PATCH)
    VERSION 1.0.3
    BUNDLE_ID com.starrydsp.analogeq
    
    # Description
    DESCRIPTION "Modular Analog-Style Graphic Equalizer with Interactive UI"
    
    # Plugin characteristics
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE
    NEEDS_MIDI_OUTPUT FALSE
    IS_MIDI_EFFECT FALSE
    EDITOR_WANTS_KEYBOARD_FOCUS TRUE
    COPY_PLUGIN_AFTER_BUILD TRUE
    
    # Format-specific categories
    VST3_CATEGORIES Fx EQ
    AU_MAIN_TYPE kAudioUnitType_Effect
)

# Source files
target_sources(AnalogEQ
    PRIVATE
        Source/PluginProcessor.cpp
        Source/PluginEditor.cpp
        Source/DSP/FilterBase.h
        Source/DSP/FilterTypes.h
        Source/DSP/FilterChain.h
        Source/DSP/FilterChain.cpp
        Source/UI/FrequencyResponseCurve.h
        Source/UI/FrequencyResponseCurve.cpp
        Source/UI/FilterNode.h
        Source/UI/FilterNode.cpp
        Source/UI/ModernLookAndFeel.h
        Source/UI/ModernLookAndFeel.cpp
        Source/UI/ParameterTooltip.h
        Source/UI/ParameterTooltip.cpp
        Source/UI/SpectrumAnalyzer.h
        Source/UI/SpectrumAnalyzer.cpp
        Source/UI/FilterControlPanel.h
        Source/UI/FilterControlPanel.cpp
        Source/UI/DBMeter.h
        Source/UI/DBMeter.cpp
        Source/Utils/ParameterHelper.h
        Source/Utils/ParameterHelper.cpp
)

# Preprocessor definitions
target_compile_definitions(AnalogEQ
    PUBLIC
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
        JUCE_VST3_CAN_REPLACE_VST2=0
        JUCE_DISPLAY_SPLASH_SCREEN=0
        JUCE_REPORT_APP_USAGE=0
)

# Link JUCE modules
target_link_libraries(AnalogEQ
    PRIVATE
        juce::juce_audio_utils
        juce::juce_dsp
    PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags
)
