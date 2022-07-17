# Docker MongoDB

## DBへの接続まで

<details>
<summary>docker run</summary>

``` PowerShell
docker run -d --name mongo-db -p 27017:27017 mongo:latest
```

</details>

<details>
<summary>docker exec</summary>

``` PowerShell
docker exec -it <CONTAINER ID> mongo bash
MongoDB shell version v5.0.9
connecting to: mongodb://127.0.0.1:27017/bash?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("9ae106a0-e9da-447d-971c-0e6e2588864e") }
MongoDB server version: 5.0.9
================
Warning: the "mongo" shell has been superseded by "mongosh",
which delivers improved usability and compatibility.The "mongo" shell has been deprecated and will be removed in
an upcoming release.
For installation instructions, see
https://docs.mongodb.com/mongodb-shell/install/
================
---
The server generated these startup warnings when booting: 
        2022-06-06T00:29:07.028+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
        2022-06-06T00:29:07.640+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
        2022-06-06T00:29:07.640+00:00: /sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never'
---
---
        Enable MongoDB's free cloud-based monitoring service, which will then receive and display
        metrics about your deployment (disk utilization, CPU, operation statistics, etc).

        The monitoring data will be available on a MongoDB website with a unique URL accessible to you
        and anyone you share the URL with. MongoDB may use this information to make product
        improvements and to suggest MongoDB products and deployment options to you.

        To enable free monitoring, run the following command: db.enableFreeMonitoring()
        To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
---
>
```

</details>

## 基本的な使い方

<details>
<summary>show dbs</summary>

``` MongoDB
> show dbs
admin     0.000GB
config    0.000GB
local     0.000GB
scraping  0.000GB
test      0.000GB
```

</details>

<details>
<summary>use some-db</summary>

``` MongoDB
> use scraping
switched to db scraping
```

</details>

<details>
<summary>show collections</summary>

``` MongoDB
> show collections
books
ebooks
```

</details>


<details>
<summary>db.collection-name.find()</summary>

``` MongoDB
> db.books.find();
{ "_id" : ObjectId("629d9bc2147a03de0da1569a"), "url" : "https://gihyo.jp/dp/ebook/2022/978-4-297-12847-0", "title" : "達人が教えるWebパフォーマンスチューニング〜ISUCONから学ぶ高速化の実践" }
{ "_id" : ObjectId("629d9bc2147a03de0da1569b"), "url" : "https://gihyo.jp/dp/ebook/2022/978-4-297-12849-4", "title" : "今すぐ使えるかんたんEx 今すぐ使えるかんたんExMicrosoft Teams プロ技BESTセレクション" }
{ "_id" : ObjectId("629d9bc2147a03de0da1569c"), "url" : "https://gihyo.jp/dp/ebook/2022/978-4-297-12843-2", "title" : "ゼロからはじめる ゼロからはじめるFacebook フェイスブック 基本＆便利技" }
```

</details>

<details>
<summary>db.collection-name.insert_one</summary>

``` MongoDB
db.inventory.insert_one(
    {
        "item": "canvas",
        "qty": 100,
        "tags": ["cotton"],
        "size": {"h": 28, "w": 35.5, "uom": "cm"},
    }
)
```

</details>

<details>
<summary>db.collection-name.insert_many</summary>

``` MongoDB
db.inventory.insert_many(
    [
        {
            "item": "journal",
            "qty": 25,
            "tags": ["blank", "red"],
            "size": {"h": 14, "w": 21, "uom": "cm"},
        },
        {
            "item": "mat",
            "qty": 85,
            "tags": ["gray"],
            "size": {"h": 27.9, "w": 35.5, "uom": "cm"},
        },
        {
            "item": "mousepad",
            "qty": 25,
            "tags": ["gel", "blue"],
            "size": {"h": 19, "w": 22.85, "uom": "cm"},
        },
    ]
)
```

</details>
