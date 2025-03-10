# llm - CLI chat with LLMs

Drop-in, zero-config, free, private and anonymized AI chat with popular LLM models, straight from your terminal. Powered by DuckDuckGo's [duck.ai](https://duck.ai) service. Written as a tiny shell script in ~130 lines of plain bash.

Available models:

- **GPT-4o mini**: gpt-4o-mini
- **Claude 3 Haiku**: claude-3-haiku-20240307
- **Llama 3.3 70B**: meta-llama/Llama-3.3-70B-Instruct-Turbo
- **Mistral Small 3**: mistralai/Mistral-Small-24B-Instruct-2501
- **o3-mini**: o3-mini

https://github.com/user-attachments/assets/4e359145-0e5a-4ed8-ba8d-bf06296fcb03

## Installation

You will need to have the following dependencies installed:

- bash
- curl
- jq

Here's two ways you can install this script (click to open):

<details><summary>1. Manual installation </summary>

1. Download the script file from github.
2. Place it into an executable directory that's in your $PATH. For instance, `~/.local/bin/llm`
3. Make sure the file is executable. `chmod +x ~/path/to/llm`
4. Run `llm` to try it out!

</details>

<details><summary>2. Contributor (git) installation </summary>

Delete any other instance of the `llm` script on your machine, if you have any.

1. Clone this repo somewhere on your machine
2. Make the `llm` file executable. `chmod +x ~/path/to/llm`.
3. Create a symlink inside one of your `bin` directories on your maching, pointing to the script. Ex:

```sh
#         This directory should be in your executable PATH
#                                /
ln -s ~/path/to/repo/llm/llm ~/bin/llm
#                         \
#       This should point to the actual llm file
```

Now you can `git pull` to get updates, modify your running installation and contribute easily.

</details>

## Usage

```
$ llm -h

NAME
  llm - Chat with duck.ai LLMs

SYNOPSIS
  llm [-m model] [-t template] [prompt | - | < file]

OPTIONS
  -m <model>      Choose between one of the available models.
  -t <template>   Use a prompt template.
  -h              Show this help text
```

## Examples

```sh
llm
llm -m meta-llama/Llama-3.3-70B-Instruct-Turbo
llm "Whats 2 + 2"
echo "What's 2 + 2?" | llm
llm < question.txt
```

## Prompt templates

Add text files under the `~/.local/share/.llm/templates` directory. Here's an example:

File path `~/.local/share/.llm/templates/translate`

```
Please translate the following text between english and french:

%s
```

Then you can use it like this:

```sh
echo "Bonjour" | llm -t translate
# > Hello
```
