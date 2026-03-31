# -EdgeAI-Water-Quality-Monitor
Edge AI based Water Pollution Monitoring System  using LSTM + Random Forest on ESP32 | Final Year Project | DGCT ECE 2026
# 🌊 Edge-AI Water Quality Monitoring System

> Final Year Project | B.E. ECE | DGCT Salem | 2026
> Team: Shivpriya M, Piriya Harini S, Roshini M.M, Susmitha G
> Guide: Dr. S. Venkatesh, HOD/ECE

## 📌 Project Overview
An intelligent IoT system that monitors water quality in
real-time using Edge AI deployed directly on ESP32 —
no cloud dependency for inference.

## 🎯 Key Results
| Metric        | Value     |
|---------------|-----------|
| Accuracy      | 100.00%   |
| F1 Score      | 1.0000    |
| Model Size    | 69.59 KB  |
| Inference     | <30ms     |
| Target Device | ESP32     |

## 🔬 Parameters Monitored
| Sensor      | Parameter     | Unit  |
|-------------|---------------|-------|
| SEN0161     | pH            | –     |
| Turbidity   | Turbidity     | NTU   |
| TDS Sensor  | Total Dissolved Solids | ppm |
| DS18B20     | Temperature   | °C    |
| DO Sensor   | Dissolved Oxygen | mg/L |

## 🏷️ Water Quality Classes
| Class    | Meaning                        | Alert          |
|----------|--------------------------------|----------------|
| SAFE     | Drinkable — all params normal  | ✅ No alert    |
| MODERATE | Borderline — monitor closely   | 💛 LED Yellow  |
| POLLUTED | Harmful — action needed        | 🔴 LED + Buzzer + SMS |
| CRITICAL | Dangerous — immediate action   | 🚨 All alerts  |

## 🧠 Model Architecture
```
Input (10 timesteps × 5 features)
    ↓
LSTM Layer 1 (64 units) + BatchNorm + Dropout
    ↓
LSTM Layer 2 (32 units) + BatchNorm + Dropout
    ↓
Dense (32) → Random Forest Ensemble
    ↓
INT8 TFLite Quantization (69.59 KB)
    ↓
ESP32 Deployment
```

## 📁 Repository Structure
```
├── water_quality_model.h        ← ESP32 C++ header
├── water_quality_int8.tflite    ← Quantized model
├── lstm_water_quality.keras     ← Full Keras model
├── random_forest_model.pkl      ← Random Forest
├── minmax_scaler.pkl            ← Normalization params
├── lstm_training_history.png    ← Training curves
├── confusion_matrices.png       ← Evaluation charts
├── model_comparison.png         ← Performance comparison
└── EdgeAI_WaterQuality.ipynb    ← Training notebook
```

## 🛠️ Tech Stack
- **Hardware:** ESP32, pH sensor, Turbidity, TDS, DS18B20, DO
- **ML Framework:** TensorFlow / Keras
- **Model:** LSTM + Random Forest Ensemble
- **Deployment:** TFLite INT8 Quantization
- **Cloud:** MQTT → ThingSpeak / AWS IoT
- **Alert:** LED + Buzzer + GSM SIM800L SMS

## 📊 Training Results
- Dataset: 8000 synthetic samples (WHO/BIS standards)
- Classes: 4 (SAFE / MODERATE / POLLUTED / CRITICAL)
- Window size: 10 samples (10 seconds)
- Train/Val/Test split: 70/15/15

## 📚 References
Based on WHO and BIS Indian drinking water quality standards.

