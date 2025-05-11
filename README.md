# Geo Narrator

Geo Narrator は、緯度・経度を起点にその土地の基本情報と観光地情報を取得し、  
音声生成ツールに投入できる紹介文（テキスト）を生成する Web アプリです。

## 技術スタック

- TypeScript
- React
- Vite
- ESLint
- Prettier
- Husky
- Storybook

## 機能概要

- 都市名から緯度・経度を検索
- 世界地図をクリックして緯度・経度を取得
- 指定した緯度・経度から周辺の観光地リストを取得
- 選択した観光地の詳細情報（説明文、画像）を取得
- 取得した情報を元に、音声用テキストを生成

## 画面
- 観光地探索画面
- 編集画面

## 使用する API

- [REST Countries API](https://restcountries.com/)  
  → 国の基本情報（国旗・人口・通貨など）を取得

- [OpenTripMap API](https://opentripmap.io/)  
  → 観光地リストと各観光地の詳細情報を取得

- [Nominatim API (OpenStreetMap)](https://nominatim.org/)  
  → 都市名から緯度・経度を取得

## アプリデザイン
https://www.figma.com/design/bWdstosdzL6UfuvgPOZtKO/GeoNarrator?node-id=0-1&t=Xy42lFOiAHVK18tS-1