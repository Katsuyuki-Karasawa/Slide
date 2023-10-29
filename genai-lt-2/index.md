---
marp: true
theme: wave
headingDivider: 1
paginate: true
size: 16:9
transition: fade 0.3s
---

<!-- _class: lead -->
# Google PixelとAI
### 発表者: L4Ph


![bg right:50%](https://github.com/Katsuyuki-Karasawa.png)

---

<!-- _header: 自己紹介 -->
## 誰?
- キーボード/ガジェット/音響/自作PC etc...のオタク
- LT会を開こうと提案して、実際はすべて投げた人
- 社会人1年目
- 元遊舎工房の舎員 <i class="fa-regular fa-keyboard" style="color: #66b9d2;"></i> / 現一般エンジニア
![bg left:30%](https://media.discordapp.net/attachments/915026053481771072/1161133756330033242/PXL_20231010_025009615.jpg?ex=6549a614&is=65373114&hm=7fe82921c18b40479cca4f94413c821836e4112099f80e098e0b841a78881c78&=&width=668&height=890)
- 重度キーボードオタクです ぜひ語り合いましょう

---

## なにを話すの
割とタイトル通り
- 技術的なことはほとんどありません(雑魚エンジニアなので) = みんな分かる
- Google Pixel持ってる人がいたら、今後に期待してみると面白いかも

---

## Google Pixelってなに
Googleが開発したスマホ
- Tensorという独自SoC(System on Chip)が搭載されたスマホ
- 最近もPixel 8 / 8 Proが発売された(Tensor G3)
- 性能は十二分に高い、AOSPからほとんどカスタムされていないので使いやすい
- 日本のAndroidシェアでは結構圧倒的
- iPhoneか、Pixelか、それ以外というレベルで二極化

![bg opacity:0.1](https://lh3.googleusercontent.com/r7H10oZ5rVfJjr8IuAmqWHxT_2dt41WSEHW88d0UfvX6VeH_yWDCW35sTs4m1Y2nprz1QCweTLVpi5l8w76rz1yojyaFseDxPOiJnL_vIrnTKp7ylwMMdD4rAaut6iXvBTl1Mt0SVDIpy_Tw2a_dHclfr5BsSi1uTPyRIE57qDL_e5ikMMupAra3RbpCWug)

---

## どこが独自SoCなの
いろいろ
- Googleが自社で設計して、(いまは)Samsungが製造
- (たぶん)Qualcomm依存からの脱却
- [**TPU(Tensor Processing Unit)**](https://cloud.google.com/tpu) というのが載ってる 👈これ今日の話で重要
- そのため、Pixelでしかできないことがいくつかある

---

## TPU(Tensor Processing Unit)って?
### Googleが開発した機械学習用のプロセッサ

Nvidiaなら**A100** / **H100** / **X100**
AMDなら**Instinct**シリーズ
つまり、**すごいAI向けのつよつよプロセッサ**

![bg right:35%](https://storage.googleapis.com/zenn-user-upload/76d0a7d3bb3a27536788cfef.gif)

--- 
## もう少し詳しく説明
- GCP(Google Cloud Platform)のCloud TPUで使用可能
- 演算精度の緩和(= 8bit/16bit)し、推論に特化
    - 推論の精度を犠牲に、データ量や消費電力が1/4、1/2に
- シストリックアレイ化により、データの高局所性化
    - よくやり取りするデータを近くに配置することで無駄を排除

### シストリックアレイ化については以下が参考になるので読んでみてください。
[Google TPUを作ってみる～アーキテクチャ考察編～](https://qiita.com/arutema47/items/b7be3aacd3c0d467a469)

---
![bg bottom:20%](https://storage.googleapis.com/zenn-user-upload/1003622b6afe47f53e70ac84.gif)

---

## 主題
ここからはオタクの妄想を話すだけです。


---

## どういうものができそうなのか
- アップスケール
- フレーム補完
- 指紋/顔認証精度の向上
- Pixel Launcherのアクセシビリティの向上
- Google製品とのインテグレーション向上
- pKVMの活用

他にもいくつかありますが、パッと思い浮かぶのだとこれくらい

---

## アップスケール
これは比較的分かりやすいと思います。  
- NvでいうDLSS  
- AMDでいうFSR  
- Qualcomm: Snapdragon GSR
- intel: XeSS

など。  

アップスケールを行うことで、ネイティブ解像度と比較して大幅に負荷が減少します。

---


## フレーム補完
現在のフレームから、次のフレームを推定することでフレームを生成し、フレーム間に挿入することでFPSを向上させる技術です。
本来スマホでフレーム補完を行う場合は、PixelworksのMEMCチップが必要です。
代替としてTPUを使用することも可能性がありますし、MEMCチップのコストを大幅に減らすことができます。

AMD RadeonのFSR3から実装されているFluid Motionが同じ技術にあたります。

---

## 