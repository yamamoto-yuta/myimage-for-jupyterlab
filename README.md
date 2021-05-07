# myimage-for-jupyterlab
自分が研究などでJupyter Lab環境を作るときによく使うDockerイメージを，DockerHubに上げるためのリポジトリ

## 使い方

DockerHubから次のイメージをpullしてくる
```
epaniuqs/myimage-for-jupyterlab
```

## 構成

### 追加した環境変数
- `$HOME`: `/home`

### ワークディレクトリ
- `$HOME`

### コピーしたファイル

`$HOME/`へコピーしたもの：
- `.bashrc`
- `requirements.txt`

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
