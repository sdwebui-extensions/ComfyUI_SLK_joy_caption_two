
## Recent changes 
* [2024-10-12] v0.0.1: 基本完成[JoyCaptionAlpha Two](https://huggingface.co/spaces/fancyfeast/joy-caption-alpha-two)到ComfyUI的实现


## ComfyUI上JoyCaptionAlpha Two的实现

参考自 [Comfyui_CXH_joy_caption](https://github.com/StartHua/Comfyui_CXH_joy_caption), 以及 [JoyCaptionAlpha Two](https://huggingface.co/spaces/fancyfeast/joy-caption-alpha-two)

参考工作流在examples/workflow.png中获取:
![image](./examples/workflow.png)

### 依赖安装

1. 把仓库下载克隆到 custom_nodes 子文件夹下。
```
cd custom_nodes
git clone https://github.com/EvilBT/ComfyUI_SLK_joy_caption_two.git
```
2. 安装相关依赖：
```angular2html
pip install -r ComfyUI_SLK_joy_caption_two\requirements.txt
```
3. 下载相关模型。
4. 重启ComfyUI。

### 相关模型下载
以下的models目录是指ComfyUI根目录下的models文件夹
#### 1. google/siglip-so400m-patch14-384:

国外：[google/siglip-so400m-patch14-384](https://huggingface.co/google/siglip-so400m-patch14-384)

国内：[hf/google/siglip-so400m-patch14-384](https://hf-mirror.com/google/siglip-so400m-patch14-384)

会自动下载，也可以手动下载整个仓库，并把siglip-so400m-patch14-384内的文件全部复制到`models/clip/siglip-so400m-patch14-384`
![image](./examples/clip.png)
#### 2. Llama3.1-8B 模型下载

支持两个版本：bnb-4bit是小显存的福音，我是使用这个版本的，原版的我没有测试过，可自行测试。程序会自动下载，可自行下载。

2.1 [unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit](https://huggingface.co/unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit)

国内可以从镜像网站下载[hf/unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit](https://hf-mirror.com/unsloth/Meta-Llama-3.1-8B-Instruct-bnb-4bit)

把整个文件夹内的内容复制到 `models\LLM\Meta-Llama-3.1-8B-Instruct-bnb-4bit` 下


国内:[meta-llama/Meta-Llama-3.1-8B](https://hf-mirror.com/meta-llama/Llama-3.1-8B)

把下载后的整个文件夹的内容复制到`models\LLM\Meta-Llama-3.1-8B`下
![image](./examples/Llama3.1-8b.png)

#### 3. Joy-Caption-alpha-two 模型下载（必须手动下载）

把 [Joy-Caption-alpha-two](https://huggingface.co/spaces/fancyfeast/joy-caption-alpha-two/tree/main) 下的`cgrkzexw-599808`
文件夹的所有内容下载复制到`models/Joy_caption_two` 下
![image](./examples/joy_caption.png)
### 重启ComfyUI之后就可以添加使用了，具体可以参考下面的图片
![image](./examples/workflow.png)
![image](./examples/workflow_flux.png)

### 其他

如果你安装了 [AIGODLIKE-ComfyUI-Translation](https://github.com/AIGODLIKE/AIGODLIKE-ComfyUI-Translation) 语言包插件，你可以复制 `translation` 文件夹下的中文翻译到对应的语言包路径下，重启就可以使用中文版的了。
把 `translation/zh-CN/Nodes/Comfyui_SLK_joy_caption_two.json` 复制到目录：`AIGODLIKE-ComfyUI-Translation\zh-CN\Nodes` 即可

有问题可以开issue问我，未完全测试，我是8G显存的环境