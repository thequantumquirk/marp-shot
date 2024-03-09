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

## Road Map

