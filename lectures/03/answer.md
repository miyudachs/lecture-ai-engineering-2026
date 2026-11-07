# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：glossary.jsonファイルを参照し、その内容と合致した回答になった
- `--trace` で見えたツール呼び出し（ツール名と引数）：
    [tool call]   search_glossary({'query': 'LoRA'})
    [tool call]   search_glossary({'query': 'QLoRA'})

- 1つの質問での LLM 呼び出し回数（`requests`）：requests=2

- 追加したツールと、docstring に書いた説明：
    [tool return] search_glossary -> [{"term": "LoRA", "lecture": 2, "definition": "事前学習済みの重みは固定したまま、重みの更新分を2つの小さな行列の積（低ランク行列）で表し、その小さな行列だけを学習するPEFT手法。学習するパラ…
    [tool return] search_glossary -> [{"term": "QLoRA", "lecture": 2, "definition": "ベースモデルの重みを4ビットなどに量子化してメモリを節約したうえで、LoRAで学習する手法。より大きなモデルを小さなGPUで扱える。本講座の第2…

## 宿題

- 取り組んだレベル：実装 
- やったこと：save_learning_logを作成し、requires_approval=trueで登録した。output_typeにDeferredToolRequestsを追加した。
- 結果：Pytestの結果は17Passedだった
- 気づき・疑問：今のCLIにはDeferredToolRequestsを受け取って利用者に確認して、承認結果を渡して処理を再開する処理がないため、CLIでのお承認・再開までは検証できなかった。
