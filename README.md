# Lesson3 制御構文 追加課題

## 課題じゃんけんゲームのプログラムを作成しよう

Review02Advance という名前のクラス（mainメソッドあり）を作成してください。

その中に、以下の仕様を満たすプログラムを書いてください。



【じゃんけんゲーム問題】

あなたとPCがじゃんけんの勝負をします。
最初に3勝した方が勝ちとなり勝負が終了します。

###  じゃんけんゲームの流れ

1. あなたは、コンソールから グー、チョキ、パーのいずれかを選択します。
2. PCはランダムにグー、チョキ、パーのいずれかを決定します。
3. あなたとPCが出した手を比べて勝敗の判定をします。あなたの勝ち、負け、あいこのいずれかになります。
4. これを繰り返し、あなたもしくはPCが先に3勝した時に勝負が終了します。
5. 勝負が終了した際に最終結果を表示します。

以下が実行結果例となります。

```
※※じゃんけんを開始します※※
-1回戦目です
-- あなたは何を出しますか？ [g/c/p]: g
[現在] あなた: グー / PC: チョキ
あなたの勝ち
---
★ あなたの 1勝/0敗/0ひきわけ
-2回戦目です
-- あなたは何を出しますか？ [g/c/p]: p
[現在] あなた: パー / PC: パー
あいこです
---
★ あなたの 1勝/0敗/1ひきわけ
-3回戦目です
-- あなたは何を出しますか？ [g/c/p]: c
[現在] あなた: チョキ / PC: チョキ
あいこです
---
★ あなたの 1勝/0敗/2ひきわけ
-4回戦目です
-- あなたは何を出しますか？ [g/c/p]: g
[現在] あなた: グー / PC: チョキ
あなたの勝ち
---
★ あなたの 2勝/0敗/2ひきわけ
-5回戦目です
-- あなたは何を出しますか？ [g/c/p]: g
[現在] あなた: グー / PC: グー
あいこです
---
★ あなたの 2勝/0敗/3ひきわけ
-6回戦目です
-- あなたは何を出しますか？ [g/c/p]: p
[現在] あなた: パー / PC: チョキ
PCの勝ち
---
★ あなたの 2勝/1敗/3ひきわけ
-7回戦目です
-- あなたは何を出しますか？ [g/c/p]: c
[現在] あなた: チョキ / PC: パー
あなたの勝ち
---
★ あなたの 3勝/1敗/3ひきわけ
※勝負がつきました！※
======
※※最終結果※※
---
★ あなたの 3勝/1敗/3ひきわけ

```

#### 仕様

1. mainメソッドの中で、まずは以下の4つの変数を用意します。

```
		// じゃんけんの手を表現する文字列配列
		String[] hands = { "グー", "チョキ", "パー" };
		// 1回のじゃんけん結果を保存する整数型配列。第一要素はあなたの勝ち数、第二要素はあなたの負け数、第三要素はあいこの数を保存
		int[] results = { 0, 0, 0 };
		// 勝負がつく勝ち数
		final int MAX = 3;
		// 今何回戦かを示すカウンター
		int count = 1;
```

2. コンソールでキーボードからの入力値を文字列として取得する以下のメソッドを以下のように定義してください。

```
	/*
	 * キーボードから入力された値をStringで返す 引数：なし 戻り値：入力された文字列
	 */
	private static String keyIn() {
		String line = null;
		try {
			BufferedReader key = new BufferedReader(new InputStreamReader(System.in));
			line = key.readLine();
		} catch (IOException e) {

		}
		return line;
	}
```

3. "g", "c", "p"のいずれかの文字列を引数とし、それぞれの引数値に応じて "グ―", "チョキ", "パー"　のいずれかの文字列を戻り値として返す getYourHand という名前のメソッドを作成してください。

```
	/*
	 * 引数の文字列をもとに"グー"、"チョキ"、"パー"のいずれかの文字列を返す
	 * 引数："g", "c", "p" のいずれかの文字列
	 * 戻り値："グー", "チョキ", "パー" のいずれかの文字列
	 */
	public static String getYourHand(String hand) {
	　// switch文を使って 引数handに値によって戻り値を場合分け
	}
```

4. 仕様1で定義したhands配列を引数とし、ランダムに、"グー"、"チョキ"、"パー" のいずれかの文字列を戻り値とする getPcHand　という名前のメソッドを以下のように定義してください。

```
	/*
	 * PCのじゃんけんの点を決定する。ランダムに "グー"、"チョキ"、"パー"のいずれかの文字列を返す
	 * 引数：hands配列
	 * 戻り値："グー", "チョキ", "パー" のいずれかの文字列
	 */
	public static String getPcHand(String[] hands) {
		// 0, 1, 2 いずれかの乱数
		int rand = (int) Math.floor(Math.random() * 3);
		return hands[rand];
	}
```


5. 仕様1で定義したresults配列を引数とし、現状の勝敗結果をコンソールに表示する以下のメソッドを定義してください。

```
	/*
	 * 現状の勝ち負けあいこの状態を表示する
	 * 引数：results配列
	 * 戻り値：なし
	 */
	public static void showStatus(int[] results) {
		System.out.println("---");
		System.out.println("★ あなたの " + results[0] + "勝/" + results[1] + "敗/" + results[2] + "ひきわけ");
	}
```

6. mainメソッドの中で、do-while文を使い、上記実行結果例と同じような結果を表示するように実装にチャレンジしてみてください。

## 解答例
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Review02Advance {
	public static void main(String[] args) {

		// じゃんけんの手を表現する文字列配列
		String[] hands = { "グー", "チョキ", "パー" };
		// 1回のじゃんけん結果を保存する整数型配列。第一要素はあなたの勝ち数、第二要素はあなたの負け数、第三要素はあいこの数を保存
		int[] results = { 0, 0, 0 };
		// 勝負がつく勝ち数
		final int MAX = 3;
		// 今何回戦かを示すカウンター
		int count = 1;

		System.out.println("※※じゃんけんを開始します※※");

		do {
			System.out.println("-" + count + "回戦目です");
			System.out.print("-- あなたは何を出しますか？ [g/c/p]: ");
			String yourHand = getYourHand(keyIn());
			String pcHand = getPcHand(hands);

			System.out.println("[現在] あなた: " + yourHand + " / PC: " + pcHand);

			if (yourHand.equals(pcHand)) {
				System.out.println("あいこです");
				results[2]++;
			} else if (yourHand.equals(hands[0]) && pcHand.equals(hands[1])
					|| yourHand.equals(hands[1]) && pcHand.equals(hands[2])
					|| yourHand.equals(hands[2]) && pcHand.equals(hands[0])) {
				System.out.println("あなたの勝ち");
				results[0]++;
			} else {
				System.out.println("PCの勝ち");
				results[1]++;
			}

			showStatus(results);
			count++;

		} while (results[0] < MAX && results[1] < MAX);

		System.out.println("※勝負がつきました！※");
		System.out.println("======");
		System.out.println("※※最終結果※※");
		showStatus(results);

	}

	/*
	 * 引数の文字をもとに"グー"、"チョキ"、"パー"のいずれかの文字列を返す
	 * 引数："g", "c", "p" のいずれかの文字
	 * 戻り値："グー", "チョキ", "パー" のいずれかの文字列
	 */
	public static String getYourHand(String hand) {
		String yourHand = "";

		switch (hand) {
		case "g":
			yourHand = "グー";
			break;
		case "c":
			yourHand = "チョキ";
			break;
		case "p":
			yourHand = "パー";
			break;
		}

		return yourHand;

	}

	/*
	 * PCのじゃんけんの点を決定する。ランダムに "グー"、"チョキ"、"パー"のいずれかの文字列を返す
	 * 引数：hands配列
	 * 戻り値："グー", "チョキ", "パー" のいずれかの文字列
	 */
	public static String getPcHand(String[] hands) {
		// 0, 1, 2 いずれかの乱数
		int rand = (int) Math.floor(Math.random() * 3);
		return hands[rand];
	}

	/*
	 * 現状の勝ち負けあいこの状態を表示する
	 * 引数：results配列
	 * 戻り値：なし
	 */
	public static void showStatus(int[] results) {
		System.out.println("---");
		System.out.println("★ あなたの " + results[0] + "勝/" + results[1] + "敗/" + results[2] + "ひきわけ");
	}

	/*
	 * キーボードから入力された値をStringで返す 引数：なし 戻り値：入力された文字列
	 */
	private static String keyIn() {
		String line = null;
		try {
			BufferedReader key = new BufferedReader(new InputStreamReader(System.in));
			line = key.readLine();
		} catch (IOException e) {

		}
		return line;
	}
}

```