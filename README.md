## 📝 自分向けメモ

秋月白箱（謎SoC基盤）に導入している資材を管理します。

秋月白箱の運用ではDebian導入を前提とする情報が多々ありますが、
本リポジトリ資材はBuidRoot上に[Mackerel](https://mackerel.io/)エージェントおよびGo言語実装のsmartmeter-exporterを追加導入しており、軽量な運用が可能です。

```sh
make akiduki_am3352_defconfig
make menuconfig
make
```

## 🎖️ 先人たちの偉業
[秋月謎SoC基板付きケースの購入～解析とLinux(buildroot,Debian)を動かす](https://honeylab.hatenablog.jp/entry/2023/03/23/152732)

[GitHub - bakueikozo / buildroot_am3352_aki](https://github.com/bakueikozo/buildroot_am3352_aki)　※当初解析をされた神

[GitHub - matsuu / buildroot_am3352_aki](https://github.com/matsuu/buildroot_am3352_aki)　※Mackerelとsmartmeter-exporterを追加導入
（[Xのポスト](https://x.com/matsuu/status/1647407785418825728)）

[秋月謎SoC基板用の buildroot_am3352_aki をカスタマイズしてsshログインしてみる](https://qiita.com/rukihena/items/4bc45330b0589c5cbe15)　※avahi/ssh有効化など

[WI-SUNモジュールと疎通できない？ #1](https://github.com/bakueikozo/buildroot_am3352_aki/issues/1)　※Issue内のWi-SUNモジュール安定化対策をマージ済み

## 🔗 関連資材
[GitHub - mackerelio / mackerel-agent](https://github.com/mackerelio/mackerel-agent)

[GitHub - k1LoW / mackerel-plugin-prometheus-exporter](https://github.com/k1LoW/mackerel-plugin-prometheus-exporter)

[GitHub - WhiteNoise0000 / go-el-controller](https://github.com/WhiteNoise0000/go-el-controller) ※/usr/bin/smartmeter-exporter

## 🛠️ 本リポジトリでの変更箇所
- NTPサーバの向き先を日本国内(NICT/インターネットマルチフィード)へ変更
- ntpd起動前に時刻を強制同期
- Mackerelエージェント設定ファイルに対し、smartmeter-exporter収集設定を追記
- smartmeter-exporterの標準出力をログ出力するよう修正
- smartmeter-exporterのPIDファイルを作成するオプションを追加(stato-stop-daemon -m)
- smartmeter-exporterのSKコマンド発行タイミングを、自宅環境向けに微調整（スキャン完了待機後にSKJOIN）

## ⚠️ 注意 / Notice

このリポジトリは、以下のオリジナルリポジトリを個人利用のためにforkしたものです：

- https://github.com/bakueikozo/buildroot_am3352_aki
- https://github.com/matsuu/buildroot_am3352_aki

元のリポジトリにはライセンス表記が存在しません。  
そのため、このforkは **私的利用（自宅環境での使用）を唯一の目的とし、再配布や第三者向けの公開利用を行う意図は一切ありません**。

---

This repository is a personal fork of the following original project:

- https://github.com/bakueikozo/buildroot_am3352_aki
- https://github.com/matsuu/buildroot_am3352_aki

The original repository does not specify a license.  
Therefore, this fork is intended **strictly for private/home use** and is **not meant for redistribution or public reuse**.

## 元README
Buildroot is a simple, efficient and easy-to-use tool to generate embedded
Linux systems through cross-compilation.

The documentation can be found in docs/manual. You can generate a text
document with 'make manual-text' and read output/docs/manual/manual.text.
Online documentation can be found at http://buildroot.org/docs.html

To build and use the buildroot stuff, do the following:

1) run 'make menuconfig'
2) select the target architecture and the packages you wish to compile
3) run 'make'
4) wait while it compiles
5) find the kernel, bootloader, root filesystem, etc. in output/images

You do not need to be root to build or run buildroot.  Have fun!

Buildroot comes with a basic configuration for a number of boards. Run
'make list-defconfigs' to view the list of provided configurations.

Please feed suggestions, bug reports, insults, and bribes back to the
buildroot mailing list: buildroot@buildroot.org
You can also find us on #buildroot on OFTC IRC.

If you would like to contribute patches, please read
https://buildroot.org/manual.html#submitting-patches
