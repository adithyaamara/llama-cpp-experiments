# llama.cpp-experiments

A collection of single-page HTML experiments showcasing local AI inference with llama.cpp. Experiment with various AI models locally - all processing happens on your machine!

## 🎯 Description

This repository contains web-based experiments that demonstrate the power of running AI models locally using llama.cpp's server mode. Each experiment is a self-contained HTML file that connects to your local llama-server instance, ensuring complete privacy and offline functionality. From vision models to language models, explore the capabilities of local AI inference.

## 🚀 Live Demo

Visit the experiments at: https://[your-username].github.io/llama.cpp-experiments/

## 📋 Current Experiments

### 🖥️ Screen Capture Assistant

- **File**: `smolVLM2ScreenDemo.html`
- **Features**: Real-time screen capture analysis, conversation history, text-to-speech
- **Use Cases**: Accessibility, screen reading, automated monitoring
- **Model**: SmolVLM2 (vision-language model via llama.cpp)

### 🎥 Webcam Vision Assistant

- **File**: `smolVLMLocalDemo.html`
- **Features**: Live webcam feed analysis, real-time object detection
- **Use Cases**: Scene understanding, object recognition, visual assistance
- **Model**: SmolVLM-Instruct (running locally via llama.cpp)

## 🛠️ Setup Instructions

### Prerequisites
- A computer with sufficient RAM (8GB+ recommended)
- Modern web browser with WebRTC support
- Basic command line knowledge

### 1. Install llama.cpp

#### Download Pre-built Binaries
```bash
# Visit https://github.com/ggml-org/llama.cpp/releases
Download the latest release for your platform, extract folder, add it to environment variables.
```

### 2. Start llama-server

```bash

# Start server with vision model - Downloads model from hugging face, runs it, exposes a OpenAI style chat completions on localhost:8080
llama-server -hf ggml-org/SmolVLM2-500M-Video-Instruct-GGUF -n 100
```

### 4. Access Experiments

1. Clone this repository:
```bash
git clone https://github.com/adithyaamara/llama.cpp-experiments.git
cd llama.cpp-experiments
```

2. Open `index.html` in your browser or serve locally:
```bash
Open index.html directly in chrome
```

3. Grant camera/screen permissions when prompted

## 🔧 Configuration

### Model Settings
Edit the model name in the HTML files if using different models:
```javascript
const payload = {
  model: "your-model-name", // Change this
  messages: [...],
  max_tokens: 200
};
```

### Server Configuration
If running llama-server on different host/port:
```javascript
const res = await fetch("http://your-host:your-port/v1/chat/completions", {
  // ...
});
```

## 🎨 Features

- **🔒 Privacy First**: All processing happens locally
- **⚡ Real-time**: Live video/screen analysis
- **🔊 Accessibility**: Built-in text-to-speech
- **💬 Conversation**: Maintains context between interactions
- **📱 Responsive**: Works on desktop and mobile devices
- **🎛️ Configurable**: Adjustable intervals, prompts, and settings

## 🧪 Creating New Experiments

Each experiment should be a single HTML file with:

1. **Local Processing**: No external API calls except to local llama-server
2. **Self-contained**: All dependencies via CDN or inline
3. **Responsive Design**: Works across devices
4. **Privacy Focused**: No data collection or external requests

### Template Structure
```html
<!DOCTYPE html>
<html>
<head>
  <title>Your Experiment</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <!-- Your UI here -->
  <script>
    // Connect to local llama-server
    const response = await fetch("http://localhost:8080/v1/chat/completions", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        model: "your-model",
        messages: [/* your messages */]
      })
    });
  </script>
</body>
</html>
```

## 🐛 Troubleshooting

### Common Issues

**Server Connection Failed**
- Verify llama-server is running: `curl http://localhost:8080/health`
- Check firewall settings
- Ensure correct host/port configuration

**Camera/Screen Access Denied**
- Grant browser permissions for camera/screen capture
- Use HTTPS or localhost (required for some features)
- Check browser compatibility

**Slow Performance**
- Reduce model size (use quantized versions)
- Adjust `--threads` parameter
- Increase `--ctx-size` if needed
- Enable GPU acceleration if available

**Model Loading Issues**
- Verify model file exists and is complete
- Check model compatibility with llama.cpp version
- Ensure sufficient RAM/disk space

## 📊 Performance Tips

- **Use Quantized Models**: Q4_K_M or Q5_K_M for good quality/speed balance
- **Optimize Context Size**: Balance between memory usage and conversation length
- **GPU Acceleration**: Use `--n-gpu-layers` if you have compatible GPU
- **Thread Tuning**: Set `--threads` to your CPU core count

## 🤝 Contributing

1. Fork the repository
2. Create a new experiment HTML file
3. Update `index.html` to include your experiment
4. Test with local llama-server
5. Submit a pull request

### Contribution Guidelines
- Keep experiments self-contained (single HTML file)
- Ensure privacy (local processing only)
- Include clear documentation
- Test across different browsers
- Follow existing code style

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [llama.cpp](https://github.com/ggerganov/llama.cpp) - Amazing local inference engine
- [SmolVLM2](https://huggingface.co/HuggingFaceTB/SmolVLM2-1.7B-Instruct) - Efficient vision-language model
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework

## 📞 Support

- 🐛 **Issues**: [GitHub Issues](https://github.com/[your-username]/llama.cpp-experiments/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/[your-username]/llama.cpp-experiments/discussions)
- 📖 **Wiki**: [Project Wiki](https://github.com/[your-username]/llama.cpp-experiments/wiki)

---

*Built with ❤️ for the local AI
