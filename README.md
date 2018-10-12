timetable
===

卒業研究
時間割自動編成システム

## 目的
私の所属していた高専では，時間割編成をMicrosoft社の表計算ソフトExcelとVBマクロを用いて手動で行っている．
そのため，完成までに膨大な時間と労力を要する．
そこで，その負担を少しでも減らすことを目的として，この研究を行った．

## 背景
時間割編成問題は，組合せ最適化問題の一つであり，NP困難である．
よって，この問題では，厳密解を求めるのではなく限られた時間内で実用的な解(近似解)を求める近似解法が用いられる．
近似解法には以下のような種類が存在する．
 * 局所探索法
 * 遺伝的アルゴリズム
 * 焼きなまし法
 * タブー探索法

## 提案手法
### 授業タイプ
すべての授業を以下のように分類した．
* 特別授業: 教室以外の実験室等を使う授業
* 同時授業: 学年や学科をまたがる授業
* 選択授業: 選択科目がある授業
* 卒業研究
* LHR
* 通常授業: 上記の5つを除いた授業

前提として，各クラスの担当教員や各授業の担当教員，使用教室などはあらかじめ決められているものとする

### 制約条件
時間割編成問題には，主に以下の2つの制約が存在する．
* ハード制約: 時間割が実行可能となるための条件
* ソフト制約: 学生，教員にとってより良い時間割となるための条件

### 固定授業
上記で分類した授業タイプの打うち，実際に運用された時間割において，事件実習系科目，非常勤講師による授業は実施時間帯を固定した．

### 初期解の生成
時間割を「学年×クラス×曜日×時間帯」の４次元配列によって表現した．
初期解の生成方法は，まず，固定授業を配置する．
次に，一部のハード制約を満たすように授業をランダムで配置する．

### 近傍解の生成
今回において，ある解に対する近傍解を「1組の授業の配置時間帯を入れ替えた状態」と定義した．
