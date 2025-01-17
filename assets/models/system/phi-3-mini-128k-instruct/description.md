---
license: mit
license_link: https://huggingface.co/microsoft/Phi-3-mini-128k-instruct/resolve/main/LICENSE

language:
- en
pipeline_tag: text-generation
tags:
- nlp
- code
---

## Model Details

Phi-3 Mini-128K-Instruct is a 3.8B parameters, lightweight, state-of-the-art open model built upon datasets used for Phi-2 - synthetic data and filtered websites - with a focus on very high-quality, reasoning dense data. The model belongs to the Phi-3 model family, and the Mini version comes in two variants 4K and 128K which is the context length (in tokens) it can support.

The model underwent a rigorous enhancement process, incorporating both supervised fine-tuning and direct preference optimization to ensure precise instruction adherence and robust safety measures.
When assessed against benchmarks testing common sense, language understanding, math, code, long context and logical reasoning, Phi-3 Mini-128K-Instruct showcased a robust and state-of-the-art performance among models with less than 13 billion parameters.

Resources and Technical Documentation:

+ [Phi-3 Microsoft Blog](https://aka.ms/phi3blog-april)
+ [Phi-3 Technical Report](https://aka.ms/phi3-tech-report)

## Training Details

### **Model**

* Architecture: Phi-3 Mini-128K-Instruct has 3.8B parameters and is a dense decoder-only Transformer model. The model is fine-tuned with Supervised fine-tuning (SFT) and Direct Preference Optimization (DPO) to ensure alignment with human preferences and safety guidlines.
* Inputs: Text. It is best suited for prompts using chat format.
* Context length: 128K tokens
* GPUs: 512 H100-80G
* Training time: 7 days
* Training data: 3.3T tokens
* Outputs: Generated text in response to the input
* Dates: Our models were trained between February and April 2024
* Status: This is a static model trained on an offline dataset with cutoff date October 2023. Future versions of the tuned models may be released as we improve models.

### **Datasets**

The training data includes a wide variety of sources, totaling 3.3 trillion tokens, and is a combination of 
1) Publicly available documents filtered rigorously for quality, selected high-quality educational data, and code; 
2) Newly created synthetic, “textbook-like” data for the purpose of teaching math, coding, common sense reasoning, general knowledge of the world (science, daily activities, theory of mind, etc.); 
3) High quality chat format supervised data covering various topics to reflect human preferences on different aspects such as instruct-following, truthfulness, honesty and helpfulness.

## Intended Uses

### **Primary use cases**

The model is intended for commercial and research use in English. The model provides uses for applications which require:

1) Memory/compute constrained environments
2) Latency bound scenarios
3) Strong reasoning (especially math and logic)

The model is designed to accelerate research on language and multimodal models, for use as a building block for generative AI powered features. 

### **Use case considerations**

The model is not specifically designed or evaluated for all downstream purposes. Developers should consider common limitations of language models as they select use cases, and evaluate and mitigate for accuracy, safety, and fariness before using within a specific downstream use case, particularly for high risk scenarios. Developers should be aware of and adhere to applicable laws or regulations (including privacy, trade compliance laws, etc.) that are relevant to their use case.

Nothing contained in this Model Card should be interpreted as or deemed a restriction or modification to the license the model is released under.  


## Benchmarks

We report the results for Phi-3-Mini-128K-Instruct on standard open-source benchmarks measuring the model's reasoning ability (both common sense reasoning and logical reasoning). We compare to Phi-2, Mistral-7b-v0.1, Mixtral-8x7b, Gemma 7B, and GPT-3.5.

All the reported numbers are produced with the exact same pipeline to ensure that the numbers are comparable. These numbers might differ from other published numbers due to slightly different choices in the evaluation.

As is now standard, we use few-shot prompts to evaluate the models, at temperature 0. 
The prompts and number of shots are part of a Microsoft internal tool to evaluate language models, and in particular we did no optimization to the pipeline for Phi-3.
More specifically, we do not change prompts, pick different few-shot examples, change prompt format, or do any other form of optimization for the model.

The number of k–shot examples is listed per-benchmark. 

|| Phi-3-Mini-128K-In<br>3.8b (this model) | Phi-3-Small<br>7b (preview) | Phi-3-Medium<br>14b (preview) | Phi-2<br>2.7b | Mistral<br>7b | Gemma<br>7b | Mixtral<br>8x7b | GPT-3.5<br>version 1106 |
|---|---|---|---|---|---|---|---|---|
|MMLU <br>5-Shot |68.10|75.60|78.20|56.3|61.70|63.60|70.50|71.40|
|HellaSwag <br> 5-Shot |74.50|78.70|83.00|53.6|58.50|49.80|70.40|78.80|
|ANLI <br> 7-Shot |52.80|55.00|58.70|42.5|47.10|48.70|55.20|58.10|
|GSM-8K <br> 0-Shot; CoT |83.60|88.90|90.30|61.1|46.40|59.80|64.70|78.10|
|MedQA <br> 2-Shot |55.30|58.20|69.40|40.9|50.00|49.60|62.20|63.40|
|AGIEval <br> 0-Shot |36.90|45.00|48.40|29.8|35.10|42.10|45.20|48.40|
|TriviaQA <br> 5-Shot |57.10|59.10|75.60|45.2|75.20|72.30|82.20|85.80|
|Arc-C <br> 10-Shot |84.00|90.70|91.00|75.9|78.60|78.30|87.30|87.40|
|Arc-E <br> 10-Shot |95.20|97.10|97.80|88.5|90.60|91.40|95.60|96.30|
|PIQA <br> 5-Shot |83.60|87.80|87.70|60.2|77.70|78.10|86.00|86.60|
|SociQA <br> 5-Shot |76.10|79.00|80.20|68.3|74.60|65.50|75.90|68.30|
|BigBench-Hard <br> 0-Shot |71.50|74.90|81.30|59.4|57.30|59.60|69.70|68.30|
|WinoGrande <br> 5-Shot |72.50|82.50|81.40|54.7|54.20|55.60|62.00|68.80|
|OpenBookQA <br> 10-Shot |80.60|88.40|87.20|73.6|79.80|78.60|85.80|86.00|
|BoolQ <br> 0-Shot |78.70|82.90|86.60| -- |72.20|66.00|76.60|79.10|
|CommonSenseQA <br> 10-Shot |78.00|80.30|82.60|69.3|72.60|76.20|78.10|79.60|
|TruthfulQA <br> 10-Shot |63.20|68.70|75.70| -- |53.00|52.10|60.10|67.70|
|HumanEval <br> 0-Shot |57.90|59.10|55.50|59|28.00|34.10|37.80|62.20|
|MBPP <br> 3-Shot |62.50|71.40|74.50|60.6|50.80|51.50|60.20|77.80|

## Inference samples

Inference type|Python sample (Notebook)|CLI with YAML
|--|--|--|
Real time|<a href="https://aka.ms/azureml-infer-online-sdk-text-generation" target="_blank">text-generation-online-endpoint.ipynb</a>|<a href="https://aka.ms/azureml-infer-online-cli-text-generation" target="_blank">text-generation-online-endpoint.sh</a>

## Finetuning samples
Task|Dataset|Python sample (Notebook)
|--|--|--|
Chat completion|<a href="https://huggingface.co/datasets/HuggingFaceH4/ultrachat_200k" target="_blank">Ultrachat 200K</a>|<a href="https://aka.ms/phi3ftnotebook" target="_blank">chat-completion.ipynb</a>

## Sample inputs and outputs (for real-time inference)

### **Sample input**
```json
{
  "input_data": {
    "input_string": [
      {
        "role": "user",
        "content": "I am going to Paris, give me a list of 10 places to visit"
      }
    ],
    "parameters": {
      "temperature": 0.7,
      "top_p": 0.9,
      "do_sample": true,
      "max_new_tokens": 1000
    }
  }
}
``` 
### **Sample output**
```json
{
  "output": " 1. Eiffel Tower: Visit the iconic symbol of Paris, offering breathtaking views of the city.\n\n2. Louvre Museum: Explore one of the world's largest and most visited museums, home to thousands of works of art, including the Mona Lisa.\n\n3. Notre-Dame Cathedral: Marvel at the stunning Gothic architecture of this famous cathedral, although note that it is currently under renovation due to the 2019 fire.\n\n4. Montmartre: Discover this historic and artistic neighborhood, famous for its bohemian past and the stunning Sacré-Cœur Basilica.\n\n5. Seine River Cruise: Take a relaxing cruise on the Seine River, seeing some of the city's most famous landmarks like the Louvre, Notre-Dame, and the Eiffel Tower from a unique perspective.\n\n6. Champs-Élysées: Visit this famous avenue lined with shops, cafes, and theaters. Don't forget to check out the Arc de Triomphe at its end.\n\n7. Palace of Versailles: Take a day trip from Paris to explore the opulent palace and gardens of Versailles, a UNESCO World Heritage site.\n\n8. Sacré-Cœur Basilica: Located at the highest point in the city, this basilica offers panoramic views of Paris.\n\n9. Latin Quarter: Stroll through this historic and vibrant neighborhood, famous for its student life, lively atmosphere, and cafes.\n\n10. Musée d'Orsay: Visit this museum, housing an impressive collection of Impressionist and Post-Impressionist art, including works by Monet, Degas, Renoir, and Van Gogh."
}
```

## Hardware Requirements
Note that by default, the Phi-3-mini model uses flash attention, which requires certain types of GPU hardware to run. We have tested on the following GPU types:
* NVIDIA A100
* NVIDIA A6000
* NVIDIA H100

If you want to run the model on:
* NVIDIA V100 or earlier generation GPUs: call AutoModelForCausalLM.from_pretrained() with attn_implementation="eager"
* CPU: use the **GGUF** quantized models [4K](https://aka.ms/Phi3-mini-4k-instruct-gguf)
+ Optimized inference on GPU, CPU, and Mobile: use the **ONNX** models [4K](https://aka.ms/Phi3-mini-4k-instruct-onnx)


## Cross Platform Support

ONNX runtime ecosystem now supports Phi-3 Mini models across platforms and hardware. You can find the optimized ONNX models [here](https://aka.ms/Phi3-ONNX-HF).

Optimized Phi-3 models are also published here in ONNX format, to run with ONNX Runtime on CPU and GPU across devices, including server platforms, Windows, Linux and Mac desktops, and mobile CPUs, with the precision best suited to each of these targets. DirectML support lets developers bring hardware acceleration to Windows devices at scale across AMD, Intel, and NVIDIA GPUs.  
Along with DirectML, ONNX Runtime provides cross platform support for Phi-3 across a range of devices CPU, GPU, and mobile.

Here are some of the optimized configurations we have added: 

1. ONNX models for int4 DML: Quantized to int4 via AWQ
2. ONNX model for fp16 CUDA
3. ONNX model for int4 CUDA: Quantized to int4 via RTN
4. ONNX model for int4 CPU and Mobile: Quantized to int4 via RTN

## Responsible AI Considerations

Like other language models, the Phi series models can potentially behave in ways that are unfair, unreliable, or offensive. Some of the limiting behaviors to be aware of include:

+ Quality of Service: the Phi models are trained primarily on English text. Languages other than English will experience worse performance. English language varieties with less representation in the training data might experience worse performance than standard American English.   
+ Representation of Harms & Perpetuation of Stereotypes: These models can over- or under-represent groups of people, erase representation of some groups, or reinforce demeaning or negative stereotypes. Despite safety post-training, these limitations may still be present due to differing levels of representation of different groups or prevalence of examples of negative stereotypes in training data that reflect real-world patterns and societal biases. 
+ Inappropriate or Offensive Content: these models may produce other types of inappropriate or offensive content, which may make it inappropriate to deploy for sensitive contexts without additional mitigations that are specific to the use case. 
+ Information Reliability: Language models can generate nonsensical content or fabricate content that might sound reasonable but is inaccurate or outdated.  
+ Limited Scope for Code: Majority of Phi-3 training data is based in Python and use common packages such as "typing, math, random, collections, datetime, itertools". If the model generates Python scripts that utilize other packages or scripts in other languages, we strongly recommend users manually verify all API uses.   

Developers should apply responsible AI best practices and are responsible for ensuring that a specific use case complies with relevant laws and regulations (e.g. privacy, trade, etc.). Important areas for consideration include:

+ Allocation: Models may not be suitable for scenarios that could have consequential impact on legal status or the allocation of resources or life opportunities (ex: housing, employment, credit, etc.) without further assessments and additional debiasing techniques.
+ High-Risk Scenarios: Developers should assess suitability of using models in high-risk scenarios where unfair, unreliable or offensive outputs might be extremely costly or lead to harm. This includes providing advice in sensitive or expert domains where accuracy and reliability are critical (ex: legal or health advice). Additional safeguards should be implemented at the application level according to the deployment context. 
+ Misinformation: Models may produce inaccurate information. Developers should follow transparency best practices and inform end-users they are interacting with an AI system. At the application level, developers can build feedback mechanisms and pipelines to ground responses in use-case specific, contextual information, a technique known as Retrieval Augmented Generation (RAG).   
+ Generation of Harmful Content: Developers should assess outputs for their context and use available safety classifiers or custom solutions appropriate for their use case. 
+ Misuse: Other forms of misuse such as fraud, spam, or malware production may be possible, and developers should ensure that their applications do not violate applicable laws and regulations.


## License

The model is licensed under the [MIT license](https://huggingface.co/microsoft/Phi-3-mini-128k/resolve/main/LICENSE).

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft’s Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party’s policies.
