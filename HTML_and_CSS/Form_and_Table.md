## Table

- 雖然使用 Table 切版是比較過去的作法，但在很多支援度較低的環境下仍會需要

  - Ex. Email、產生 PDF 的套件

- 基本結構

  ```html
  <!-- 整個表格區域 -->
  <table>
    <!-- 橫列 -->
    <tr>
      <!-- 直欄 / 直行 -->
      <td>第 1 欄</td>
      <td>第 2 欄</td>
    </tr>
  </table>
  ```

  <img src="./img/html_table_basic.png" width="500">

  - 欄位標題用 `<th>` 取代 `<td>`

    ```html
    <!-- 標題在上 -->
    <table>
      <tr>
        <th>標題 1</th>
        <th>標題 2</th>
      </tr>
      <tr>
        <td>內容 1</td>
        <td>內容 2</td>
      </tr>
    </table>

    <!-- 標題在左側 -->
    <table>
      <tr>
        <th>標題 1</th>
        <td>內容 1</td>
      </tr>
      <tr>
        <th>標題 2</th>
        <td>內容 2</td>
      </tr>
    </table>
    ```

- 可用 `<caption>` 來標記表格標題，預設會出現在表格上方

  ```html
  <table>
    <caption>
      Table Title
    </caption>
    <!-- ... -->
  </table>
  ```

- 增強表格結構，不會影響外觀，但結構較為完整，也好設置 CSS

  | Tag        | Group                                    |
  | ---------- | ---------------------------------------- |
  | `thead`    | 表格標題列                               |
  | `tbody`    | 表格資料列                               |
  | `tfoot`    | 表格最後一列元素                         |
  | `colgroup` | 表格直欄群組，方便用來做框線、背景色等等 |

  <img src="./img/html_table-structure.png" width="400">

  - 利用 `scope` 屬性增強欄位結構，技術儲存格標題以哪個方向顯示

    > 並不會影響外觀，但能讓瀏覽器更了解此表格

    - `scope="row"` - 橫列
    - `scope="column"` - 直欄

- 合併儲存格

  > 指定要合併的數量，並拿掉被合併的儲存格 (要小心移除)

  - `colspan` - 合併直欄的儲存格，也就是做橫向的合併

    ```html
    <tr>
      <td colspan="3">1</td>
      <!-- <td>2</td> -->
      <!-- <td>3</td> -->
    </tr>
    <tr>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
    ```

  - `rowspan` - 合併橫列的儲存格，也就是做縱向的合併

    ```html
    <tr>
      <td rowspan="2">1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <!-- <td>4</td> -->
      <td>5</td>
      <td>6</td>
    </tr>
    ```

  - `colspan` + `rowspan`

    ```html
    <tr>
      <td colspan="2" rowspan="2">1</td>
      <!-- <td>2</td> -->
      <td>3</td>
    </tr>
    <tr>
      <!-- <td>4</td> -->
      <!-- <td>5</td> -->
      <td>6</td>
    </tr>
    ```

## Form

- 用 `fieldset` + `legend` 讓表單結構更為完善

  ```html
  <form>
    <fieldset>
      <legend>申請人</legend>
      <div class="form-control">
        <label for="name">姓名</label>
        <input type="text" id="name" />
      </div>
      <div class="form-control">
        <label for="email">Email</label>
        <input type="email" id="email" />
      </div>
    </fieldset>
  </form>
  ```

  - `fieldset` - 用來對表單進行分組

  - `legend` - 用來定義一組表單的標題
