# Geo Narrator アーキテクチャドキュメント

## コンポーネント設計方針

本プロジェクトでは、Atomic Design をベースにコンポーネント設計を行う。  
開発の進行に伴う設計ブレを防ぐため、各レイヤーの定義を以下に明確に定義する。

### Atoms（原子）

- 最小単位のコンポーネント。
- 単体で意味が成立するものを Atom と定義する。
  - 例：Button, Input, Label, Icon など。
- 内部に複数要素を内包していても、単独で役割が完結していれば Atom とする。

### Molecules（分子）

- 複数の Atoms を組み合わせることで初めて意味を持つ小さな構造体。
- 単体では意味が成立しないものを Molecule と定義する。
  - 例：Input と Button を組み合わせた検索フォーム、リストの 1 アイテムなど。

### Organisms（有機体）

- 複数の Atoms および Molecules を組み合わせた大きな UI ブロック。
- 明確な機能単位（例：地図表示、観光地リスト、詳細情報表示など）を担う。

### Templates（テンプレート）

- ページレイアウトの構造のみを定義する。
- 本プロジェクトでは現状 Templates 層は必須とはしない。

### Pages（ページ）

- 実際にデータを流し込み、最終的な画面を構成する。
- データ取得とコンポーネント組み立ての責任を持つ。

---

## データ取得設計方針

- API 通信はすべて専用の hooks に集約して管理する。
- Pages は hooks を呼び出して、コンポーネントにデータを渡すだけに徹する。
- Components（Atoms, Molecules, Organisms）は、渡されたデータを受け取って表示に専念する。

### Hooks 層の役割

- OpenTripMap API、REST Countries API など外部データの取得を行う。
- 非同期通信、エラーハンドリング、データ整形を担当する。

### Pages 層の役割

- 必要なデータを hooks から取得する。
- 状態管理（useState 等）を行い、Organisms 以下のコンポーネントに適切にデータを渡す。

---

## フォルダ構成方針

```plaintext
src/
├── components/
│   ├── atoms/
│   ├── molecules/
│   ├── organisms/
├── hooks/
│   ├── useFetchPlaces.ts
│   ├── useFetchPlaceDetail.ts
├── pages/
│   ├── TopPage.tsx
├── types/
│   ├── place.ts
├── utils/
│   ├── apiClient.ts
├── assets/
│   ├── images/
│   ├── styles/
```
