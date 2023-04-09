## `media`

- 依照視窗大小、螢幕尺寸、畫面解析度、裝置顯示方向等瀏覽器建置環境，套用不同的 CSS

- 可寫在以下任意位置

  - 與其他 CSS 設定放在同檔案中管理

    - `.css` 中的 `@media`

      ```css
      @media 媒體類型 and (媒體特性) {
        /* 樣式設置 */
      }
      ```

  - 將各種 CSS 敘述存於外部檔案

    - `link` 元素的 `media` 屬性

      ```html
      <link rel="stylesheet" media=:"媒體類型 and (媒體特性)" href="檔名.css">
      ```

    - `.css` 中的 `@import`

      ```css
      @import url("檔名.css") 媒體類型 and (媒體特性);
      ```

- 媒體類型 - `screen` ( 通常用這個 ) / `all` ( default ) / `print` ( 須注意有些樣式不能用 )

- 媒體特性

  - width ( 數值 ) - 顯示區域 ( 瀏覽器畫面寬度 )

    > 透過開發者工具調整切換點

    - 使用 `max-width` ( ..px 以下，為 Desktop First ) | `min-width` ( ..px 以上，為 Mobile First ) 設置

      ```css
      /* 640px 以下的環境 */
      @media screen and (max-width: 640px) {
        /* ... */
      }

      /* 641px 以上、980px 以下的環境 */
      @media screen and (min-width: 641px) and (max-width: 980px) {
        /* ... */
      }

      /* 980px 以上的環境 */
      @media screen and (min-width: 981px) {
        /* ... */
      }
      ```

  - height ( 數值 ) - 顯示區域 ( 瀏覽器畫面高度 )

    - 使用 `max-height` | `min-height` 設置

  - aspect-ratio ( 寬/高 ) - 顯示區域的長寬比

    - 使用 `max-aspect-ratio` | `min-aspect-ratio` 設置

  - resolution ( `dpi` 每英吋的點陣數 / `dpcm` 每 cm .. / `dppx` 每 px .. ) - 畫面的像素密度

    - 使用 `max-resolution` | `min-resolution` 設置

  - `orientation` ( `portrait` 縱向 / `landscape` 橫向 ) - 顯示區域方向

    ```css
    /* 直立顯示 */
    @media screen and (orientation: portrait) {
      /* ... */
    }

    /* 橫放顯示 */
    @media screen and (orientation: landscape) {
      /* ... */
    }
    ```

- 常見斷點

  - 手機 - `320px` — `480px`

  - 平板 - `481px` — `768px`

  - 筆電 & 小螢幕 - `769px` — `1024px`

  - 大螢幕 & 桌墊 - `1025px` — `1200px`

  - TV & 特大螢幕 - `1201px` 以上

## 關於行動裝置

- 加上以下 `meta` 來自動適應不同裝置調整 `viewport` 大小 ( 否則將會以原大小硬塞到裝置大小中 )

  `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`

- Google 在 2018 宣布正式啟動「行動版內容優先索引系統 Mobile First Indexing」

- 使用特點 - 觸控操作 ( 滑動、拖曳、縮放 )、性能有限、上網模式差異

- [設計技巧](https://developer.apple.com/design/tips/)

  - 注意點選尺寸大小和間距，避免難以點選

    - google 建議 `48px x 48px` 以上 / apple 建議 `44px x 44px` 以上

  - 一眼就要知道可以按 ( 不像電腦有 `hover` 效果 )

  - 讓寬度能自適應畫面大小，避免寫死

  - 文字尺寸最少應大於 `11px` ( 不須放大就能看清 )

    > 網頁一般文字應大於 `12px`，標題應大於 `14px`

- 建立行動裝置專用的網站

  - 行動裝置專用網站 vs 響應式網站 (rwd)

    | Comparison             | 行動裝置專用網站      | 響應式網站            |
    | ---------------------- | --------------------- | --------------------- |
    | 資訊發布特性           | ✅ 可針對行動裝置提供 | ⚠️ 和電腦獲得相同資訊 |
    | 架構設計上的自由度     | ✅ 較高               | ⚠️ 較低               |
    | 建構新網站的技術難易度 | ✅ 較高               | ⚠️ 較低               |
    | 營運上耗費的能力       | ⚠️ 較高               | ✅ 較低               |
    | 建構成本 & 所需時間    | ⚠️ 較高               | 響應式 ✅ 較低網站    |

  > [Google 的測試行動裝置相容性](https://search.google.com/test/mobile-friendly)

  - 所有設計尺寸都應以 `x2` 完成，畫面寬度需容許 `320px` ~ `640px` 的可變幅度

  - 加上 `viewport` 設置，`initial-scale` 讓使用者能夠用手指縮放

    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    ```

  - 考慮到裝置換方向時自動調整文字大小，可加上以下來避免文字尺寸自動調整

    ```css
    html {
      --webkit-text-size-adjust: 100%;
    }
    ```

  - 電話號碼自動偵測功能

    - 手機若發現電話號碼，會將他自動轉換成連結，觸碰就能撥出

    - 此功能無法分辨電話和傳真的差異，因此常使用 `meta` 設置將此功能關閉

      ```html
      <meta name="format-detection" content="telephone=no" />
      ```

  - SEO 優化 - 為了避免搜尋引擎將兩個網站視為重複內容而產生負面影響

    ```html
    <!-- 電腦版網址 - http://www.example.com/ -->
    <!-- 手機板網址 - http://www.example.com/sp/ -->

    <!-- 電腦版加上 (知會搜尋引擎有手機專用網站的存在) -->
    <link
      rel="alternate"
      media="only screen and (max-width: 640px)"
      href="http://www.example.com/sp/"
    />

    <!-- 手機版加上 (與電腦版網址產生關連) -->
    <link rel="canonical" href="http://www.example.com/" />
    ```

  - 準備首頁專用 icon ( 正方形，可以抓 `180px * 180px` )

    > [favicon generator](https://realfavicongenerator.net/)

    ```html
    <!-- apple-touch-icon.png -->

    <!-- iOS Safari、Android 標準瀏覽器 -->
    <link rel="apple-touch-icon" href="apple-touch-icon.png" />

    <!-- Android Chrome -->
    <link rel="icon" sizes="192x192" href="apple-touch-icon.png" />
    ```

  - 檢測環境，注意有無 `-webkit-` 前綴的需要

  - 請勿使用 Flash，行動裝置都不支援

## 前綴字元

- 通常是瀏覽器供應商為了實驗性質而制定的，防止破壞原有的標準語法，實驗沒問題後，再移除轉而使用標準語法撰寫

- 因此當某些屬性在某個瀏覽器上失效，可能就是少加了前綴

- 以下為常見的前綴
  - `-webkit-` ( Chrome、Safari、Edge、新的 Opera、幾乎所有 IOS 瀏覽器 )
  - `-moz-` ( Firefox )
  - `-o-` ( Opera )
  - `-ms-` ( Internet Explorer )
