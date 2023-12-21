# Startup

- clone the llama repo
- run '''pip install -e .'''
- run the download script

the folder structure should look like this:
```
llama
├── llama-2-7b-chat
├── llama
│   ├── __init__.py
│   ├── generation.py
│   ├── model.py
│   ├── tokenizer.py
├── example_chat_completion.py
├── ...
llama.cpp
├── ci
├── cmake
├── common
├── ...
```

## Metal
- clone the llama-cpp repo
- cd into the llama-cpp repo
- switch to the commit 0353a1840134b24b07ab61fd4490192f28c4db6b since at the time of writing this is the last commit that does not break in the conversion process
- set '''LLAMA_METAL=1 make'''
- run '''pip install -r requirements.txt'''
- run '''python convert.py ../llama/llama-2-7b-chat --outputtype q8_0`` for quantization otherwhise run '''python convert.py ../llama/llama-2-7b-chat''' -> gpu memory will run out
- activate the llama conda env
- run ```CMAKE_ARGS="-DLLAMA_METAL=on" FORCE_CMAKE=1 pip install llama-cpp-python```
``


https://github.com/ggerganov/llama.cpp
https://github.com/ggerganov/llama.cpp/issues/4493
git checkout 0353a1840134b24b07ab61fd4490192f28c4db6b