---
title: Gene Workflow Platform (Galaxy)
author: 黃馨平
date: 2020-02-26T08:08:51.114Z
tags: [gene,workflow,automotive,netflow]
---

### Gene Workflow Platform (Galaxy)
![](images/48082a569d9/1*4LLc3F2oW_CJ8kdDnx9L-Q.jpeg "")
#### 為什麼想寫這篇 ?

Galaxy 是一個基因流程平台，那他有分 [online](https://usegalaxy.org/) and offline，那為什麼想要寫本篇呢 ? 因為他跟 IGV tool 一樣複雜，另外 google 了一下，發現中文的資源超少，那就來當成筆記，順便跟大家 17 討論吧，本篇寫的是 offline 的安裝教步驟，一步步的跟大家做完 offline 的方法。


 **但本篇暫時不使用 docker 喔 ，** 而是用 virtualenv。
#### Step 0 Go to official website:

[Get Galaxy
Here you will find information on obtaining and setting up a Galaxy instance with default configuration. If setting up…galaxyproject.org](https://galaxyproject.org/admin/get-galaxy/)
#### Step 1 Download galaxy:

因為 project 超大所以需要 clone 一段時間，目前用的版本是 19.09。
```
git clone -b release\_19.09 https://github.com/galaxyproject/galaxy.git


```
####  **Step 2** set up envirment **:** 

我們需要建立一個虛擬環境，與真實環境隔離。
```
apt install virtualenv
virtualenv .venv
```

剛開始 config 的時間需又很久喔。
```
cd galaxy/
sh run.sh
```

好了以後可以輸入 [http://localhost:8080](http://localhost:8080) 就可以看我們進入到 galaxy 平台了。

#### Step 4 修改 config 檔:

因為 galaxy 需要設定的東西真的有點小多，啊我的目的就只是為了快速用平台阿，在那邊盧真的很煩，又不是要玩系統，有時候多覺得還不如自己下 command 來的快。
```
cp config/galaxy.yml.sample config/galaxy.yml


```

 **step 4-1 改成區域網路都可以連:** 
```
vim config/galaxy.yml


```

 **step 4–2 將帳戶改成最高權限:** 
```
找到 a<!-- -->dmin\_users: ''  
改成 admin\_users: 你的email@gmail.com  
我的 admin\_users: [jackycsie@gmail.com](mailto:jackycsie@gmail.com)


```

 **step 4–3 重新 run 1次:** 
```
sh run.sh
```
![](images/48082a569d9/1*yDEYBuqKS0E-9ijJ6iaKEg.jpeg "")

成功了 ，狀態列上也有 Admin 的選項。

 **step 5 下載工具 :** 

拿到了最高權限後我們來示範怎麼下載工具。

首先點 Admin > Install or Uninstall > 輸入 fastqc ，選擇你想要下載的 fastqc version 就可以囉。
![](images/48082a569d9/1*KSfvOPvkD49sZ8SKxOlsqw.png "")
![](images/48082a569d9/1*i-5Xui-KwM-Yobc2jbXwhg.jpeg "")

成功。
#### Step 6 實驗使用 Fastqc :

選擇您要的 fastq 檔案，然後按執行。
![](images/48082a569d9/1*uZ9udt4iJmiHrKdANnXt4A.jpeg "")

執行完後我們會看到怎麼全部都是亂碼，因為我們並沒有將 fastqc 加入白名單，因此來跟大家介紹怎麼加入。
![](images/48082a569d9/1*anfsQ-sxRHV4NXpolx586g.jpeg "")

首先點 Admin > Manage whitelist>尋找 FastQC ，點選後按 submit 。
![](images/48082a569d9/1*lLCeQSyljfOZw_m5mYK-wA.png "")
![](images/48082a569d9/1*aMfJ6IdhOp2Y1iK6rF4Saw.jpeg "")

圖片都成功回來了。
![](images/48082a569d9/1*Sn8d0qXK-lQJw6uoZ2ETYA.jpeg "")
#### 結束

初步的介紹大概就是這樣，還是不懂明明應該要更容易使用的 GUI，卻把它說明文件卻搞得很複雜，好險做這個人的看不懂中文，不然他們關掉這個就少了一個好用的 GUI 了。

之後還會陸續增加覺得很煩的設定，讓大家盡量專注在 gene 研究的身上比較好。



+-----------------------------------------------------------------------------------+

| **[View original post on Medium](https://medium.com/jacky-life/gene-workflow-platform-galaxy-48082a569d9) - Converted by [ZhgChgLi](https://blog.zhgchg.li)/[ZMediumToMarkdown](https://github.com/ZhgChgLi/ZMediumToMarkdown)** |

+-----------------------------------------------------------------------------------+
