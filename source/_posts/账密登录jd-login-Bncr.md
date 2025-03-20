---

title: 账密登录jd-login-Bncr

date: 2024-10-08 22:05:54

tags:  "Bncr"

---

---

<!-- more -->



### 1. docker run命令（新手推荐）直接复制到ssh执行

```
docker run -d \
    --name jd_autologin \
    --restart unless-stopped \
    -p 12345:12345 \
    -e TZ=Asia/Shanghai \
    -v /your/host/app/directory:/app \
    python:3.12.4 \
    sh -c "apt -y update && apt -y install libnss3 libnspr4 libatk1.0-0 libatk-bridge2.0-0 libcups2 libdrm2 libdbus-1-3 libxkbcommon0 libxcomposite1 libxdamage1 libxfixes3 libxrandr2 libgbm1 libasound2 libatspi2.0-0 libxshmfence1 && python -m pip install --upgrade pip && pip install pyppeteer Pillow asyncio aiohttp opencv-python-headless ddddocr quart && rm -rf && wget -O api.py https://raw.githubusercontent.com/zhao-zg/jd-login/main/api.py && wget -O login.py https://raw.githubusercontent.com/zhao-zg/jd-login/main/login.py && python api.py"

```



## 2. docker-compose方式安装

创建docker-compose.yml文件，把下面代码放进去



```
version: "3"
services:
  jd_autologin:
    image: python:3.12.4
    container_name: jd_autologin
    restart: unless-stopped
    ports:
      - 12345:12345
    working_dir: /app
    environment:
      TZ: Asia/Shanghai
    command: >
      sh -c "apt -y update && apt -y install libnss3 libnspr4 libatk1.0-0
      libatk-bridge2.0-0 libcups2 libdrm2 libdbus-1-3 libxkbcommon0
      libxcomposite1 libxdamage1 libxfixes3 libxrandr2 libgbm1 libasound2
      libatspi2.0-0 libxshmfence1 && python -m pip install --upgrade pip && pip
      install pyppeteer Pillow asyncio aiohttp opencv-python-headless ddddocr
      quart && rm -rf && wget -O api.py
      https://raw.githubusercontent.com/zhao-zg/jd-login/main/api.py
      && wget -O login.py
      https://raw.githubusercontent.com/zhao-zg/jd-login/main/login.py
      && python api.py"
networks: {}


```





- **启动服务（后台模式）**：

  ```
  docker-compose up -d    #使用 `-d` 参数表示后台运行，省略 `-d` 参数则会在前台显示容器日志。
  ```

  接着去无界后台 插件配置 登录.js 密码登录服务地址：填入你服务器的地址加上12345端口 重启无界即可
 ![](https://blog.106996.xyz/HEXO/bncr-auto-login/Snipaste_2024-10-27_11-10-52.png)