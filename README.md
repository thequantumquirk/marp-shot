# MarpShot

In the rapidly evolving digital landscape, the demand for compelling and credible content has
never been higher. Our groundbreaking project aims to redefine content creation by introducing
a suite of AI-powered tools meticulously designed for content creators and marketing agencies.
This innovative suite seamlessly integrates cutting-edge technologies to enhance the entire
content creation process.

## Key Features

1. AI Auto Blog: Unlock the potential of our system to effortlessly produce engaging and
high-quality blog posts across any conceivable topic. Our AI leverages advanced data analysis
techniques, delivering valuable insights that captivate your audience.

2. AI Genie: Elevate the credibility and authority of your content by
posing questions and receiving accurate, well-supported answers. Our AI-driven system
ensures that your content is not just informative but is backed by solid references.

3. Truth Tracker: Uphold the integrity of your content with our AI-driven fact verification,
cross-referencing information against trusted sources. Say goodbye to inaccuracies and
embrace content that stands up to scrutiny.

4. Present Perfect: Transform the way you create presentations by letting our AI
analyze your topic, extract key points, and design visually appealing slides. Effortlessly convey
your message with dynamic presentations that leave a lasting impression.

5. Util Gen: Harness the power of our AI-driven utilities to perform operations on text such as rephrasing, extending, shredding, and more. Empower your content creation process with advanced text manipulation capabilities.

6. Product Gen: Utilize our AI-powered product generation tool to effortlessly create detailed product reviews and descriptions. Streamline your content creation process and captivate your audience with compelling product narratives.

## Demo
**Landing Page**:
![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/44743770-8475-4c3e-833b-fb717ec11a21)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/87ed0b88-3501-4e61-975b-c9540c373c73)

**AI Auto Blog**:
![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/c38a110d-afb3-4dd6-85f8-9b9e5056c006)

**Truth Tracker**:
![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/ee15b2e8-d039-4408-8452-28ff74d50696)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/e879d8ec-82a5-498f-8b55-9247436944f3)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/382c8710-6c59-4caa-a51b-227238c4e06b)

**Present Prefect**:

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/080c9906-004a-448c-a7d0-4a5f23fcb965)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/1514083c-0751-4f6a-9a91-c618f0e0f5f5)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/262fd59a-4c87-4598-99e3-b1ae882239f1)
Demo Presentation

**Util Gen**:

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/360a28b4-e420-4b88-af0a-ce731b998752)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/06e0143b-9626-4113-bac7-9d37c26034fc)

**AI Genie**:

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/be1c2760-47e8-437d-8a04-b6288b38d2bf)

**Product Gen**:

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/6023c0bf-c69b-4544-aa38-4bf8ee545373)

![image](https://github.com/thequantumquirk/marp-shot/assets/67329471/fdebaa38-69cd-453a-9c49-13a9ac226b3e)

## What's under the hood?

### LLM

- [Longshot APIs](https://docs.longshot.ai): Utilized for generations that require internet (Eg. Truth Tracker)

- [Intel® llm-on-ray](https://github.com/intel/llm-on-ray): Used to do finetuning and interference.

### Backend

- [Bun](https://bun.sh/): Poweres the Backend for the App
- [Marp](https://marp.app/): Takes care of generating the presentation with the content from LLM

### Frontend

- [Next.js](https://nextjs.org/): Heart of the frontend
- [Shadcn/ui](https://ui.shadcn.com/): Provides all the components needed to bulid the app
- [Aceternity UI](https://ui.aceternity.com/): Add the <3 to the UI

## LLM on Ray

This section explains about Intel®'s llm-on-ray and how we utilized Intel®'s llm-on-ray to finetune and interference for the LLM.

### Introduction about LLM on Ray

LLM-on-Ray is a comprehensive solution designed to empower users in building, customizing, and deploying Large Language Models (LLMs). Whether you're starting from scratch with pretraining, looking to finetuning an existing model, or aiming to deploy a production-ready LLM endpoint service, this project simplifies these complex processes into manageable steps.

LLM-on-Ray harnesses the power of Ray, an industry-leading framework for distributed computing, to scale your AI workloads efficiently. This integration ensures robust fault tolerance and cluster resource management, making your LLM projects more resilient and scalable.

LLM-on-Ray is built to operate across various hardware setups, including Intel CPU, Intel GPU and Intel Gaudi2. It incorporates several industry and Intel optimizations to maximize performance, including [vLLM](https://github.com/vllm-project/vllm), [llama.cpp](https://github.com/ggerganov/llama.cpp), [Intel Extension for PyTorch](https://github.com/intel/intel-extension-for-pytorch)/[Deepspeed](https://github.com/intel/intel-extension-for-deepspeed), [BigDL-LLM](https://github.com/intel-analytics/BigDL), [RecDP-LLM](https://github.com/intel/e2eAIOK/tree/main/RecDP/pyrecdp/LLM), [NeuralChat](https://huggingface.co/Intel/neural-chat-7b-v3-1) and more.

Read more about llm-on-ray [here](marp-shot-llm/README.md)

### Finetuning with LLM on Ray

Finetuning LLMs with LLM on Ray is very simple and straight forward. Follow the steps below to Finetune your own LLM:

1. Setup llm-on-ray by following the steps on [Setup.md](marp-shot-llm/docs/setup.md)

2. Now run the following command to start fine tuning

```bash
llm_on_ray-finetune --config_file finetune.yaml
```

We have used our own data set `marp-dataset.jsonl` and `mistralai/Mistral-7B-v0.1` model to fine tune our custom model using the config [finetune.yaml](marp-shot-llm/finetune.yaml)

3. Find your model at `/tmp/llm-ray/output`

It's that simple :P.

### Interference with LLM on Ray

As like the finetuning Interference is also simple with llm-on-ray.

1. Specify all your needs in a yaml file. You can check our [interference.yaml](marp-shot-llm/interference.yaml) or other examples [here](marp-shot-llm/llm_on_ray/inference/models/)

2. Start the interference server via the following command

```bash
llm_on_ray-serve --config_file interference.yaml --simple
```

To test your server you can use this script

```bash
python examples/inference/api_server_simple/query_single.py --model_endpoint http://127.0.0.1:8000/mistral-7b-v0.1
```

3. Alternatively you can also start an OpenAI-compatible API server (OpenAI API Reference)[https://platform.openai.com/docs/api-reference/chat] by the following command

```bash
llm_on_ray-serve --config_file interference.yaml
```

### Benchmarks with LLM on Ray

There are two benchmarks:

1. Performance Benchmarks
2. Ease of Use Benchmarks

#### Performance 

![bar-graph](https://github.com/thequantumquirk/marp-shot/assets/67329471/790f60b2-96dd-4126-b1f3-5c3b71bfe963)

The Interference for same model and same hardware has brought in more than 5x improvements compared to using other approaches.

#### Ease of Use

![bar-graph(1)](https://github.com/thequantumquirk/marp-shot/assets/67329471/017c01a5-fac8-4e55-bc0b-aa0055a9e810)

The amount of time spent exploring, learning and debugging while finetuning and interference has drastically reduced upto 8x.

### Conclusion

LLM-on-Ray is a revolutionary solution that simplifies the process of building, customizing, and deploying Large Language Models (LLMs). Leveraging the power of Ray for distributed computing, LLM-on-Ray ensures efficient scaling of AI workloads with robust fault tolerance and cluster resource management. This project is designed to operate seamlessly across various hardware setups, including Intel CPU, Intel GPU, and Intel Gaudi2, incorporating industry and Intel optimizations such as vLLM, llama.cpp, Intel Extension for PyTorch/Deepspeed, BigDL-LLM, RecDP-LLM, and NeuralChat. With LLM-on-Ray, users can easily pretrain models, fine-tune existing ones, and deploy production-ready LLM endpoint services, making complex AI tasks manageable and scalable.

## Road Map

![MarpShot](https://github.com/thequantumquirk/marp-shot/assets/67329471/74d24443-c872-4530-adf9-cf4d10163907)
