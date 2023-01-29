# Javascript開発環境構築 
MacOSでshellはzshを使用することを想定している。

## nodebrewのinstall
nodebrewをinstallする。
```
brew install nodebrew
```

下記コマンドで、nodebrewがinstallされているかを確認する。
```
nodebrew -v
```

stableのinstallを行う。
```
nodebrew install-binary stable
```

特定のversionを有効化する。
```
nodebrew use x.x.x
```

PATHを通す。
```
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
```

versionの確認を行う。
```
node -v
```