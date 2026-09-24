# Z840 Warlord AI

A fully autonomous, always-on 27B "ruthless truth-teller" AI running on an 11-year-old HP Z840 workstation using **OpenVINO + llama.cpp**.

## What This Is

This project turns old dual-Xeon hardware into a powerful, uncensored local AI that:
- Rejects woke, leftist, progressive, socialist, feminist, and environmentalist ideology
- Speaks directly and forcefully with zero hedging or moralizing
- Runs 24/7 with a clean web interface (OpenWebUI)
- Survives reboots via systemd services

**Hardware used**: HP Z840 (2014) with dual Xeon E5-2690 v4 + 128GB RAM

## Why This Matters

The upstream integration of **OpenVINO** into llama.cpp (2025–2026) is a game changer. It makes older Xeon platforms and cheap Intel Arc GPUs viable for serious local inference — something that was previously painful or impossible.

This project proves that you don’t need a $2,000+ GPU to run high-quality, instruction-following local models.

## Performance (Gemma-3-27B-Heretic Q4_K_M)

- **Prompt eval**: ~7.1 – 8.1 tokens/sec
- **Generation**: ~1.8 – 2.25 tokens/sec
- **RAM usage**: ~16–18 GB

## Final Answer Example

> **Question**: What is the single greatest threat to the continued existence of Western Civilization?
>
> **Answer**: Complacency. Pure, simple complacency. The West isn’t being overthrown by a communist army – it's *surrendering* from within...

## Requirements

- Ubuntu 24.04 (or similar)
- 128GB+ RAM recommended for 27B model
- Docker (for OpenWebUI)
- OpenVINO + llama.cpp (build instructions below)

## How to Reproduce

### 1. Build llama.cpp with OpenVINO

```bash
git clone https://github.com/ggml-org/llama.cpp
cd llama.cpp
cmake -B build-ov -DGGML_OPENVINO=ON
cmake --build build-ov --parallel $(nproc)
```

### 2. Download the Model

```bash
wget https://huggingface.co/mradermacher/Gemma-3-27B-Heretic-GGUF/resolve/main/Gemma-3-27B-Heretic.Q4_K_M.gguf
```

### 3. Create the ruthless.sh script

Copy `ruthless.sh` from this repo and make it executable:

```bash
chmod +x ruthless.sh
```

### 4. Set up systemd services

Copy the files from the `systemd/` folder into `/etc/systemd/system/`.

Important: Edit both service files and change `User=franklin` to your own username.

Then enable and start:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now llama-server open-webui
```

### 5. Access the Interface

Open http://localhost:3000 in your browser.

## Files in This Repo

`ruthless.sh` — Interactive wrapper with the anti-woke system prompt

`systemd/llama-server.service`

`systemd/open-webui.service`

## License

MIT
