# Linux command cheat sheet

## File
* grep -rn "test" ./clientDir/
* grep -rn "todo" ./dir/*.c
* grep -rn "test" ./clientDir/*	# ignore .xxx
* find ~/ -name "*.cpp" -ls
* find ~/* -name "*.cpp" -ls	# ignore direcotry start with .
* chmod +x fileName

## Archive
* extract
```
tar zxvf aaa.tgz
tar zxvf aaa.tar.gz
unzip aaa.zip
unrar x aaa.rar
```

* compress
```
tar zcvf aaa.tar.gz fileName
rar a aaa.rar fileName
zip -r aaa.zip fileName
```

## File Transfer
* scp pi@192.168.0.144:~/serverFile.txt .
* scp -r pi@192.168.0.144:~/serverDir .
* scp clientFile.txt pi@192.168.0.144:~/.
* scp -r clientDir/ pi@192.168.0.144:~/.
* sftp pi@192.168.0.144
	* get serverFile.txt
	* get -r serverDir/
	* put serverFile.txt
	* unable to upload directory

# Network
* curl -X POST -d '{ "param1":"val1", "param2":"val2"}' http://192.168.0.104:80/aaa.php

## System
* ps -ef | grep appName
* sudo kill 1234
* sudo shutdown -h now
* sudo reboot
* Ctrl + Alt + F1-7F7 to change terminal



## git
### いつも
* 戻す
* 今のlogの先頭、先頭の1つ前
```
git reset --hard HEAD
git reset --hard HEAD^
```
* 全logの先頭
```
git reset --hard ORIG_HEAD
```
* タグ
```
git tag v1.0 (id)
git tag -d v1.0
```
* チェック
```
git log --graph --oneline --decorate=full
git log --oneline
git log -p
git log --stat
git status
```

### Unstaged
* To stage
```
git add .
```
* 戻す
```
git checkout -- filename
```

* チェック
```
git diff
git difftool
```

### Staged
* To commit
```
git commit -m ""
```
* チェック
```
git diff --cached
```

### ブランチ
* 作成と移動
```
git branch name
git checkout name
git checkout -b name
```
* 削除
```
git branch -d name
```

*マージ
	* マージ先ブランチに移動
	* git merge name
	* コンフリクトが起きてたら、コンフリクトファイルをテキストエディタで編集
	* git add ,   git commit

### 共有リポジトリ
* 共有リポジトリ作成
	* mkdir out.git; cd out.git
	* git init --bare

* リポジトリ登録
	* ローカル作業ディレクトリで
	* git remote add origin ../out.git
	* git remote rm origin

* 共有リポジトリへコピー、更新
	* ローカル作業ディレクトリで
	* git push origin master

* 共有リポジトリから全取得
	* git clone our.git name_local
	* ディレクトリ作成、共有リポジトリ登録は不要

* 共有リポジトリから更新
	* git pull origin master
