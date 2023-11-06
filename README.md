## 前端工程師負責部分

### 專案打包指令

1. 在終端機中輸入「 npm run build 」，會在資料夾中產出「 .next/ 」資料夾。

2. 將「 .next/ 」、「 node_modules/ 」、「 public/ 」、「 .env 」、「 next.config.js 」、「 package.json 」、「 package-lock.json 」放入伺服器中的專案資料夾。

![next.js/react.js專案資料夾](/README_image/F2E-project.JPG)

> 備註：
> <br />
> 上圖的藍色方框 「 node_modules/ 」和 「 package.json && package-lock.json 」+ npm install 兩種方式可以二擇一。

## 後端工程師負責部分

### 安裝 IIS 步驟

1.  確認電腦為 windows 專業版

2.  安裝IIS<br/>
 控制台 >> 程式集 >> 程式和功能 >> 開啟或關閉 windows 功能
![開啟IIS安裝的系統位置](/README_image/install-IIS-01.JPG)
 把以下圖片 IIS 相關功能打開<br/>
![開啟IIS安裝的系統位置](/README_image/install-IIS-02.JPG)
>備註：請注意【要求篩選】、【.NET Extensibility 4.8】、【ASP.NET4.8】要另外打開

3. 安裝 [IISnode](https://github.com/Azure/iisnode/wiki/iisnode-releases) <br/>
請選擇【iisnode for iis 7/8 (x64)】版本下載
![版本圖示](/README_image/install-IIS-03.JPG)
![安裝畫面](/README_image/install-IIS-04.JPG)
> 備註：不須更改設定，直接安裝完成即可。

4.  安裝 [url-rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) <br/>
請選擇【English: x64 installer】版本下載
![版本圖示](/README_image/install-IIS-05.JPG)
![安裝畫面](/README_image/install-IIS-06.JPG)
> 備註：不須更改設定，直接安裝完成即可。

5.  安裝[node.js](https://nodejs.org/en)
![版本圖示](./README_image/install-IIS-07.JPG)
![安裝畫面](./README_image/install-IIS-08.JPG)
> 備註：不須更改設定，直接安裝完成即可。

6. 在 C:\inetpub 中新增 專案資料夾。

7. 開啟 IIS 管理員
![開啟IIS](./README_image/install-IIS-10.JPG)

8. 應用程式集區設定<br />
新增應用程式及區 ( 在右側 ) >> 名稱設定為【iisnode】
![開啟IIS安裝的系統位置](./README_image/install-IIS-11.JPG)
【iisnode】>> 右鍵 >> 進階設定 >> 識別 ( 在最下方 ) >> 內建帳戶 >> 選擇【NetworkService】
![開啟IIS安裝的系統位置](./README_image/install-IIS-13.JPG)

9. 新增網站<br />
站台 >> 新增網站
![新增網站流程](./README_image/install-IIS-15.JPG)
輸入【站台名稱】 >> 選取【應用程式集區】為【iisnode】 >> 設定【實體路徑】空白資料夾<br/>
![開啟IIS安裝的系統位置](./README_image/install-IIS-16.JPG)
>備註：請把預設的網站停用(以避免 80port 被占用)，順便把我們新增的網站啟用

10. 處理常式對應<br />
回到設定網站介面 >> 【處理常式對應】 >> 新增模組對應 (在右側)<br>
![開啟IIS安裝的系統位置](./README_image/install-IIS-20.JPG)<br /> 
設定 要求路徑：server.js >> 模組：iiinode >> 名稱：Module1 <br/>
![開啟IIS安裝的系統位置](./README_image/install-IIS-21.JPG)

11. 設定 URL Rewrite
![開啟IIS安裝的系統位置](./README_image/install-IIS-23.JPG)<br>
新增規則 >> 空白規則
![開啟IIS安裝的系統位置](./README_image/install-IIS-24.JPG)<br>
設定 名稱：myapp >> 模式：/* >> 重寫 URL：server.js<br>
![開啟IIS安裝的系統位置](./README_image/install-IIS-25.JPG)

12. 將前端的專案內容丟進資料庫
![next.js/react.js專案資料夾](./README_image/F2E-project.JPG)

13. 最後設定 「 .next/ 」資料夾的權限 <br/>
「 .next/ 」 右鍵 >> 內容 >> 安全性 >> 編輯 >> User >> 勾選「 寫入 」 >> 套用 >> 確定
![next.js/react.js專案資料夾](./README_image/install-IIS-26.JPG)

14. 啟動站台
