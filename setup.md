1. git clone https://github.com/yachty66/Wan2.1.git
2. pip install -r requirements.txt
3. huggingface-cli download Wan-AI/Wan2.1-T2V-14B --local-dir ./Wan2.1-T2V-14B
4. python generate.py \
 --task t2v-14B \
 --size 1280*720 \
 --ckpt_dir ./Wan2.1-T2V-14B \
 --prompt "A beautiful cinematic shot of a boat sailing on the ocean at sunset."
