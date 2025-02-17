# GroupWork

## 概要　　　　　　　　　　　　　　　　　　　　　　　　　
	テーマ：RPG
	言語：Java
	使用ツール：Git / GitHub / PowerShell
	期間：

## システムの流れ								
	初期化・変数の準備など

	OUTPUT 登録するIDとパスワードを入力してください
	INPUT　IDとパスワードを入力する・データベースに保存する
	OUTPUT ユーザー登録が完了しました

	OUTPUT　IDとパスワードを入力してください
	INPUT　IDとパスワードを入力する・パスワードとIDを照合
	OUTPUT　ログインに成功しました　/　失敗しました

	OUTPUT　キャラクターの名前を入力してください
	OUTPUT　キャラクターの職業を選んでください
	INPUT キャラクターを作成する・変数などに入れて値を保持
	
	　　　モンスターを生成する・変数などに入れて値を保持

	OUTPUT　モンスターｘが現れた
		行動を選択してください
	INPUT　行動を選ぶ
	OUTPUT　ｘにｙのダメージ
		倒す　/　倒されるまで続ける
		モンスターの数分繰り返す
	
	OUTPUT　モンスターをすべて倒した
		ゲームクリア
		
## 完成イメージ　								

	 ＜ユーザー登録＞
	 IDとパスワードを入力してください >>>
	 ID >>> test
	 パスワード >>>test

	 ユーザー登録が完了しました

	 ＜ログイン＞
	 IDとパスワードを入力してください >>>
	 ID >>> test
	 パスワード >>>test

	 ログインに成功しました

	 ＜キャラクター作成＞
	 勇者の名前を入力してください >>> ゆうしゃ
	 勇者の装備を選んでください
	 炎の剣　氷の剣　風の剣 >>> 炎の剣

	 炎の剣を装備しました
	 スペシャルスキル　ファイヤーアタックを取得しました

	 魔法使いの名前を入力してください >>> まほう
	 魔法使いの装備を選んでください
	 炎の杖　氷の杖　風の杖 >>> 氷の杖

	 氷の杖を装備しました
	 スペシャルスキル　アイスマジックを取得しました

	 格闘家の名前を入力してください　>>>　かくとう
	 格闘家の装備を選んでください
	 炎の手袋　氷の手袋　風の手袋 >>> 風の手袋

	 風の手袋を装備しました
	 スペシャルスキル　ウィンドパンチを取得しました

	 準備が整いました
	 ～適当なストーリー～

	 モンスター　スライムが現れた！（HP：10）
	 勇者の行動を選んでください
	 攻撃　回復　雷斬り　特殊攻撃　>>> 攻撃

	 スライムに10のダメージ！
	 スライムを倒した！

	 モンスター　おばけキノコが現れた！（HP：100）
	 勇者の行動を選んでください
	 攻撃　回復　雷斬り　特殊攻撃　>>> 攻撃

	 おばけキノコに10のダメージ！

	 魔法使いの攻撃を選んでください
	 ～～～～～

	 モンスター　ドラゴンが現れた！（HP:500）
	 ～～～

	 ドラゴンを倒した！

	 ゲームクリア！


## 要件定義　　　　　　　　　　　　　　　　　　　　　　　
	①ログイン機能
		・アプリケーションにログイン
		・ユーザーIDとパスワードの入力により認証
		・ユーザー登録の必要がある
	②ユーザー登録機能
		・ユーザー登録をする
		・登録する情報は、
			ユーザーID / パスワード
		・同じユーザーIDは登録できない
	③キャラクター作成機能
		・キャラクターを作成する
		・名前を入力して登録する
		・職業を選んで登録する
		・職業の種類は、
			勇者 / 魔法使い / 格闘家
		・３人のキャラクターを作成する
	④モンスター生成機能
		・モンスターを生成する
		・モンスターの種類は、
			スライム / おばけキノコ / ドラゴン
		・すべてのモンスターを倒せたらクリア
	⑤装備機能
		・キャラクターはそれぞれ装備を身に付けることが出来る
		・装備は特有のスキルを持つ
	⑥道具使用機能




## クラス設計　　　　　　　　　　　　　　　　　　　　　　　　　
	①ログイン機能
	②ユーザー登録機能

	③キャラクター作成機能
		◆Hero.java (勇者)◆
			名前：name
			HP:hp（初期値は300）
			最大HP：MAX_HP(定数、300)
			MP:mp（初期値は50）
			最大MP:MAX_MP(定数、50)
										
			戦う:Attack　敵１体に切りつける（10～15のダメージ）
			回復:Aid　味方一人のHPを回復する（10　+　1～5のランダム、MPを5消費）
			雷斬り:Thunder力を込めた剣で切り裂く（30のダメージ、MPを15消費）
			
		◆Wizard.java(魔法使い)◆
			名前:name
			HP:hp（初期値は100）
			最大HP：MAX_HP(定数、100)
			MP:mp（初期値は80）
			最大MP:MAX_MP(定数、80)
										
			戦う:Attack　敵１体を殴りつける（3～6のダメージ）
			炎魔法:Fire　炎で焼き尽くす（20のダメージ、MPを10消費）
			自暴自棄：Bomb　MPをすべて使って爆発させる（消費MP分のダメージ）

		◆Fighter.java(格闘家) ◆
			名前:name
			HP:hp（初期値は200）
			最大HP：MAX_HP(定数、200)
			MP:mp（初期値は10）
			最大MP:MAX_MP(定数、10)
										
			戦う:Attack　敵を力一杯蹴る（5のダメージ　×　1～3のランダム回数）
			MPを分ける：Share　味方一人にMPをあげる（MPすべてを指定の味方にプレゼント）
			自己研鑽：PowerUp　自分の攻撃力を5あげる（戦う、をしたときのダメージが5上がる）

	④モンスター生成機能
		◆Slime.java(スライム) ◆
			名前:name（スライム１，２，３などと複数召喚出来る）
			HP:hp(初期値は10)
										
			攻撃：Attack　ぷるぷる攻撃する（3のダメージ）
			うずくまる：Crouch　なにもせず丸くなる

		◆Matango.java(おばけキノコ) ◆
			名前:name
			HP:hp(初期値は100)
										
			毒攻撃：Poison １体のHpが3減少、2ターン続く
			大暴れ:Rampage　敵全員に5のダメージ

		◆Dragon.java(ドラゴン) ◆
			名前:name
			HP:hp(初期値は500)
										
			炎の息：FireBreath　全員に10のダメージ
			噛みつく：Bite　１体に20のダメージ

	⑤装備機能
		◆Sword.java(剣、勇者が装備できる) ◆
			名前：name
			スキル：skill
										
			特殊攻撃：SpecialAttack　武器固有のスキルを発動する

		◆Staff.java(杖、魔法使いが装備できる) ◆
			名前：name
			スキル：skill
										
			特殊攻撃：SpecialAttack　武器固有のスキルを発動する

		◆Globe.java(グローブ、格闘家が装備できる) ◆
			名前：name
			スキル：skill
										
			特殊攻撃：SpecialAttack　武器固有のスキルを発動する
      
## ファイル階層　　　　　　　　　　　　　　　　　　　　　
	◆Main.java
	
	操作キャラクターの作成
	 ⬜︎Character PL:
	  ↑継承
	 ◆Hero 担当:
	 ◆Wizard 担当:
	 ◆Fighter 担当:

	モンスターの作成
	 ⬜︎monster PL:
	  ↑継承
	 ◆Slime 担当:
	 ◆Matango 担当:
	 ◆Dragon 担当:

	装備の作成
	 ⬜︎weapon PL:
	  ↑継承
	 ◆Sword 担当:
	 ◆Staff 担当:
	 ◆Globe 担当:

## その他記載事項
	・キャラクター作成部門３人（内１人がリーダー）
	・モンスター作成部門３人（内１人がリーダー）
	・リーダーが大元となるクラスを作成し、それを継承して具体的なクラスを作成していく
	 例）Character をリーダーAさんが作成
	   Characterを継承してAさんがHero、BさんがWizard、CさんがFighterを作成
	・具体的なクラス名（Hero,Slimeなど）は変えてもOK、その場合は全体に情報を共有する
	・各クラスは名前、属性、操作をクラス図にまとめて共有する（概要通りでなくてもよい）
	・余裕があればさらに継承してSuperHeroなどを作ったり、スキルを増やしたりしてもよい
	・Mainクラスに関しては、現時点では各人が作成して完成形とする
	（各クラスを分担して作成しGitHub上に集約、その後各々でクローンしてMainクラスを作成し完成させる）
	・ポートフォリオなどの成果物として発表してもよい
	
