+++
title = "Windows WSLでのPython環境構築メモ 1"
author = ["u-yuta"]
date = 2024-04-14T16:29:00+09:00
tags = ["python"]
draft = false
ShowToc = true
+++

WSL上でのPython環境構築に関するメモ。ここでは方針のみ。具体的な手順は後ほど追加する。


## 前提 {#前提}

Pythonの用途は、データ解析と統計処理・可視化、物理・工学の計算機シミュレーション、数式処理など。

主な使用パッケージはNumpy, Scipy, Pandas, Matplotlib, Holoviz (hvPlot, Panel), etc.


## 方針： ベース環境 {#方針-ベース環境}

システムのPython（OSが使用するPython）とは別に、「ベース環境」として普段使い用のPython環境をインストールする。

必要に応じてバージョンが切り替えられるように、ベース環境は [asdf](https://asdf-vm.com) を用いてインストールする。後述する仮想環境を有効にしていない限りは、シェルの `python` コマンドでベース環境のPythonが実行される。


## 方針: 仮想環境 {#方針-仮想環境}

Python本体や使用ライブラリのバージョン違いによる不具合を避けて再現性を保つため、プロジェクトごとに実行環境（仮想環境）を作って管理する。

VSCodeで自動的に認識されるように、仮想環境はプロジェクトのrootディレクトリの `.venv/` にインストールする。

[Windows WSLでのPython環境構築メモ 2]({{< relref "python-on-wsl-environment-setup-memo-2" >}}) へ続く。
