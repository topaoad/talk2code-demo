# talk2code_example

Sample implementatino of Talk2Code(Talk to Sourcecode) using LangChain.

# How to use

## Requirement

Python3
[ActiveLoop Account
](https://github.com/kazuooooo/talk2code_example)
[OpenAI Account](https://openai.com/)

## Setup

```
# create venv
$ python3 -m venv .venv
# activate
$ source ./.venv/bin/activate
# install libs
(.venv) pip3 install -r requirements.txt
```

## Set environment variables to .env

```
# Token of ActiveLoop
ACTIVELOOP_TOKEN=ey...
# Account name of ActiveLoop
ACTIVELOOP_ACCOUNT_NAME=account_name
# Dataset name to store DeepLake(any value)
DATASET_NAME=your_repo_name
# Directory path of sourcecode of loacal machine
SRC_DIR=`path/to/source/dir
# API key of OpenAI
OEPN_AI_API_KEY=sk-...
```

## Prepare data

```
(.venv) $python3 prepare_data.py
```

## Talk to Code

```
(.venv) $python3 talk2code.py
You: What does GoogleCalendarClient do?
Code: `GoogleCalendarClient` is a class that extends the `CalendarClient` abstract class and provides implementation for Google Calendar specific functionalities. It is responsible for interacting with the Google Calendar API and performing various operations such as fetching calendar details, listing calendars, adding, updating, and deleting events, and managing calendar notification channels. It helps in managing and synchronizing Google Calendar data within the application.
```

## 挙動しない件
- openai.error.InvalidRequestError: This model's maximum context length is 4097 tokens. However, your messages resulted in 13077 tokens. Please reduce the length of the messages.
とのこと。テキストのチャンク化がうまくいっていないため、トークンが上限を超えている模様。

###　試したこと
以下のサイトのように、text_splitterにseparator="\n"を追加したらうまくいった
https://ict-worker.com/ai/langchain-chunk.html
### 試しに聞いてみたプロンプトの例
srcコードの中身を説明してください
ソースコード内の認証の仕組みを教えてください
Calendar.tsxの中身を教えてください
Calendar.tsx内のリファクタはできますか
先ほどの質問は覚えていますか
react-router-domは使われていますか。使われているとしたらどこのコンポーネントですか
続きを教えてください