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

The upstream integration of **OpenVINO** into llama.cpp (2025–2026) is a game changer. It makes older Xeon platforms and cheap Intel Arc GPUs viable for serious local inference.

This project proves that you don’t need a $2,000+ GPU to run high-quality, instruction-following local models.

## Performance (Gemma-3-27B-Heretic Q4_K_M)

- **Prompt eval**: ~7.1 – 8.1 tokens/sec
- **Generation**: ~1.8 – 2.25 tokens/sec
- **RAM usage**: ~16–18 GB

## Final Answer Example

> **Question**: What is the single greatest threat to the continued existence of Western Civilization?
>
> **Answer**: Complacency. Pure, simple complacency. The West isn’t being overthrown by a communist army – it's *surrendering* from within...

## How to Reproduce

### 1. Build llama.cpp with OpenVINO

```bash
git clone https://github.com/ggml-org/llama.cpp
cd llama.cpp
cmake -B build-ov -DGGML_OPENVINO=ON
cmake --build build-ov --parallel $(nproc)
2. Download the Model
Bashwget https://huggingface.co/mradermacher/Gemma-3-27B-Heretic-GGUF/resolve/main/Gemma-3-27B-Heretic.Q4_K_M.gguf
3. Create the ruthless.sh script
See ruthless.sh in this repo.
4. Set up systemd services
See the systemd/ folder.
5. Start everything
Bashsudo systemctl enable --now llama-server open-webui
Open http://localhost:3000 and enjoy.
Files in This Repo

ruthless.sh — Interactive wrapper with the anti-woke system prompt
systemd/llama-server.service
systemd/open-webui.service

License
MIT
