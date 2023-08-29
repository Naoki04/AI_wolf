# About
This is an AI assigned-conversational game for 3~8 players. Developped for a Monthly Hackathon by Supporters in Sep 2023.

ChatGPTを用いたパーティゲームです。AIに乗っ取られた人間と、自我を保った人間に分かれて質問に答え, AIに乗っ取られた人間を特定します。

## ゲームの概要
- 参加人数: 3~8人
- Hacked(乗っ取られた人)とConcious(自我を保った人)に分かれる。
- Hackedは 1~(参加人数-2) 人
    - ゲームが始まると, 趣味などに関する質問が提示される。
        - HackedはAIに潜在意識を乗っ取られているため, 質問にはAIが答える。
        - Conciousは自我を保っているため, 自分で回答する。
    - 回答が終わると, 誰の回答かは伏せられた状態で全員に回答が提示される。
    - ２分間の会話タイムで、Hackedは自分がHackedであることに悟られないように振る舞う。
    - 会話タイムの後, 多数決でHacked容疑者を決める。
    - 選ばれた人はゲームから除外される。
- 以上を規定の質問回数を超えるか, Hackedが全滅するまで繰り返す。
    - 規定の質問回数を終了した場合, Hackedの勝利
    - Hackedが質問回数内で全滅した場合, Conciousの勝利

## ゲームの流れ
- グループ作成
    - オーナーが参加人数(n_mem: 3~8)を指定して部屋を作成し, 部屋IDを他の参加者に配る。
    - 他のユーザーが部屋IDを入力して入室するまで待機する。

- ゲームの設定
    - オーナーが乗っ取られる人数(n_con : 1<=n_con<"n_mem/2")を指定する。
    - オーナーが最大質問回数(n_trial : n_con =< n_trials < n_mem )を指定する。
    - オーナーが質問の系統を選ぶ(学校系, 趣味系, 恋愛系, オリジナル質問)

- ゲーム開始！
    - 人狼に乗っ取られるメンバーの決定・通知(ランダム)
    - 質問と審判(trial)
        - (オリジナルの質問の場合)
            - 質問者の決定, 質問者が質問を入力する
        - 人間が質問に回答する。

        - ２分間のディスカッションタイム(Zoomか何かで音声つながっている想定)
            - できればスキップ可能にする
        - 審判の時間(投票)：Conciousが投票でHacked疑いの人を選ぶ。処分する。
        - 処分されたユーザーがゲームから除外される。
    - 質問と審判は(n_trial)回繰り返す。
        - (n_trial)回以内にHackedが全滅した場合, Conciousの勝利
        - (n_trial)回の質問でHackedが生き残った場合, Hackedの勝利

### 要検討
- Hackedは投票権をもつか？
- Hackedの最大人数は？
- Hackedは他のHackedが誰かを知っているか？

---
# システム設計
## DynamoDB
1. ゲーム管理DB
ゲームID(int), タイムスタンプ, 部屋ID(int), 人数(int), メンバーid(list)
2. ゲーム進行DB

3. 質問DB\
質問の種類ID(int), 質問id(int), 質問内容(str)

## Vue.js
## Lamda


## 懸念事項
- Vue.jsはどこでDeployする？
- ユーザーの識別どうする？        

---
# 開発情報
## 状況
- 開発開始: 2023.8.29~

## 使用技術
- Vue.js
- AWS(DynamoDB, Lamda, EC2)
- ChatGPT API

## 開発メンバー
- Nao: Backend
- Kuri: FrondEnd

