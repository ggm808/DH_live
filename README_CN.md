# 实时直播数字人
# 实时直播数字人 [哔哩哔哩视频](https://www.bilibili.com/video/BV1Ppv1eEEgj/?vd_source=53601feee498369e726af7dbc2dae349)

### 新闻

## 训练
有关渲染模型训练的详细信息，请查看 [这里](https://github.com/kleinlee/DH_live/tree/master/train)。

### 视频示例
![视频示例](https://github.com/user-attachments/assets/7e0b5bc2-067b-4048-9f88-961afed12478)

## 概述
该项目是一个实时直播数字人，基于少样本学习技术。它旨在在所有30系列和40系列显卡上顺畅运行，确保无缝且互动的直播体验。

### 主要特性
- **实时性能**：数字人可以在超过25帧每秒的速度下与NVIDIA 30系列和40系列GPU实时互动
- **少样本学习**：系统能够从少量示例中学习，生成真实的响应。

## 使用方法

### 创建环境并解压模型文件
首先，导航到 `checkpoint` 目录并解压模型文件：
```bash
conda create -n dh_live python=3.12
conda activate dh_live
pip install torch --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
cd checkpoint
gzip -d -c render.pth.gz.001 > render.pth
```

### 准备视频
接下来，使用数据准备脚本准备视频。将 YOUR_VIDEO_PATH 替换为视频的路径：
```bash
python data_preparation.py YOUR_VIDEO_PATH
```
结果（video_info）将存储在 ./video_data 目录中。

### 使用音频文件运行
运行带有音频文件的演示脚本。确保音频文件为 .wav 格式，采样率为16kHz，16位单声道。将 video_data/test 替换为你的视频信息文件路径，video_data/audio0.wav 替换为音频文件路径，1.mp4 替换为所需的输出视频路径：
```bash
python demo.py video_data/test video_data/audio0.wav 1.mp4
```

### 使用麦克风进行实时运行
要使用麦克风进行实时操作，只需运行以下命令：
```bash
python demo_avatar.py
```

## 致谢
我们感谢 [Wav2Lip](https://github.com/Rudrabha/Wav2Lip)、[DINet](https://github.com/MRzzm/DINet)、[LiveSpeechPortrait](https://github.com/YuanxunLu/LiveSpeechPortraits) 项目的贡献者们，感谢他们的开放研究和贡献。

## 许可
该项目遵循 MIT 许可协议。

## 联系
如有任何问题或建议，请联系 [kleinlee1@outlook.com]。
