## 其他元素

- `pre`

- `code`

## HTML5 新元素

- `time` - 以電腦可辨識的時間格式，表示 24 小時制的時間、西曆年月日

  - 搭配 `datetime` 屬性 - 值須為日期、時間

    ```html
    <time>13:15</time>
    <p><time date-time="2019-02-18">明天</time>有重要會議</p>
    ```

  - 格式 - `YYYY-MM-DDThh:mm:ssTZD`

    | Type                | Example                   |
    | ------------------- | ------------------------- |
    | 年                  | `2019`                    |
    | 年月                | `2019-01 `                |
    | 年月日              | `2019-01-01`              |
    | 時分                | `08:30`                   |
    | 時分秒              | `08:30:21`                |
    | 年月日時分秒        | `2019-01-01T08:30:21`     |
    | 年月日時分秒 + 時區 | `2019-01-01T08:30:21+9:0` |

- `ruby` - 用來標示注音，透過 `rt` 設定注音、`rp` 設置不支援時的 fallback 符號

  ```html
  <ruby>
    肉燥飯
    <rp>(</rp>
    <rt>ㄖㄡˋㄙㄠˋㄈㄢˋ</rt>
    <rp>)</rp>
  </ruby>
  ```

- `mark` - 在文字上加上底色，用在想讓使用者注意的文字，或關鍵字搜尋結果

- `video`、`audio` - 播放影片、聲音檔，而不需擔心有無安裝播放程式

  ```html
  <video src="sample.mp4" type="video/mp4" controls>
    您的瀏覽器未支援 video 元素，請改用最新版的瀏覽器開啟
  </video>

  <audio src="sample.mp3" controls>
    您的瀏覽器未支援 audio 元素，請改用最新版的瀏覽器開啟
  </audio>
  ```

  - `controls` 可讓使用者操作影片播放、調節音量等等

  - `source` - 可以放置多個，提供不同格式的影片、聲音檔

    ```html
    <video controls>
      <source src="sample.mp4" type="video/mp4" />
      <source src="sample.webm" type="video/webm" />
    </video>

    <audio controls>
      <source src="sample.mp3" type="video/mp3" />
      <source src="sample.wav" type="video/wav" />
    </audio>
    ```

- `picture` - 依照畫面尺寸、解析度等環境差異，顯示不同圖片

  ```html
  <picture>
    <source media="(max-width: 640px)" srcset="img/small.jpg" />
    <source media="(max-width: 960px)" srcset="img/medium.jpg" />
    <!-- 用 img 指定預設圖片 -->
    <img src="img/large.jpg" alt="xxx" />
  </picture>
  ```

## HTML5 新屬性

- `data-*` - 自訂資料屬性，通常搭配其他東西使用 ( Ex. CSS、JavaScript )

  ```html
  <a href="#" data-tooltip="Hello">Example</a>

  <style>
    a::after {
      content: attr(data-tooltip);
      /* ... */
    }
  </style>

  <script>
    element.dataset.tooltip;
  </script>
  ```

- `aria-*`

- `role` - 用來定義各元素的角色 ( 大多有對應的元素可以直接使用 )

  | Value           | Definition                  | Related Element |
  | --------------- | --------------------------- | :-------------: |
  | `application`   | 元素為 Web 程式             |        -        |
  | `search`        | 包含搜尋功能表單的區塊      |        -        |
  | `form`          | 搜尋功能以外的表單          |        -        |
  | `main`          | 文件內主要內容 ( 每頁一個 ) |    `<main>`     |
  | `navigation`    | 文件的操作導航              |     `<nav>`     |
  | `complementary` | 文件的補充資料              |    `<aside>`    |
  | `banner`        | 網站的頁首 ( 每頁一個 )     |   `<header>`    |
  | `contentinfo`   | 內容版權及隱私聲明相關連結  |   `<footer>`    |

  - 較常使用的為 `application`、`search`、`form`

- `srcset` - 為 `<img>` 元素的新屬性，讓瀏覽器適應裝置尺寸、解析度顯示不同圖片

  ```html
  <!-- 按照畫面寬度使用不同圖片 -->
  <img
    src="img/small.jpg"
    srcset="img/small.jpg 400w, img/medium.jpg 800w, img/large.jpg 1200w"
    alt="..."
  />

  <!-- 按照解析度使用不同圖片 -->
  <img
    src="img/sample.jpg"
    srcset="img/sample@2x.jpg 2x, img/sample@3x.jpg 3x"
    alt="..."
  />
  ```

- `image-set()` - 為 `background-image` 新屬性值，因應不同解析度顯示不同背景圖片

  ```css
  background-image: img-set(
    url(img/bg.jpg) 1x,
    url(img/bg@2x.jpg) 2x,
    url(img/bg@3x.jpg) 3x
  );
  ```
