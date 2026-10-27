# 米山研究室 UAVグループ ウェブサイト編集手順

この文書は，米山研究室UAVグループのウェブサイトを共同編集するための手順書です.
GitHub DesktopとVisual Studio Code（VS Code）を使う方法を中心に説明します.

## 1. 公開先とリポジトリ

- 公開サイト：<https://haruabiko.github.io/yoneyama-lab-website/>
- GitHubリポジトリ：<https://github.com/HaruAbiko/yoneyama-lab-website>
- 公開元：`main`ブランチ

`main`へマージされた内容は，GitHub Pagesによる処理後に一般公開されます.
ローカルで保存しただけの変更や，作業ブランチへpushしただけの変更は公開されません.

## 2. 基本方針

編集は次の順序で行います.

1. GitHubから届いた共同編集者の招待を承認する.
2. リポジトリをPCへcloneする（初回のみ）.
3. `main`を最新状態へ更新する.
4. 作業用ブランチを作る.
5. VS Codeで編集し，ローカル表示を確認する.
6. 変更をcommitし，作業ブランチをpushする.
7. `main`宛てのPull Requestを作成する.
8. 管理者が内容を確認し，`main`へmergeする.

> `main`へ直接commit・pushせず，作業ブランチとPull Requestを使用してください.

## 3. 初回準備

### 3.1 GitHubの招待を承認する

1. GitHubから届いた招待メールを開く.
2. 自分のGitHubアカウントでサインインする.
3. **Accept invitation**を選択する.

アカウント，パスワード，アクセストークンは他の人と共有しません.

### 3.2 使用するアプリを準備する

次のアプリを使用します.

- [GitHub Desktop](https://desktop.github.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- VS Code拡張機能：Live Server

Live Serverは，VS Code左側のExtensionsから`Live Server`を検索し，発行元がRitwick Deyのものをインストールします.

### 3.3 リポジトリをcloneする

cloneは最初の1回だけ行います.

1. GitHub Desktopを開く.
2. **File → Clone repository...**を選択する.
3. **URL**タブを選択する.
4. Repository URLへ次を入力する.

   ```text
   https://github.com/HaruAbiko/yoneyama-lab-website.git
   ```

5. Local pathで保存先を選ぶ.
6. **Clone**を選択する.
7. clone完了後，**Open in Visual Studio Code**を選択する.

## 4. 編集を始める前の操作

### 4.1 mainを最新状態にする

1. GitHub Desktopを開く.
2. 上部の**Current branch**が`main`であることを確認する.
3. `main`でない場合は，**Current branch → main**を選択する.
4. **Fetch origin**を選択する.
5. **Pull origin**が表示された場合は選択する.

### 4.2 作業用ブランチを作る

1. **Current branch**を選択する.
2. **New branch**を選択する.
3. 変更内容が分かる名前を入力する.

例：

```text
docs/update-professor-profile
docs/update-research-description
fix/correct-typo
```

4. **Create branch**を選択する.

ブランチ名は，半角英数字とハイフンを使うとトラブルが少なくなります.

## 5. VS Codeで編集する

GitHub Desktopの**Open in Visual Studio Code**を選択して，サイトを開きます.

### 主なファイル

| ファイル | 内容 |
|---|---|
| `index.html` | トップページ |
| `about.html` | UAVグループ紹介 |
| `research/uav.html` | UAV研究の概要 |
| `research/fixed-wing.html` | 固定翼班 |
| `research/ppg.html` | PPG班 |
| `assets/images/` | 公開用画像 |
| `README.md` | リポジトリ概要 |

### 編集時の注意

- HTMLタグの`<`，`>`，`"`を誤って削除しない.
- 文章だけを変更する場合も，変更箇所の前後を確認する.
- 人数，役職，所在地，研究内容は関係者の確認を取る.
- 写真を追加する前に，人物の掲載許可を確認する.
- 発表資料，掲示物，PC画面，機体ラベル，個人情報，未公開研究が写っていないか確認する.
- `assets/originals/`と`.hermes/`は公開対象にしない.
- パスワードやアクセストークンをファイルへ書かない.

## 6. ローカルで表示を確認する

1. VS Codeで`index.html`を開く.
2. 右下の**Go Live**を選択する.
3. ブラウザーでサイトを確認する.

確認項目：

- 変更した文章に誤字がない.
- 見出しや改行が崩れていない.
- メニューとリンクが開く.
- 画像が表示される.
- PC幅とスマートフォン幅の両方で読める.

`127.0.0.1`または`localhost`で始まるURLは，編集しているPCだけで表示できる確認用URLです. 一般公開URLではありません.

## 7. commitとpush

### 7.1 変更をcommitする

1. ファイルを保存する（`Ctrl + S`）.
2. GitHub Desktopへ戻る.
3. 左側のChangesで変更ファイルと差分を確認する.
4. Summaryへ変更内容を入力する.

例：

```text
Update professor profile
Correct UAV research description
Fix typo on top page
```

5. **Commit to 作業ブランチ名**を選択する.

### 7.2 ブランチをpushする

初回は**Publish branch**，2回目以降は**Push origin**を選択します.

pushしても，この時点では公開サイトへ反映されません.

## 8. Pull Requestを作る

1. GitHub Desktopの**Create Pull Request**を選択する.
2. GitHubの画面で次の組み合わせを確認する.

   ```text
   base: main
   compare: 作業ブランチ名
   ```

3. タイトルと変更内容を入力する.
4. **Create pull request**を選択する.

Pull Request本文の例：

```markdown
## 変更内容

- 教員紹介文を更新
- 研究内容の表現を修正

## 確認したこと

- [x] ローカル表示
- [x] リンク
- [x] 誤字脱字
- [x] 写真・個人情報・未公開情報
```

Pull Request作成後，管理者へURLを共有します. 管理者が内容を確認し，`main`へmergeします.

## 9. 追加修正が発生した場合

### Pull Requestがまだ開いている場合

同じ作業ブランチで修正し，再度commit・pushします. 新しいcommitは，開いている同じPull Requestへ自動で追加されます.

### Pull Requestがすでにmergeされた場合

`main`へ戻ってPullした後，原則として新しい作業ブランチを作ります. マージ済みのPull Requestへ変更を後から追加することはできません.

## 10. merge後の更新

管理者からmerge完了の連絡を受けたら，GitHub Desktopで次を行います.

1. **Current branch → main**を選択する.
2. **Fetch origin**を選択する.
3. **Pull origin**が表示された場合は選択する.
4. 不要になった作業ブランチは削除する.

次の編集も，最新の`main`から新しい作業ブランチを作って始めます.

## 11. ターミナルで操作する場合

### 初回clone

```bash
git clone https://github.com/HaruAbiko/yoneyama-lab-website.git
cd yoneyama-lab-website
```

### 通常の編集開始

```bash
git switch main
git pull --ff-only origin main
git switch -c docs/update-description
```

### 編集後

```bash
git status
git add 変更したファイル
git commit -m "docs: update website description"
git push -u origin docs/update-description
```

push後，GitHubで`main`宛てのPull Requestを作成します.

## 12. 困ったとき

### 変更がGitHub Desktopに表示されない

- VS Codeでファイルを保存したか確認する.
- GitHub Desktopで正しいリポジトリを開いているか確認する.
- VS CodeとGitHub Desktopで同じフォルダーを使用しているか確認する.

### `There isn't anything to compare`と表示される

- `compare`に正しい作業ブランチが選ばれているか確認する.
- 作業ブランチをpush済みか確認する.
- `main`との差分が実際にあるか確認する.

### conflictと表示される

競合した状態で無理にmergeせず，管理者へ連絡してください. 競合箇所以外を含めて上書きすると，他の人の変更が消える可能性があります.

### pushできない

- GitHubの招待を承認済みか確認する.
- GitHub Desktopで自分のGitHubアカウントへサインインしているか確認する.
- 他人のパスワードやアクセストークンは使用しない.

## 13. 公開前チェック

Pull Requestを作る前に，次を確認してください.

- [ ] 変更箇所をローカル表示で確認した.
- [ ] 誤字脱字と役職・氏名を確認した.
- [ ] リンクと画像が正常に表示される.
- [ ] 人物写真の掲載許可を確認した.
- [ ] 個人情報と未公開情報が含まれていない.
- [ ] `main`ではなく作業ブランチへcommitした.
- [ ] Pull Requestのbaseが`main`になっている.
