# Python開発環境構築
下記は、複数存在するPythonの開発環境の設定方法の一例である。  
Dockerを使用しない場合の設定方法を記載する。  
MacOSでshellはzshを使用することを想定している。

## pyenvをinstallする
※ [pyenv 公式ドキュメント](https://github.com/pyenv/pyenv#installation) 

pyenvを用いてPythonのVersion管理を行うことを目的とする。  
pyenvをinstallする。  
```
brew update
brew install pyenv
```

PATHを追記し、pyenvコマンドを認識させる。  
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

pyenvコマンドが認識されているかを下記コマンドで確認する。  
```
pyenv --version
```

## Poetryをinstallする
※ [Poetry 公式ドキュメント](https://python-poetry.org/docs/)  

poetryをinstallする。  
```
curl -sSL https://install.python-poetry.org | python3 -
```  

PATHを追記し、poetryコマンドを認識させる。  
```
echo 'export PATH="/$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

poetryコマンドが認識されているかを下記コマンドで確認する。  
```
poetry --version
```

## 開発環境作成
### pyenvでPythonの特定versionをinstall
pyenvでinstall可能なPythonのversionを確認する。  
```
pyenv install --list
```

pyenvで特定のPythonのversionを作成する。  
```
pyenv install x.x.x
```  

特定のディレクトリでinstallしたPythonのversionを認識させる。  
```
pyenv local x.x.x
```

### poetryを用いて開発環境を作成

プロジェクトのrootディレクトリ内に仮想環境を作成する。  
```
poetry config virtualenvs.in-project true --local
``` 

poetryが参照するpython versionの変更を行う。
```
poetry env use x.x.x
```

既存のディレクトリが存在している場合は、初期化を行う。  
```
poetry init
```

ライブラリを追加する。  
```
poetry add xxx
``` 

開発用のライブラリ(e.g. black, mypy)を追加する。  
```
poetry add -D xxx
```

ライブラリ群をインストールする。
```
poetry install
```

`$SHELL`環境変数に従って、仮想環境の中でshellを起動する。  
```
poetry shell
``` 
