# kgrid40

40% (4x10) Grid Layout 一体型カスタムキーボードプロジェクト。

## 1. プロジェクトの経緯
本リポジトリは、
2026年3月23日に名称の完全統一と物理基板（PCB）との整合性確認を完了。
**2026年3月26日、実機（SuperMini nRF52840）への書き込み、
**Bluetooth接続、および全40キーのマトリックス導通テストを完了し、ハードウェア・ソフトウェアの両面で動作を実証しました。**

## 2. ハードウェア仕様
実機の回路図および物理配線に基づいた確定済みのピン割り当てです。

### ターゲットボード
* ターゲットボード: SuperMini nRF52840 (nice!nano 互換)
* **ZMKビルド構成**: nice_nano をベースに使用
* ピンアサイン: kgrid40.dtsi にて GPIO ポート (P0.xx, P1.xx) を直接定義。
* SuperMini 本体のシルク印刷（物理表示）に基づいた物理ピン配置に完全対応済み。

### マトリックス配線 (4行 × 10列)
PCB上の穴番号と、SuperMiniのGPIOポート（P0.xx / P1.xx）を1対1で対応させています。

| 役割 | PCB穴番号 | GPIOポート (ZMK) | 備考 |
| :--- | :--- | :--- | :--- |
| **Rows** | 5, 6, 7, 8 | `P0.17, P0.20, P0.22, P0.24` | ROW 0〜3 |
| **Cols (左)** | 9, 10, 11, 12 | `P1.00, P0.11, P1.04, P1.06` | COL 0〜3 |
| **Cols (右)** | 17, 18, 19 | `P0.29, P0.02, P1.15` | COL 4〜6 |
| **Cols (右)** | 20, 21, 22 | `P1.13, P1.11, P0.10` | COL 7〜9 |

### 物理・論理構成（実証済み）
* **ダイオード方向**: `col2row`
* **スキャン論理**: **Active High / Pull Down** (実機での安定動作を確認)
* **接続**: Bluetooth  (Macmini接続確認済み) / USB-C

## 3. ソフトウェア構成
* **Firmware**: ZMK Firmware (stable)
* **GUI Editor**: [Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) 対応済み

## 4. 修正履歴



### 2026-03-23: ピンアサインの正常化と重複排除
* **資産名称の同期**: フォルダ名、シールド定義、UF2出力名をすべて `kgrid40` に統一。

## 5. 現在のステータス
* [x] 独立リポジトリへの移行と名称統一
* [x] GPIOピンアサインの重複排除と物理整合性確認
* [x] GitHub Actions による UF2 直接出力の確認
* [x] Keymap Editor でのレイアウト認識確認
* [x] 実機への書き込みと導通テスト完了
* [x] Bluetooth接続およびレイヤー動作確認


## 6. メモ
* **トラブルシューティング**: Bluetooth接続が不安定な場合や、特定の行が反応しない場合は、`settings_reset.uf2` でプロファイルをクリアすること。


## MIT License

This project is licensed under the MIT License.
