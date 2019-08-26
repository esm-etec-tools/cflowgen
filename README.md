# CFlowGen(コントロールフロー生成)
## 概要
AUTOSAR R4.2.2のarxmlファイルを読み込み，コントロールフローをDOT言語で出力します．  
DOT言語はGraphvizで図に変換してください．  
※DOT言語はグラフをテキスト形式で表現するための言語です

## コントロールフロー対象
* OSタスクからのExecutableEntity呼び出し
* ExecutableEntityからのRTE API呼び出し
* RTE APIからのExecutableEntityの直接関数呼び出し(Rte_CallからのServerRunnable呼び出し)
* ※マルチインスタンス未対応

## V0.1.0で対応済みのRTE API
* Rte_Write/Rte_Read(S/R DataSemantics)
* Rte_Call(C/S)

## 実行環境設定
* Java環境設定(Java8以降)  
 Javaの実行環境をインストールし，PATHを通すか，bin/cflowgen.bat内のjava.exeをフルパスに変更してください．
* 必要なファイルの設定  
 AUTOSARのサイト(https://www.autosar.org/) から下記のzipファイルをダウンロードし，指定ファイルをschemaフォルダにコピーしてください．
* ダウンロードするファイル  
    * Methodology-and-Templates_Templates.zip (CATEGORIES: 4.2 (CP), CLASSIC PLATFORM)
* schemaフォルダにコピーするファイル  
    * AUTOSAR_4-2-2.xsd
    * xml.xsd
* Graphvizインストール  
 http://www.graphviz.org/

## ツールの使い方
* コマンドプロンプトでcflowgen.batを実行してください．  
`$ cflowgen.bat <arxml file1> [<armxl file2> [<armxl file3>] ...] [-o <file>]`
    * -o <file>
     生成するdotファイルを指定します．未指定の場合，cflow.dotとなります．
* コマンドプロンプトでdot.exeを実行してください．  
`$ dot -Tsvg <dot file> > <SVG file>`  
 ※図が大きくなるため，SVG形式がおすすめです．検索も可能です．
* 実行例
    ```
    $ cflowgen.bat *.arxml  
    $ dot -Tsvg cflow.dot > cflow.svg
    ```

## 免責事項
自由にご利用いただけますが，本ソフトウェアの利用に伴ういかなる場合においても，著作権者は一切責任を負いません．

Copyright (C) 2019 ESM, Inc. All rights reserved.
