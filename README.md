# vLLM-quickstart

vLLM框架的Quickstart指南提供了一个简单而快速的方法来部署和使用vLLM进行大型语言模型(LLM)的推理和服务。以下是基于搜索结果的vLLM框架快速开始的步骤：

1. **安装vLLM**：
   - 首先，你需要安装vLLM库。这可以通过Python的包管理器pip来完成。如果你想创建一个新的conda环境，可以先创建环境，然后在该环境中安装vLLM。以下是安装命令的示例：
     ```bash
     conda create -n myenv python=3.8 -y
     conda activate myenv
     pip install vllm
     ```

2. **下载模型权重**：
   - 在开始之前，你需要下载模型权重。对于一些大型模型，如llama2，模型权重可能非常大（例如10GB左右），因此在国内可能会遇到网络不稳定的问题。你可以参考相关的下载教程来获取模型权重。

3. **配置和启动服务**：
   - 使用vLLM，你可以构建一个与OpenAI API兼容的API服务。vLLM支持多种Huggingface模型架构，包括但不限于GPT-2、GPT-J、GPT-NeoX等。你可以通过配置文件和环境变量来设置服务参数，例如并行度、数据类型等。

4. **使用Rolling Batch加速推理**：
   - vLLM提供了Rolling Batch的功能，这可以通过配置化方式在推理服务器上实现，无需安装和部署vLLM库或开发封装vLLM engine的服务器端应用。这在Amazon SageMaker上特别有用，因为SageMaker推理容器支持HuggingFace的Transformers和vLLM两种动态batch框架。

5. **部署在SageMaker上**：
   - 如果你使用Amazon SageMaker，可以通过SageMaker SDK的`image_uris`来指定Large Model Inference（LMI）容器的镜像版本，并通过`serving.properties`配置文件来设置对应的vLLM部署参数。

6. **性能测试**：
   - vLLM项目下的benchmark目录提供了测试脚本，允许你对服务进行性能测试。这包括测试服务的稳定性、延迟和性能等关键指标。

7. **分布式多GPU部署**：
   - vLLM原生支持多节点多GPU部署，基于ray的分布式计算框架。你可以在Docker环境中基于ray连接各节点，组成cluster，并在主节点上运行大模型API启动命令。

以上步骤概述了vLLM框架的快速开始过程，具体的命令和配置可能会根据你的环境和需求有所不同。更详细的信息可以在vLLM的官方文档和相关博客文章中找到[1][2][3][4][5][6].

Citations:
[1] https://aws.amazon.com/cn/blogs/china/accelerate-sagemaker-llm-model-inference-performance-using-rolling-batch/
[2] https://blog.csdn.net/weixin_45920955/article/details/135300561
[3] https://www.zhihu.com/question/611905691/answer/3208379424
[4] https://blog.csdn.net/qq_39749966/article/details/135194629
[5] https://www.xiaoiluo.com/article/vllm-gpu-ray-multigpu
[6] https://qwen.readthedocs.io/zh-cn/latest/getting_started/quickstart.html
[7] https://developer.aliyun.com/article/1380325
[8] https://github.com/HIT-SCIR/huozi/blob/main/README.md
