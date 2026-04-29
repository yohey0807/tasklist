■環境構築
・JAVA 17：OK
・Maven：OK
・PostgreSQL：OK
・pgAdmin：OK
・VSCode：OK

■Spring Initializr
https://start.spring.io/

【設定】
・Project：Maven
・Language:Java
・SpringBoot：4.06(デフォルト)
・Group:jp.gihyo.projava
・Artifact:tasklist
・Name:TaskList
・Description:SpringBootを使ったタスク管理アプリケーション
・Package name:jp.gihyo.projava.tasklist
・Packaging:Jar
・Configuration:Properties
・Java:17
＜Dependencies＞
・Spring Web

■git
【config設定確認】git config --list or cat ~/.gitconfig
user.name=YouheiOzaki
user.email=ozayou1979test@gmail.com
init.defaultbranch=main
core.autocrlf=input
core.editor=code --wait
i18n.commitencoding=utf-8
i18n.logoutputencoding=utf-8
push.default=simple
alias.lg=log --oneline --graph --decorate --all

【操作】
git init
git add .
git commit -m "initial commit"

git status
git lg or git log

【マージ操作】
git merge

■github
【github情報】
https://github.com/
ozayou1979test@gmail.com
USERNAME:yohey0807
PASSWORD:ozaoza1979test

【設定】
new repository選択
Repository name:tasklist
※他設定デフォルト

【SSH設定】
ssh-keygen -t ed25519 -C "ozayou1979test@gmail.com"
cat ~/.ssh/id_ed25519.pub
----
Settings
SSH and GPG keys
New SSH key
貼り付け

＜接続確認＞
ssh -T git@github.com

【操作】
git remote add origin git@github.com:yohey0807/tasklist.git
＜確認＞
git remote -v
origin	git@github.com:yohey0807/tasklist.git (fetch)
origin	git@github.com:yohey0807/tasklist.git (push)
＜push操作＞
git push -u origin main

■実行
./mvnw spring-boot:run
http://localhost:8080/resthello
http://localhost:8080/hello
http://localhost:8080/list

■パッケージ作成→実行
mvn clean package
java -jar target/tasklist-0.0.1-SNAPSHOT.jar 

■タスク登録
http://localhost:8080/restadd?task=要件定義&deadline=2026-04-30
http://localhost:8080/restadd?task=構造設計&deadline=2026-05-15
http://localhost:8080/restadd?task=詳細設計&deadline=2026-05-31

http://localhost:8080/restlist

■DB連携
＜インストール＞
sudo apt update
sudo apt install -y postgresql
sudo systemctl status postgresql
＜ログイン＞
sudo -u postgres psql
＜パスワード＞
admin

＜データベース作成＞
CREATE DATABASE tasklist;
psql -h localhost -p 5432 -U postgres -d tasklist

＜テーブル作成＞
CREATE TABLE IF NOT EXISTS tasklist (
    id VARCHAR(8) PRIMARY KEY,
    task VARCHAR(256),
    deadline VARCHAR(10),
    done BOOLEAN
);

＜テーブル一覧＞
\dt








