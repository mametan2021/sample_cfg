PREFERRED_PROVIDER を指定する際は、以下の点に注意する必要があります:

1. スペルミスがないか確認してください。正しいスペルは "PREFERRED_PROVIDER" です。あなたの質問文では "PREFFERRED" と "PREFFERED" という2つの異なるスペルミスがありました。

2. 変数名の形式は以下のようにするのが正しいです:

   ```
   PREFERRED_PROVIDER_virtual/libxrandr = "レシピ名"
   ```

   または

   ```
   PREFERRED_PROVIDER:virtual/libxrandr = "レシピ名"
   ```

3. コロン (:) を使用する構文は、Yocto Project の新しいバージョン（3.1 "dunfell" 以降）で導入されたオーバーライド構文です[2]。古いバージョンを使用している場合は、アンダースコア (_) を使用する必要があります。

4. libxrandrは通常、仮想プロバイダ（virtual/libxrandr）として扱われるため、"virtual/" プレフィックスを付ける必要があります。

5. この設定は正しい場所に記述する必要があります。通常は local.conf ファイルか、カスタムレイヤーの conf/layer.conf ファイルに記述します。

したがって、推奨される記述方法は以下のいずれかです：

```
PREFERRED_PROVIDER_virtual/libxrandr = "libxrandr"
```

または（新しいバージョンの Yocto Project を使用している場合）

```
PREFERRED_PROVIDER:virtual/libxrandr = "libxrandr"
```

これらの点を確認し、それでも効果がない場合は、ビルド環境のクリーンアップ（`bitbake -c cleanall virtual/libxrandr`）を行ってから再ビルドしてみてください。また、bitbake の詳細なログを確認して、実際にどのプロバイダが選択されているかを確認することも有効です。

Citations:
[1] https://mickey-happygolucky.hatenablog.com/entry/2015/06/28/004605
[2] https://qiita.com/AngryMane/items/61d2fa47246a9f9217f5
[3] https://mickey-happygolucky.hatenablog.com/entry/2023/02/17/211258
[4] https://www.paltek.co.jp/techblog/techinfo/240626_01
[5] https://qiita.com/rg125_suzuki/items/702e90084e12e0fdf6de
