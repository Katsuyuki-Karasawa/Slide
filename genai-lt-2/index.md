---
marp: true
theme: wave
headingDivider: 1
paginate: true
size: 16:9
transition: fade 0.3s
---

<!-- _class: lead -->
# ガジェオタから見る、Googleと生成AI
### 発表者: L4Ph

---

<!-- _header: 自己紹介 -->
## 誰?
- キーボード / ガジェット / 音響 / マウス / 自作PC etc...のオタク
- LT会を開こうと提案して、実際はすべて投げた人(ごめんなさい)
- 社会人1年目

---

## なにを話すの
割とタイトル通り
- 技術的なことはほとんどありません(雑魚エンジニアなので)
- Google Pixel持ってる人がいたら、今後に期待してみると面白いかも

---

## Google Pixelってなに
Googleが開発したスマホ
- Tensorという独自SoC(System on Chip)が搭載されたスマホ
- 最近もPixel 8 / 8 Proが発売された(Tensor G3)
- 性能は十二分に高い、AOSPからほとんどカスタムされていないので使いやすい

---

## なにが独自なの
いろいろ
- Googleが自社で設計して、(いまは)Samsungが製造
- (たぶん)Qualcomm依存からの脱却
- [**TPU(Tensor Processing Unit)**](https://cloud.google.com/tpu) というのが載ってる 👈これ今日の話で重要

---

## TPU(Tensor Processing Unit)ってなに
Googleが開発した機械学習用のプロセッサ
- 2016年に発表
- 現在は5世代(v5e)が最新
- TPU v4が

つまり、**すごいつよいぱそこん**