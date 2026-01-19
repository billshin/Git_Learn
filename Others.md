

**git checkout 以前什麼都做**
git checkout develop       # 換分支
git checkout -b feature    # 建分支 + 換
git checkout commit_hash   # 跳到某 commit
git checkout -- file.txt   # 還原檔案

**Git 2.23（2019）之後：拆開**
用途	指令
換分支	git switch
建立 + 換分支	git switch -c
還原檔案	git restore
checkout（保留）	給老手或舊文件