# Laravel 8 隧道服務

引入 beyondcode 的 expose 套件來擴增把本地主機（localhost）對應到 HTTPS 公開網域的服務，讓本機電腦的測試環境直接對外提供連線，以便進行測試與偵錯。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __Artisan__ 指令的 __migrate__ 來執行所有未完成的遷移。
```sh
$ php artisan migrate
```
- 執行安裝 Laravel Mix 引用的依賴項目，並執行所有 Mix 任務。
```sh
$ npm install && npm run dev
```
- 執行 __Expose__ 指令的 __token__ 來使用授權金鑰連結 expose 伺服器。
```sh
$ expose token [你的授權金鑰]
```
- 執行 __Expose__ 指令的 __token__ 使用最近的可用 expose 伺服器。
```sh
$ expose default-server [expose 伺服器名稱]
```
- 執行 __Expose__ 指令的 __share__ 來使用隨機產生的 expose 子網域共享對路由 URL 的存取
```sh
$ expose share [路由 URL] --subdomain=
```
- 在瀏覽器中輸入產生的 expose 子網域 URL 來訪問，例如：https://6hfvk21jmw.ap-1.sharedwithexpose.com。

----

## 畫面截圖
![](https://i.imgur.com/f9rBxNt.png)
> 共享路由 URL 存取

![](https://i.imgur.com/aElfBsW.png)
> 在瀏覽器中輸入產生的 expose 子網域 URL 一下就能連上本機電腦，非常的實用