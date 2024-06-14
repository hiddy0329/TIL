# 事象

- Webの請求業務システムを仕事で開発しているが、PDFの請求書を出力する処理にLaravelの「DomPDF」を使用していた。その際に、途中でメモリ消費量が増加した影響で処理が止まってしまい、サーバーがディスクスリープになってしまうという事象が発生。

# 処理概要

- 処理概要としては以下のイメージ。
<img src="https://github.com/hiddy0329/TIL/assets/91509668/21650465-ee94-4906-ac3d-f528f46c2786" width="50%" height="50%">

- 上図の処理の中で、DomPDFを使用して請求データの数だけ繰り返しでPDFデータを生成するという基本的な処理の流れとなる。

# 問題点

- DomPDFは「HTML」によって描画されたデータを「PDF」に変換する処理を実行するが、その際にHTMLの「tableタグ」の記述方法に問題があった。１つのtableタグの中で要素が多く展開され、
結果的に複数ページにまたがるような形になってしまった場合、DomPDFが変換処理で迷ってしまい、速度の低下やメモリの大量消費に繋がってしまっていた。
<img alt="4cea0c0a4363c04372251ca9d227509a" src="https://github.com/hiddy0329/TIL/assets/91509668/3ff97af2-6d3a-449b-8279-1c34de51d15e">

# 解決策

- 複数ページに渡って展開されてしまっていたtableタグの記述方法を見直し、特定の行数になったらtableタグを閉じ、また別のtableタグを形成するように変更した。これによりtableが分割
されるようになり、正常にHTMLからPDFへの変換処理が実行されるようになった。
<img width="901" alt="4191cf3c8a7464624a035a1d45eb5317" src="https://github.com/hiddy0329/TIL/assets/91509668/3ea7eda4-da6f-494e-a2ed-e269048ba7b5">

# 今後の課題

- 今回解決したのはあくまで「**メモリ消費量が増加して処理が途中で止まってしまい、以後進まなくなってしまう**」という点を解決し、処理が最後まで完了するということを実現できたまでに過ぎない。
- そのため、処理速度自体を向上させるようなパフォーマンスの改善はできていない。
- 以後はパフォーマンスの改善を目指して以下のような解決策を試してみる必要がありそうだ。
  - 他の無料ライブラリの検討
  - 生成処理において、複数のチャンクごとの処理に変更し、毎回メモリを解放できるようにする。

# 参考情報
- [Performance suggestions for HTML source](https://github.com/dompdf/dompdf/wiki/Performance)
- [dompdf memory issues](https://stackoverflow.com/questions/2323045/dompdf-memory-issues)
