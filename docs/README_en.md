<div align="center">

# Tomotake Yoshino Bot
*********************

_🌱 This project is based on the [go-cqhttp](https://github.com/Mrs4s/go-cqhttp) and [fnbot](https://github.com/mrhblfx/fnbot) development of QQ entertainment robot 🌱_

</div>

<div align="right">
  Language:
  <a title="Chinese" href="/README.md">🇨🇳</a>
  <a title="English" href="/docs/README_en.md">EN</a>
</div>



# Quick Start
- This project uses [go-cqhttp](https://github.com/Mrs4s/go-cqhttp) as the front end
  python3 as the backend, creating a QQ robot
- The core code is concentrated in the `fnbot` folder for easy import (`pip install fnbot`)
- Plugin code is concentrated in the `plugins` folder for easy management



# Chatgpt Analysis Report

Using chatgpt to parse this project, blame chatgpt if there are any issues.

- [CN](https://github.com/mrhblfx/yoshino-bot/blob/master/docs/chatgpt_analysis_report.md)
- [EN](https://github.com/mrhblfx/yoshino-bot/blob/master/docs/chatgpt_analysis_report_en.md)



# for Windows

## Download [go-cqhttp](https://github.com/Mrs4s/go-cqhttp)

- Pay attention to selecting `0: HTTP communication` after launching

- If using it for the first time, you can first read the [official document (click me)](https://docs.go-cqhttp.org/guide/#go-cqhttp)

- Modify the generated `config.yml`

  <details>
  <summary>Content to be modified</summary>

  ```yml
  account: # Account related
    uin: 123456789 # QQ account
    password: '' # Use scanning code login when the password is empty
  ```
  and
  ```yml
  # Connection service list
  servers:
    # Adding methods, the same connection method can add multiple, please refer to the documentation for specific configuration instructions
    #- http: # http communication
    #- ws:   # Positive Websocket
    #- ws-reverse: # Reverse Websocket
    #- pprof: #Performance analysis server

    - http: # HTTP communication settings
        address: 127.0.0.1:9900 # HTTP listening address
        timeout: 5      # Reverse HTTP timeout, in seconds, <5 will be ignored
        long-polling:   # Long polling extension
          enabled: false       # Whether to turn on
          max-queue-size: 2000 # Message queue size, 0 means unlimited queue size, use with caution
        middlewares:
          <<: *default # Reference the default middleware
        post:           # Reverse HTTP POST address list
        #- url: ''                # Address
        #  secret: ''             # Key
        #  max-retries: 3         # Maximum retries, disabled when 0
        #  retries-interval: 1500 # Retry time, in milliseconds, 0 means immediate
          - url: http://127.0.0.1:9901/ # Address
            secret: ''                  # Key
            max-retries: 10             # Maximum retries, disabled when 0
            retries-interval: 1000      # Retry time, in milliseconds, 0 means immediate
  ```

  </details>

## Download and configure the python code

```powershell
cd qqbot
```

```powershell
git clone https://github.com/mrhblfx/yoshino-bot
```

```powershell
cd yoshino-bot
python -m pip install -r requirements.txt
```

- Temporary source replacement
```powershell
python -m pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/
```

- Modify `pybot.toml`
  <details>
  <summary>Content to be modified</summary>

  ```toml
  host = "127.0.0.1"
  port = 9900 # Corresponding to the address: 127.0.0.1:9900 in gocq's config.yml
  post = 9901 # Corresponding to gocq's config.yml: - url: http://127.0.0.1:9901/
  bot_qq = 123456789 # qq account
  group_list = [123456,1234567] # QQ group number to be added
  ```

  </details>

## Finally run `main.py`

```powershell
python main.py
```

---

# Suggestions

- Create a new configuration file `config.toml` or `config.json` to replace `pybot.toml` or `pybot.json`

- Create a `bot.py` file to replace `main.py`

---

# for Linux

## Pre-install `python3 and git` (`can be skipped`)

```bash
apt install python3
apt install git
```

---

## Download `gocq`
- There are two ways, manual and command-line download. Here, the command method is selected
- Here we take `arm` architecture as an example

```bash
mkdir qqbot
cd qqbot
mkdir gocq
cd gocq
wget https://github.com/Mrs4s/go-cqhttp/releases/download/v1.0.0-rc5/go-cqhttp_linux_arm64.tar.gz
tar -xvf go-cqhttp_linux_arm64.tar.gz
./go-cqhttp
```

- Choose `0: HTTP communication`

- The modified configuration information is the same as the configuration on windows.

## 翻译 private_upload/2023-05-30-14-15-12\README.md.part-1.md

You can also use other editors, here we take "vim" as an example.

Execute the command "vim config.yml", it will enter a new interface.

Press the "i" key to enter edit mode and press the "esc" key to exit edit mode.

Use "h" to move the cursor to the left, "j" to move the cursor down, "k" to move the cursor up, and "l" to move the cursor to the right.

If you need to exit and save, press "esc", then enter ":", "w", "q" in order, and press "enter".

If you cannot save and exit with ":wq", use ":wq!" to force exit and save.

```bash
vim config.yml
./go-cqhtttp
```

## Note: if using "termux", the latest version of gocq may have some small problems

- "termux-chroot" can be used to avoid this bug.

```bash
termux-chroot
./go-cqhttp
```

## Download and configure Python code

- The modified configuration information is the same as the one configured on Windows above.

```bash
cd qqbot
```

```bash
git clone https://github.com/mrhblfx/yoshino-bot yoshino-bot
```

```bash
cd yoshino-bot
python -m pip install -r requirements.txt
```

"Temporarily change the source"
```bash
python -m pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/
```

```bash
vim pybot.toml
```

```bash
python3 main.py
```

---

# unfinished to be continued

# ......

# TODO

- []
- [×] ......
- [√] ......

