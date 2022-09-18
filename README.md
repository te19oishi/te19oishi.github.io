# te19oishi.github.io
issueの作成手順
GitHub上の該当プロジェクトのタブからIssuesを選択する
New issueを選択
issueのタイトルと内容を記入してSubmit new issueを押す（issueが追加される）
コメントでチェックボックス等を付けることが出来るので子タスクの管理としても便利
issueを用いた開発手順
登録されているissueに合わせて新たにブランチを切って開発を始める

git branch 新規ブランチ名_#issue番号としてissue番号を付けておくと今後見やすくて便利
git checkout 新規ブランチ名で作業ブランチに移動することを忘れない
ブランチの移動まで一括で行いたい場合は、git checkout -b 新規ブランチ名_#issue番号として実行する。-bオプションは「ブランチの作成（branchのb）」のこと。

キリの良いところで適宜コミットする（git commit -m "コミットメッセージ #issue番号"）

コミットする時必ず対応するissue番号を半角スペースを空けて付け加えること！（こうすることで、そのIssueに関するコミットだということを紐付けることが出来る）

作業が完了したら適宜git pushする（全て終わってからじゃなくてもOK）

この時作業ブランチ宛にpushすることに注意！（git push origin 作業ブランチ名 または、 git push origin HEAD）

作業が全て完了したらプルリクを作成し、リモートのmainブランチにmergeする

プルリクの際、コメント欄にclose #issue番号と書くと、mergeされる際に自動的にそのissueがcloseになるので便利
プルリクの流れは以下の通り
Compare & pull requestボタンを押す
Write欄にコメントを書く（変更点の記入 & close #issue番号の記入）
Create pull requestボタンを押す
File changedで変更差分を確認（コメントがあればコメント）
この時、修正箇所がある場合はコメント等で指摘が入る（先輩等から）
指摘を踏まえての修正作業がある場合はMerge pull requestの前に以下の流れを取って修正作業をする
作業ブランチで修正作業をする
git add → git commitする
git push origin 同作業ブランチ名でpushする
上記のようにすることで、同ブランチ宛てにpushを行っていれば、自動的に最新のコミット履歴がプルリクにも積み重なるようになっている
この作業をプルリクがOKとなるまで繰り返す
Conversationタブ内のMerge pull requestボタンを押す（この前までなら修正が効く）
Confirm mergeボタンを押す
Delete branchボタンを押してリモートの作業ブランチを削除する

ローカルのmainブランチをリモートブランチと同じ状態にする（git pull origin main）

git checkout mainでmainブランチに移動する
git pull（git pull origin main）する（チーム開発においては「git fetch + git merge」の方が無難かも）
git pullしたあとはローカルでmerge commitが作成されるので、ここで一度git pushしてリモートのmainブランチを更新しておいたほうがいいかも。（因みに、このmerge commitの作成を回避するためには、git pull --rebaseコマンドを使うといいとかなんとか）

ローカルにある作業ブランチを削除する（git branch -d 作業ブランチ名）

完了！以下また①〜⑥の繰り返し

