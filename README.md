# PATCHROOM
A code-review desk that sends a file to your own local MiMo inference server. Hosted page is an interface, not hosted AI. The sample is deliberately flawed test data, not precomputed review output.

## Run with the linked model, free
1. Obtain the text-only Q5_K_M GGUF from https://huggingface.co/0xSojalSec/Abliterated-MiMo-V2.6-Distill-Qwen-9B-GGUF-MLX/tree/main (6.47 GB). The smaller Q4_K_M is 5.63 GB. Both were published without smoke tests. Review the upstream license before redistributing weights; the parent card currently does not state a license, despite the derivative's MIT label.
2. Use a recent llama.cpp build supporting Qwen3.5 hybrid. `llama-server -m /path/to/MiMo-V2.6-Distill-Qwen-9B-Abliterated-Q5_K_M.gguf -c 8192 --host 127.0.0.1 --port 18182`.
3. `node server.mjs` (Node 20+). Open the hosted page or index.html through a local static server, select Connect, and test. The bridge is loopback-only and allows the published site origin. Do not expose either service to the internet.

The bridge was built and syntax checked, but this project has not yet been inference-tested against those untested GGUF quantizations. Model output is fallible; never apply a fix without reviewing it. No code execution and no uploads by the hosted page.

Source: https://x.com/0x0SojalSec/status/2103298971032777123?s=46 . Model: https://huggingface.co/0xSojalSec/Abliterated-MiMo-V2.6-Distill-Qwen-9B-GGUF-MLX .
