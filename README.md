# ACO可視化ツール

このアプリケーションは、複雑な問題解決手法である「アントコロニー最適化（ACO）」が、どのようにして最短経路という解を見つけ出すのかを、視覚的に観察し、深く理解するために開発しました。
GeminiのCanvas機能で作成したアプリです。

[アプリはこちら](https://gemini.google.com/share/f1d6ddc954e4)

## 主な特徴

### 1. インタラクティブな可視化

アリの動き、フェロモン濃度の変化（経路の色の濃さ）、そして各経路のコストやフェロモン量をリアルタイムで表示します。アルゴリズムの内部で起こっている動的なプロセスを、直感的に捉えることができます。

### 2. 詳細なパラメータ制御

ACOの挙動を決定づける重要なパラメータを、スライダーやチェックボックスで簡単に調整できます。

- **基本パラメータ**: アリの数、蒸発率、フェロモン強度
- **経路選択パラメータ**: α（フェロモン重要度）、β（コスト重要度）
- **高度な戦略**: エリート重み、ループ許可、ヒューリスティック使用

これらのパラメータが、アリたちの「探索」と「活用」のバランスにどう影響するかを実験できます。

### 3. 動的なグラフ編集機能

シミュレーションの実行中であっても、グラフを自由自在に編集できます。

- **クリックで追加**: キャンバスの空きスペースをクリックしてノードを追加。ノードを2つ順にクリックすれば、エッジ（経路）のIDが自動入力され、コストを設定するだけで簡単に追加できます。
- **手動での設定**: 入力欄にIDや数値を入力してグラフを構成することも可能です。

### 4. 多彩なサンプルグラフ

アルゴリズムの様々な側面を学習できるよう、4種類のサンプルグラフを用意しています。

- **基本**: シンプルな構成で、基本的な動きを確認できます。
- **基本2**: 実行途中に新たに道を追加して、蟻たちがどのような挙動をするか確認できる。
- **複雑**: 経路が複数絡み合い、解の候補が多いグラフです。
- **超複雑**: 更に複雑なグラフです。初期状態のグラフです。

### 5. 詳細な統計情報と解説

シミュレーションの状況を数値で正確に把握できます。特に重要なのが以下の2つです。

- **グローバル最短経路長**: シミュレーション開始から現在までに見つかった、理論上の最短記録。
- **現在の収束経路長**: 現在のフェロモン濃度が最も高い経路の長さ。

この2つの数値を比較することで、アルゴリズムが「最適解に向かっているのか」、それとも「局所解の罠にはまっているのか」を客観的に判断できます。

## 使い方

### Step 1: グラフを準備する

まずは「グラフ操作」パネルから、好きなサンプルグラフを読み込みます。あるいは、「クリア」ボタンで初期化した後、キャンバスをクリックしたり、手動入力したりして、あなただけのオリジナル問題を作成することもできます。

### Step 2: パラメータを調整する

次に「制御パネル」で各パラメータを調整します。例えば、以下のような実験が考えられます。

- **収束を早めたい場合**: エリート重みやα（フェロモン）の値を大きくしてみる。
- **もっと多様な経路を探させたい場合**: 蒸発率を少し上げてみる。
- **コストを無視させたい場合**: ヒューリスティック使用のチェックを外してみる。

### Step 3: シミュレーションを実行する

準備ができたら、実行制御ボタンを押します。

- **開始/一時停止**: シミュレーションを開始・停止します。
- **ステップ実行**: 1世代ずつアルゴリズムを進め、フェロモンがどう変化するかをじっくり観察できます。
- **リセット**: パラメータやアリの状態を初期化します。

### Step 4: 観察と分析

シミュレーションが始まったら、グラフの可視化エリアと、その下にある統計情報エリアを同時に観察します。アリたちがどの経路に集まり、フェロモン（青い経路）がどう濃くなっていくかと、「グローバル最短経路長」と「現在の収束経路長」の数値がどう変化していくかの関係性に注目してください。

### Step 5: 実験する

このツールの醍醐味は、動的な実験にあります。

- アリたちが局所解に陥ってしまったら、新しい近道（エッジ）をクリックで追加してみましょう。アリたちが新しい道に気づき、状況がどう変化するかを観察できます。
- 「ループ許可」をオンにすると、アリたちがどういう非効率な動きをするのか、なぜループ禁止が重要なのかを体感できます。

このアプリケーションを通じて、アントコロニー最適化という、自然界の叡智にヒントを得たアルゴリズムの面白さと奥深さを、ぜひご自身の「手」で体験してみてください。


# プロンプト
---
アントコロニー最適化可視化アプリ仕様書

1. 概要

グラフ問題における最短経路探索をアントコロニー最適化（ACO）アルゴリズムで解く過程を教育目的で可視化するWebアプリケーション。始点から終点への経路探索におけるアリの動きやフェロモン濃度の変化をリアルタイムで表示し、アルゴリズムの理解を深める。



2. 機能要件

2.1 グラフ作成機能

ノード追加: テキスト入力によるノード座標の手動入力

エッジ追加: ノード間の接続とコスト設定

始点・終点設定: 経路探索の開始点と目標点を指定

グラフ編集: ノード・エッジの削除、コスト変更、始点・終点の変更

制約: 最大20ノード

入力形式例

ノード: ID, X座標, Y座標

エッジ: ノードID1, ノードID2, コスト

始点: ノードID

終点: ノードID

2.2 可視化機能

2.2.1 グラフ表示

ノード: 青色円形、番号ラベル付き

始点: 緑色円形、「START」ラベル

終点: 赤色円形、「GOAL」ラベル

エッジ: 直線、コスト値表示

動的レイアウト調整機能

2.2.2 アリの動き表示

アリの視覚表現: 小さな動く点またはアリ型アイコン

移動アニメーション: エッジに沿った滑らかな移動

経路構築: 始点から終点への経路探索過程を表示

同時表示: 全てのアリを同時表示（上限なし）

アリの識別: 異なる色または形状で区別

到達状態: 終点に到達したアリの明確な表示

2.2.3 フェロモン濃度表示

色分け表示: 3段階の濃度レベル高濃度: 濃い青/紫

中濃度: 青

低濃度: 薄い青/白

数値表示: エッジ上にフェロモン濃度数値

動的更新: フェロモン蒸発・追加のリアルタイム反映

2.2.4 統計情報表示

現在の世代（イテレーション）数

フェーズ状態: 探索中/フェロモン更新中

現在の最適解（最短パス長）

各世代の最適解履歴

アリの到達状況: 何匹が終点に到達したか

収束状況の表示

2.3 制御機能

2.3.1 パラメータ調整

アリの数: 5〜100匹（スライダー）

蒸発率: 0.1〜0.9（スライダー）

フェロモン強度: 0.1〜5.0（スライダー）

α（フェロモン重要度）: 0.5〜3.0

β（距離重要度）: 0.5〜3.0

2.3.2 実行制御

開始/停止: アルゴリズムの実行制御

一時停止/再開: 途中での停止・再開

速度調整: 1x〜10x倍速（スライダー）

ステップ実行: 1世代ずつの実行

リセット: 初期状態に戻す

2.4 教育支援機能

アルゴリズム説明: 各ステップの説明表示

現在の処理: 何が起こっているかの実況表示

パラメータ効果: パラメータ変更の影響説明

3. 画面設計

3.1 レイアウト構成

┌─────────────────────────────────────────────────────────┐

│ タイトル │

├─────────────────────────────────────────────────────────┤

│ グラフ入力エリア │ 制御パネル │

│ - ノード入力 │ - パラメータ調整 │

│ - エッジ入力 │ - 実行制御 │

│ - 編集機能 │ - 速度調整 │

├─────────────────────────────────────────────────────────┤

│ │

│ グラフ可視化エリア │

│ （アリの動き・フェロモン表示） │

│ │

├─────────────────────────────────────────────────────────┤

│ 統計情報・説明エリア │

│ - 現在の世代・最適解 │

│ - アルゴリズム説明 │

│ - 履歴グラフ │

└─────────────────────────────────────────────────────────┘

3.2 UI要素詳細

3.2.1 制御パネル

パラメータ調整用スライダー

開始/停止ボタン

速度調整スライダー

リセットボタン

3.2.2 グラフ可視化エリア

Canvas要素でのグラフ描画

リアルタイムアニメーション

800x600px程度のサイズ

3.2.3 統計エリア

数値表示エリア

収束グラフ表示

アルゴリズム解説テキスト

4. アルゴリズム仕様

4.1 ACOアルゴリズム実装（最短経路問題）

初期化

全エッジのフェロモン濃度を初期値に設定

全アリを始点ノードに配置

始点・終点を明確に設定

各世代の処理フロー

フェーズ1: 探索フェーズ各アリが始点から確率的に次のノードを選択

訪問済みノードは選択対象から除外（ループ回避）

全アリが終点に到達するまで継続

フェーズ2: フェロモン更新フェーズアリの移動が完了したことを確認

フェロモン蒸発処理

各アリの経路に沿ってフェロモン追加

最適解の更新

フェロモン濃度の可視化更新

確率計算



P(i,j) = [τ(i,j)]^α × [η(i,j)]^β / Σ[τ(i,k)]^α × [η(i,k)]^β

τ: フェロモン濃度

η: ヒューリスティック値（1/距離）

訪問済みノードkは除外

終了条件

全アリが終点に到達

行き止まりの場合は最も近いノードから再開始

4.2 可視化更新タイミング

探索フェーズ中フレームレート: 30fps

アリの位置更新: 毎フレーム

到達アリ数の表示: リアルタイム

フェロモン更新フェーズフェロモン濃度更新: 全アリ到達後

統計情報更新: フェロモン更新完了時

次世代開始: ユーザー確認後または自動

5. 技術要件

5.1 開発環境

Google Gemini Canvas機能

HTML5 Canvas API

JavaScript ES6+

5.2 パフォーマンス要件

最大20ノードでの滑らかな動作

リアルタイム可視化（30fps）

レスポンシブなUI操作

5.3 ブラウザ対応

Chrome, Firefox, Safari, Edge

モダンブラウザでのCanvas API対応

6. データ形式

6.1 グラフデータ

{

nodes: [

{id: 1, x: 100, y: 200, label: "1"},

{id: 2, x: 300, y: 150, label: "2"}

],

edges: [

{from: 1, to: 2, cost: 5, pheromone: 1.0}

]

}

6.2 アリデータ

{

id: 1,

currentNode: 1,

targetNode: 5, // 終点

path: [1, 2, 3], // 始点から現在までの経路

pathLength: 8,

isCompleted: false, // 終点到達フラグ

position: {x: 150, y: 175}, // アニメーション用現在位置

visitedNodes: [1, 2, 3] // 訪問済みノード（ループ回避用）

}

6.3 世代データ

{

generation: 1,

phase: "exploring", // "exploring" | "updating_pheromone"

completedAnts: 5, // 終点に到達したアリ数

totalAnts: 10, // 総アリ数

bestPath: [1, 2, 4, 5],

bestPathLength: 12,

allAntsCompleted: false

}

7. 教育的配慮

7.1 理解促進要素

フェーズ別説明: 探索フェーズとフェロモン更新フェーズの詳細説明

アリの到達状況: 何匹が終点に到達したかの実況

パラメータの影響: パラメータ変更が経路選択に与える影響を視覚化

収束過程: 最適経路への収束過程の分かりやすい表示

フェロモン濃度の意味: 濃度変化が次世代の経路選択に与える影響の説明

7.2 インタラクティブ要素

パラメータのリアルタイム調整: 次世代から反映

フェーズ毎の一時停止: 探索完了時とフェロモン更新完了時での観察

世代単位での実行: 1世代ずつ実行して結果を確認

異なる始点・終点: 同じグラフで異なる経路問題の実験

経路比較: 複数世代の最適経路を重ねて表示

---
## 追加
複数のアリが移動するとき、重なって何率いるのか見えない。スタートに近づくようにアリが移動したとき、そのアリがゴールにたどり着いていないのにフェイズが終了する。ノード間の距離がわかりづらい。制御パネルを操作しながら画面を見られるように配置を変更。
制御パネルの数値について、それぞれの項目が何か説明するボタンを追加。最短経路長だけでなく、収束する経路の長さを表示するようにする。
実行途中でも、画面をクリックすることで新たなルートを追加することができるようにする。
