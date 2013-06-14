
<style scoped>
#dixian {
    letter-spacing: 2em;
    padding-left: 2em;
}
</style>


底線 { #dixian }
===

<dfn>底線</dfn>是一種常見的排版效果，在網際網路中更有諸多如連結等的應用。「_漢_{.pn}字標準格式」通過註記元素來呈現底線效果，並修改了其他預設使用底線樣式的元素。



註記元素 { #zhuji_yuansu }
---

在_漢_{.pn}字網頁中，改以底部邊框呈現_註記元素_{.pn}`<u>`中的底線樣式，以避免_漢_{.pn}字附著在底線上。



### 相鄰註記元素 { #xianglin_zhuji_yuansu }

在二個_相鄰_{.pn}<wbr>_註記元素_{.pn}之間，毋需以空白相隔即可得到視覺上的間隔效果。範例是二個不同卻相鄰的專有名詞，在沒有手動插入空白字符的情況下，仍有區隔二底線的小間隙，以為識別。


> _英國_{.pn}<!--注意：中間毋需插入任何空白-->_倫敦_{.pn}是個世上少有、數一數二，且融合古典及現代的大城市。



上方的例子由以下代碼實現：

    <u class="pn">英國</u><!--注意：中間毋需插入任何空白--><u class="pn">倫敦</u>是個世上少有、數一數二，且融合古典及現代的大城市。


#### 更多說明

1. 使用者開啓[[JavaScript]]{:en-GB}時有較佳瀏覽效果。

2. 二個註記元素間*不得*出現***除*「註解」`<!--comment-->`或「機會斷行元素」`<wbr>`*外***的任何隱藏、空白元素，否則底線仍將相連。



### 專名號 { #zhuanminghao }

#### 更完整的辨義功能

下面這個範例以專名號的使用來區別二個意義不同的「西文」——前者為普通名詞「西方的語文」，後者為專有名詞「_西班牙_{.pn}文」之又稱。

> _歐洲大陸_{.pn}眾多的西文當中，我最喜歡的語言是隷屬於_羅曼_{.pn}語族的_西_{.pn}文。



#### 套用合適的類別

套用類別<code>class="|pn|"</code>於使用專名號的專名上，以區分其他使用註記元素的情況。這個動作有點麻煩，卻能加強語義的區隔，並在特定的情況下加入或移除樣式。建議你可依需求選用這個類別。

範例同時以套用專名號類別、錯別字類別的二個註記元素，分別表示「專名」及「錯別字」。

*[pn]: proper noun { :en-GB }

    「先看完電影，」他說，「<u class="pn">阿呆</u>舉辦的派對我們晚點<u class="typo">在</u>去。」


如此一來——如果你的網站有這個需求的話——我們便能為色盲者提供一個沒有專名號樣式、連結具底線、錯別字仍然包含底線標示的專屬環境，

    .color-blind u.pn {
        border-bottom: 0 none;
    }

    .color-blind a:link {
        border-bottom: 1px solid;
    }



### 覆寫／去除此元素樣式 { #zhuji_yuansu-overwrite }

藉由以下代碼，你可以完整去除「_漢_{.pn}字標準格式」所定義的「++註記元素++」樣式。

    :lang(zh) u,
    :lang(ja) u {
        letter-spacing: inherit;
        border-bottom: inherit;
        padding-bottom: inherit;
        text-decoration: inherit;
    }

    u + u,
    html.han-js u + u,
    html.han-js u.adjacent {
        margin-left: auto;
    }




連結、插入等元素 { #lianjie_charu_deng_yuansu }
---

為了美觀、專名號的使用等原因，凡語系設定為「_中_{.pn}文」的網頁，皆取消了[連結][links]`<a>`、<ins>插入</ins>`<ins>`等元素的預設下劃線，並以其他樣式取代。

[links]: #lianjie_charu_deng_yuansu

> **出清品！**

> 這件上衣的價格是
  **<del datetime="2013-03-16 00:00">¥TW 650</del>
  <ins datetime="2013-03-16 00:00">¥TW 450</ins>**。

> [點選此處立即訂購！](#)

上方範例的原始碼如下，

    <html lang="zh-*">

    ……

    <p><strong>出清品！</strong></p>

    <p>這件上衣的價格是<strong>
       <del datetime="2013-03-16 00:00">¥TW 650</del>
       <ins datetime="2013-03-16 00:00">¥TW 450</ins>。</strong></p>

    <p><a href="#">點選此處立即訂購！</a></p>

    ……

    </html>



### 覆寫／去除此元素樣式 { #lianjie_charu_deng_yuansu-overwrite }

藉由以下代碼，你可以完整去除「_漢_{.pn}字標準格式」所定義的「++連結、插入元素++」樣式。

    html:lang(zh) ins {
        border-bottom: inherit;
        padding-bottom: inherit;
    }

