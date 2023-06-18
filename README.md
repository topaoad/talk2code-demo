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

## 進捗

- openai.error.InvalidRequestError: This model's maximum context length is 4097 tokens. However, your messages resulted in 13077 tokens. Please reduce the length of the messages.
  - 4096 トークンまでしか入力できないとのことで、これらについては解決方法を模索中（6/18）
- gpt-3.5-turbo は稼働するが、gpt ー４は読んでくれない（ウェイティングリスト待ちが必要？）
  → 次のイシューと同じ？と思ってやり始めたが、現在のところうまくいってない。
  https://github.com/hwchase17/langchain/issues/3328

### 試しに聞きたいプロンプトの例

src コードの中身を説明してください
