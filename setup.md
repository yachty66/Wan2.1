1. start a gpu best case with torch 2.4 env (runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04) to make following setup easier 
1. git clone https://github.com/yachty66/Wan2.1.git
2. pip install -r requirements.txt 
    - in the case its failing (python -m pip install ninja packaging)
    - change req file to the following:
        torch==2.1.0
        torchvision==0.16.0
        opencv-python>=4.9.0.80
        diffusers>=0.31.0
        transformers>=4.49.0
        tokenizers>=0.20.3
        accelerate>=1.1.1
        tqdm
        imageio
        easydict
        ftfy
        dashscope
        imageio-ffmpeg
        flash-attn==2.5.8
        gradio>=5.0.0
        numpy>=1.23.5,<2
    - pip install -r requirements.txt
3. huggingface-cli download Wan-AI/Wan2.1-T2V-14B --local-dir ./Wan2.1-T2V-14B
4. python generate.py \
 --task t2v-14B \
 --size 1280*720 \
 --ckpt_dir ./Wan2.1-T2V-14B \
 --prompt "A beautiful cinematic shot of a boat sailing on the ocean at sunset."


## multi gpu

1. start a gpu best case with torch 2.4 env (runpod/pytorch:2.4.0-py3.11-cuda12.4.1-devel-ubuntu22.04) to make following setup easier 
2. git clone https://github.com/yachty66/Wan2.1.git
3. pip install -r requirements.txt 
4. pip install "xfuser>=0.4.1"
5. huggingface-cli download Wan-AI/Wan2.1-T2V-14B --local-dir ./Wan2.1-T2V-14B
6. torchrun --nproc_per_node=2 generate.py \
--task t2v-14B \
--size 1280*720 \
--ckpt_dir ./Wan2.1-T2V-14B \
--dit_fsdp \
--t5_fsdp \
--ulysses_size 2 \
--prompt "A beautiful cinematic shot of a boat sailing on the ocean at sunset."