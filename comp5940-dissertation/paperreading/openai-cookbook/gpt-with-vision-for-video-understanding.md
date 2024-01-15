# GPT with vision for video understanding

```
// bibtex reference
@misc{OpenaiCookbook,
    author = {{Openai}},
    year = {2023},
    title = {Openai Cookbook},
    howpublished = {\url{https://cookbook.openai.com}}    
}
```

[https://github.com/openai/openai-cookbook/blob/main/examples/GPT\_with\_vision\_for\_video\_understanding.ipynb](https://github.com/openai/openai-cookbook/blob/main/examples/GPT\_with\_vision\_for\_video\_understanding.ipynb)

该demo将视频通过抽帧的方式输入gpt4，并配有任务描述。

```python
// Some code
from IPython.display import display, Image, Audio

import cv2  # We're using OpenCV to read video, to install !pip install opencv-python
import base64
import time
from openai import OpenAI
import os
import requests

client = OpenAI()
video = cv2.VideoCapture("data/bison.mp4")

base64Frames = []
while video.isOpened():
    success, frame = video.read()
    if not success:
        break
    _, buffer = cv2.imencode(".jpg", frame)  # 通过cv2将帧图片转换为jpg形式并压缩
    base64Frames.append(base64.b64encode(buffer).decode("utf-8"))  # 通过base64将字节流编码

video.release()
display_handle = display(None, display_id=True)
for img in base64Frames:
    display_handle.update(Image(data=base64.b64decode(img.encode("utf-8"))))  # 本地展示需要先解码
    time.sleep(0.025)

# message构建，将文本和图片信息构建成一个content（单轮对话）
PROMPT_MESSAGES = [
    {
        "role": "user",
        "content": [  # 未采取left padding形式，而是将图片放在末端？与VQA相悖，有待尝试……
            "These are frames from a video that I want to upload. Generate a compelling description that I can upload along with the video.",
            *map(lambda x: {"image": x, "resize": 768}, base64Frames[0::50]),  # 图片帧
        ],
    },
]
# 请求函数的参数头
params = {
    "model": "gpt-4-vision-preview",
    "messages": PROMPT_MESSAGES,  # 实际消息
    "max_tokens": 200,
}

result = client.chat.completions.create(**params)
print(result.choices[0].message.content)
```
