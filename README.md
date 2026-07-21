# marutyan/.github

このリポジトリは、`marutyan`個人アカウント配下のリポジトリへ、既定のIssue・Pull Requestテンプレートを提供するdefault community health repositoryである。

## 経緯

設立当初はClaude Codeが主にGitHub操作を担当していたため、ローカルのClaude Code用Rulesを運用規則の正本とし、このリポジトリを表示用テンプレートの配布先としていた。

現在はCodexとClaude Codeの両方がGitHub操作を担当する。特定のAIやローカルパスへ依存しないよう、表示形式、AI実行手順、ツール固有設定の責務を分離している。

## SSoTと責務

- このリポジトリのmerge済みdefault branch: GitHub上に表示されるIssue・PR形式のSSoT。
- private dotfilesの共通`github-ops` Skill: Issue確認、branch、commit、PR、検証、review、merge gateなど、AI実行手順のSSoT。
- Codex・Claude Code別のRules・設定: Skill discovery、Hooks、permissions、sandboxなど、各ツール固有機能のadapter。

テンプレート全文をAI側のRulesやSkillへコピーしない。AIは作業時に対象リポジトリへ実際に適用されるテンプレートを確認する。

## 適用優先順位

### Issue

1. 対象リポジトリにIssue TemplateまたはIssue Formが一つでもある場合、そのリポジトリ固有のtemplate set。
2. 対象リポジトリにIssue TemplateもIssue Formもない場合、このリポジトリのmerge済みtemplate set。
3. GitHub上で適用されるtemplate setを取得できない、または選択肢に必要な形式がない場合のみ、AI実行手順が定める最小fallback。

GitHubは対象リポジトリにIssue template setがあると、このリポジトリのdefault Issue templatesを個別種類ごとには補完しない。例えば対象側にChangeだけがありBugがない場合、共通Bug templateを混在させず最小fallbackを使う。

### Pull Request

1. 対象リポジトリ固有のPR Template。
2. 対象リポジトリにPR Templateがない場合、このリポジトリのmerge済みPR Template。
3. どちらも取得できない場合のみ、AI実行手順が定める最小fallback。

対象リポジトリ固有の形式を、このリポジトリの共通形式で上書きしない。

## Badge labels

- Issue・PR全体の優先度は`P0`、`P1`、`P2`のいずれか1つで示す。
- Issue種別は`bug`、`change`、`investigation`、`experiment`で示す。
- 本文中の個別項目は`🔴🟡🟢⚪`でtriageし、GitHub labelとは区別する。

default community health repositoryのlabel実体は対象リポジトリへ継承されない。templateの
`labels`指定が自動適用されるには、対象リポジトリに同名labelが必要である。AIは存在を確認し、
存在しないlabelを付与済みとして報告しない。

## 更新手順

1. 変更対象と成果をIssueで定義する。
2. 表示形式の変更は、このリポジトリのテンプレートを更新する。
3. GitHub操作の判断規則も変わる場合だけ、private dotfilesの共通`github-ops` Skillを別成果として更新する。
4. CodexとClaude Codeへ同じdry runを与え、template選択、追跡性、検証の誠実性を確認する。
5. 各PRはユーザーの明示指示までmergeしない。

default community health filesを利用するため、このリポジトリはpublicで維持する。公開ファイルへ秘密情報、認証情報、privateな環境詳細を含めない。
