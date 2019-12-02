Unity Engine Challenge by mixi Shader チュートリアル
===========

これは Unity Engine Challenge by mixi のShaderチュートリアルです。
Shaderの基礎的な知識や実装方法について、例題を元に理解深めていってください。

## セットアップ
- hogehoge


## 頂点シェーダ、フラグメントシェーダとは
- hogehoge

## UV座標とは
- hogehoge

## 例題01：RGB値を変更して色を変える

シーン上に表示されているモデルの色を変えるようなShaderを実装してください。


### 進め方
- `Assets/Scenes/Tutorial01` を開いてください。
- `Assets/Shaders/Tutorial01` を開いてください。
- 頂点シェーダ `frag` に実装を追加してください。

### 実装について
`frag`関数の返り値は各ピクセルのカラー値です。
`tex2D`関数はモデルのテクスチャ情報とUV座標情報をを渡すことでピクセルの色計算して返します。
```
float4 c = tex2D(_MainTex, i.uv);
```
`float4`というのは4要素をもつ型です。
各要素へは`r`,`g`,`b`,`a`もしくは`x`,`y`,`z`,`w`としてアクセスできます。`c.rgb`など組み合わせて扱うこともできます。


## 例題02：UV座標を変更してグラデーションをさせる

シーン上に表示されているモデルのUV座標を変更してグラデーションをかけるようなShaderを実装してください。

### 進め方
- `Assets/Scenes/Tutorial02` を開いてください。
- `Assets/Shaders/Tutorial02` を開いてください。
- 頂点シェーダ `vert` に実装を追加してください。

### 実装について
モデルの色を変える方法は例題01で実装したとおりです。
グラデーションかける方法は色々ありますが、今回はUV座標を使った実装をしてください。
モデルのUV座標は`frag(v2f i)`の引数`i`から`i.uv`として得られます。
`v2f`とはshaderファイル内で定義されている構造体です。
```
struct v2f
{
    float4 vertex : SV_POSITION;
    float2 uv : TEXCOORD0;
};
```
`float2`は、`x`,`y`の2要素を持つ型です。`float4`と同様に`i.uv.x`のようにアクセスできます。


## 例題03：頂点座標を変更して波を作る

シーン上に表示されているモデルの頂点座標を変更して波Shaderを実装してください。


### 進め方
- `Assets/Scenes/Tutorial03` を開いてください。
- `Assets/Shaders/Tutorial03` を開いてください。
- 頂点シェーダ `vert` に実装を追加してください。

### 実装について
`vert`関数の返り値は各ピクセルの頂点情報です。
引数で渡される`appdata v`はUnityから受け取るモデルの頂点情報で、それを`UnityObjectToClipPos(v.vertex)`でスクリーン上に描画する座標を計算して頂点情報を作成しています。
波を実装するには常時値が変わるような変数が必要ですが、Unityの組み込み定義値として、時間`_Time`を使用できます。



## 補足問題
- fmod

- floor


