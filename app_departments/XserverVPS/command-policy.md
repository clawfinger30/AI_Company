# XserverVPS 許可コマンド・禁止コマンド方針

作成日: 2026-07-02

## 1. 基本方針

VPS運用AIは、読み取り調査を優先し、状態変更を伴うコマンドは承認後に実行する。

コマンド実行前に、対象パス、対象サービス、実行目的、想定影響、ロールバック可否を確認する。

## 2. 原則として承認不要な読み取りコマンド

対象環境や対象ディレクトリを確認する目的で、以下は原則として実行できる。

```text
pwd
whoami
hostname
date
ls
find
rg
cat
sed -n
tail
head
git status
git branch
git log --oneline -n 20
git diff --stat
docker ps
docker compose ps
docker compose logs --tail 200
systemctl status
journalctl -n 200
df -h
free -h
uptime
nginx -t
```

ただし、秘密情報を含む可能性があるファイルに対して `cat`、`sed`、`tail` を使う場合は、値を表示せず、項目名や存在確認に留める。

## 3. 承認後に実行できる変更コマンド

以下は、実行前にユーザー承認、影響範囲、ロールバック方法、検証方法を確認する。

```text
git pull
git switch
git checkout
git merge
git revert
docker compose pull
docker compose build
docker compose up -d
docker compose down
docker compose restart
systemctl restart
systemctl reload
nginx -s reload
cp
mv
chmod
chown
ln -s
npm install
npm run build
composer install
php artisan migrate
certbot renew
crontab -e
```

## 4. 原則禁止コマンド

以下は、通常作業では実行しない。緊急復旧などで必要な場合も、ユーザーの明示指示、対象範囲、バックアップ、ロールバック方法が必要です。

```text
rm -rf /
rm -rf /*
rm -rf ./*
rm -rf /var
rm -rf /home
mkfs
dd
shred
wipefs
fdisk
parted
docker system prune -a
docker volume rm
docker compose down -v
git reset --hard
git clean -fdx
chmod -R 777
chown -R
ufw reset
ufw deny
iptables -F
DROP DATABASE
TRUNCATE
DELETE FROM
```

## 5. 秘密情報に関する禁止

以下は実行または出力しない。

- 秘密鍵の内容表示
- `.env` の値の全文表示
- DBパスワード、APIキー、トークン、Cookieの表示
- 証明書秘密鍵の表示
- SSH設定の秘密値の転記

必要な場合は、ファイルの存在、キー名、更新日時、権限だけを確認する。

## 6. コマンド提案時の形式

変更コマンドを提案する場合は、次をセットで提示する。

```text
目的:
対象:
実行予定コマンド:
想定影響:
事前バックアップ:
検証方法:
ロールバック:
承認要否:
```

