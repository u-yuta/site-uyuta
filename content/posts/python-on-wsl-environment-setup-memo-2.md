+++
title = "Windows WSLでのPython環境構築メモ 2"
author = ["u-yuta"]
date = 2024-04-15T22:41:00+09:00
draft = false
ShowToc = true
+++

[Windows WSLでのPython環境構築メモ 1]({{< relref "python-on-wsl-environment-setup-memo-1" >}}) 続き


## 方針： Jupyter での仮想環境の利用 {#方針-jupyter-での仮想環境の利用}

Jupyterは基本的にベース環境にのみインストールする。

仮想環境ごとにJupyterをインストールすると次のような問題が出るため。

-   仮想環境ごとにJupyter, JupyterLab, ... をインストールする必要があり、手間とディスク容量がかかる。
-   プロジェクトを切り替えるたびにJupyterLabを起動し直したり、JupyterLab上でのルートフォルダの場所が変わるのでファイルを開き直したりする必要がある。

プロジェクトごとの仮想環境のカーネルをJupyterに登録し（ipykernel）
JupyterLabの起動ディレクトリを常に同じ場所に保つことで、上記の問題が避けられる。


### 例外 {#例外}

JupyterにPythonカーネルを登録しても、Pythonの管理外のプログラムへのパスが通らない。そのためcondaで仮想環境を作った場合で仮想環境にPython以外のプログラムが含まれる場合は、上記の方法だとJupyter上でのプログラムの動作に支障が出る。

そのような場合はcondaの仮想環境にJupyterをインストールして使う。


## ipynbファイルのバージョン（Git）管理 {#ipynbファイルのバージョン-git-管理}

Jupytextでpy-script化したものをGit管理する。ipynbファイル自体をGit管理すると実行状態によって差分が出て管理がしづらいため。
