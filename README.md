# myimage-for-jupyterlab
自分が研究などでJupyter Lab環境を作るときによく使うDockerイメージを，DockerHubに上げるためのリポジトリ

## 使い方

### pullして使う

1. DockerHubから次のイメージをpullしてくる

```
$ docker pull epaniuqs/myimage-for-jupyterlab
```

2. 次のファイルを引っ張ってくる
    - `docker-compose.yml`
    - `.bashrc`（任意）
    - `.gitignore`（任意）

3. docker-compose.ymlを次のように修正

```yml
...
    # For build image
    # build: .      # コメントアウトする
    # image: myimage-for-jupyterlab     # コメントアウトする

    # For pull image
    image: epaniuqs/myimage-for-jupyterlab  # コメント解除する
...
```

4. Docker環境を立ち上げる
```
$ docker-compose up
```

### `FROM`で使う

1. Dockerfileに次の内容をコピペ
```Dockerfile
# Base image
FROM epaniuqs/myimage-for-jupyterlab

# Environment
COPY requirements.txt $HOME/

# Install Python libraries
RUN pip install --upgrade pip \
  && pip install -r $HOME/requirements.txt

```

2. requirements.txtを作る

3. 次のファイルを引っ張ってくる
    - `docker-compose.yml`
    - `.bashrc`（任意）
    - `.gitignore`（任意）

4. docker-compose.ymlを次のように修正

```yml
...
    # For build image
    build: .      # コメントアウト解除
    image: myimage-for-jupyterlab     # コメント解除する（イメージ名は用途に合わせて変更すること）

    # For pull image
    # image: epaniuqs/myimage-for-jupyterlab  # コメントアウトする
...
```

5. buildして環境を立ち上げる
```
$ docker-compose up -d --build
```


## 構成

### 追加した環境変数
- `$HOME`: `/home`

### ワークディレクトリ
- `$HOME`

### コピーしたファイル

`$HOME/`へコピーしたもの：
- `.bashrc`
- `requirements-base.txt`

### インストールしたコマンド
- git
- vim

### インストールしたPythonライブラリ
- jupyterlab
- numpy
- pandas
- tqdm

### インストールしたJupyter Lab拡張機能
- jupyterlab_widgets
- lckr-jupyterlab-variableinspector
- ipywidgets

## 更新履歴

v1.0 - 2021/05/09
