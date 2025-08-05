# 軌跡エディタ ユーザーマニュアル

## 概要

軌跡エディタは、自動運転車両の軌跡データ（CSV形式）をグラフィカルに編集できるQt5ベースのツールです。軌跡点の移動、追加、削除、速度編集、およびUndo/Redo機能を提供します。

## 機能一覧

### 基本機能
- 📂 CSVファイルの読み込み・保存
- 🎯 軌跡点の選択・移動（ドラッグ&ドロップ）
- ➕ 軌跡点の追加
- ❌ 軌跡点の削除
- ⚡ 速度編集（単一点・範囲編集）
- ↩️ Undo/Redo機能（最大50回）
- 🔍 ズーム・パン操作
- 🏁 トラック境界線表示

### 表示機能
- 速度に基づく色分け表示（青：低速 → 緑：中速 → 赤：高速）
- 点サイズ・線幅の調整
- 軌跡情報の表示

## 起動方法

```bash
cd /path/to/standalone-trajectory-editor/build
./trajectory_editor
```

## 基本操作

### 1. ファイル操作

#### CSVファイルの読み込み
1. **「Open CSV」**ボタンをクリック
2. 軌跡データファイル（CSV形式）を選択
3. ファイルが正常に読み込まれると軌跡が表示される

**CSVファイル形式:**
```csv
x,y,z,velocity
100.0,200.0,0.0,25.5
101.2,201.1,0.0,26.0
...
```

#### CSVファイルの保存
1. **「Save CSV」**ボタンをクリック
2. 保存先とファイル名を指定
3. 編集した軌跡データが保存される

### 2. 編集モード

#### View Mode（標準モード）
- **目的**: 軌跡点の選択・移動・削除
- **操作**:
  - 左クリック: 点を選択（黄色にハイライト）
  - ドラッグ: 選択した点を移動
  - 右クリック: 点を削除
  - 背景クリック: 選択解除

#### Add Points Mode（追加モード）
- **目的**: 新しい軌跡点の追加
- **操作**:
  - 左クリック: クリック位置に新しい点を追加
  - 点は自動的に適切な位置に挿入される

### 3. 速度編集

#### 単一点の速度編集
1. View Modeで軌跡点を選択
2. **Point Speed**欄で速度値を調整
3. **「Apply」**ボタンをクリックして適用
4. **「Clear」**ボタンで選択解除

#### 範囲速度編集
1. **From**欄に開始点のインデックスを入力
2. **To**欄に終了点のインデックスを入力
3. **Range Speed**欄で設定したい速度を入力
4. **「Apply Range」**ボタンをクリックして範囲適用

### 4. 表示操作

#### ズーム・パン
- **マウスホイール**: ズームイン/アウト
- **Fit All**: 軌跡全体を画面に収める
- **Zoom In/Out**: ボタンによるズーム操作
- **Reset Zoom**: ズームをリセット

#### 表示設定
- **Point Size**: 軌跡点のサイズ調整（1-20）
- **Line Width**: 軌跡線の太さ調整（1-10）
- **Show Track Boundaries**: トラック境界線の表示/非表示

### 5. 編集履歴

#### Undo/Redo機能
- **「Undo」**: 直前の編集操作を取り消し
- **「Redo」**: 取り消した操作をやり直し
- 最大50回まで履歴を保持
- ボタンにカーソルを当てると操作内容を表示

## キーボードショートカット

| 操作 | ショートカット |
|------|----------------|
| ファイルを開く | Ctrl+O |
| ファイルを保存 | Ctrl+S |
| Undo | Ctrl+Z |
| Redo | Ctrl+Y |
| ズームイン | Ctrl++ |
| ズームアウト | Ctrl+- |

## 色分け表示

軌跡点は速度に応じて色分けされます：

- 🔵 **青色**: 低速（デフォルト: 0-20 km/h）
- 🟢 **緑色**: 中速（デフォルト: 20-40 km/h）
- 🔴 **赤色**: 高速（デフォルト: 40+ km/h）

## トラブルシューティング

### よくある問題

#### Q: 軌跡点を移動できない
**A**: 以下を確認してください：
- View Modeが選択されているか
- 軌跡点の近く（15ピクセル以内）をクリックしているか
- CSVファイルが正しく読み込まれているか

#### Q: CSVファイルが読み込めない
**A**: 以下を確認してください：
- ファイル形式が正しいか（x,y,z,velocity列が必要）
- ファイルパスに日本語が含まれていないか
- ファイルの読み取り権限があるか

#### Q: Undo/Redoが効かない
**A**: 
- 編集操作を行った後でないとUndo/Redoボタンは有効になりません
- 最大50回まで履歴を保持します

#### Q: 速度編集が反映されない
**A**: 
- 軌跡点が選択されているか確認
- 「Apply」ボタンをクリックしているか確認
- 範囲編集では開始・終了インデックスが正しいか確認

## ファイル形式仕様

### 入力CSVファイル
```csv
x,y,z,velocity
# x: X座標（メートル）
# y: Y座標（メートル）  
# z: Z座標（メートル、通常は0.0）
# velocity: 速度（km/h）
```

### 例
```csv
x,y,z,velocity
3725.71,-124.15,0.0,20.0
3725.85,-123.05,0.0,22.5
3726.12,-121.98,0.0,25.0
```

## システム要件

- **OS**: Linux/Windows/macOS
- **Qt**: 5.12以上
- **C++**: C++17対応コンパイラ
- **メモリ**: 最小512MB

## バージョン情報

- **バージョン**: 1.0.0
- **ビルド日**: 2025年1月
- **ライセンス**: MIT License

## サポート

技術的な問題や質問については、プロジェクトのGitHubリポジトリにIssueを作成してください。

---

*このマニュアルは軌跡エディタ v1.0.0 用です。*



Trajectory Editor User Manual
Overview

The Trajectory Editor is a Qt5-based tool for graphically editing autonomous vehicle trajectory data (CSV format). It provides the ability to move, add, and delete trajectory points, edit speed, and undo/redo functions.
List of Features
Basic Features

📂 Loading and Saving CSV Files
🎯 Selecting and Moving Trajectory Points (Drag & Drop)
➕ Adding Trajectory Points
❌ Deleting Trajectory Points
⚡ Speed Editing (Single Point/Range Editing)
↩️ Undo/Redo Function (Up to 50 Times)
🔍 Zooming and Panning
🏁 Track Boundary Display

Display Features

Color-Coded Display Based on Speed (Blue: Slow → Green: Medium → Red: Fast)
Adjusting Point Size and Line Width
Displaying Trajectory Information

Starting

cd /path/to/standalone-trajectory-editor/build
./trajectory_editor

Basic Operations
1. File Operations
Loading CSV Files

Click the "Open CSV" button
Select a trajectory data file (CSV format)
The trajectory will be displayed if the file is loaded successfully.

CSV file format:

x,y,z,velocity
100.0,200.0,0.0,25.5
101.2,201.1,0.0,26.0
...

Saving a CSV file

Click the "Save CSV" button.
Specify the save location and file name.
The edited trajectory data will be saved.

2. Editing Mode
View Mode (Standard Mode)

Purpose: Select, move, or delete trajectory points.
Operations:
Left-click: Select a point (highlighted in yellow).
Drag: Move the selected point.
Right-click: Delete a point.
Click on the background: Deselect.

Add Points Mode (Add Mode)

Purpose: Add a new trajectory point.
Operations:
Left-click: Add a new point at the clicked location.
The point will automatically be inserted in the appropriate position.

3. Speed Editing
Single-Point Speed Editing

Select a trajectory point in View Mode.
Adjust the speed value in the Point Speed field. Click the "Apply" button to apply.
Click the "Clear" button to deselect.

Range Speed Editing

Enter the starting index in the From field.
Enter the ending index in the To field.
Enter the desired speed in the Range Speed field.
Click the "Apply Range" button to apply the range.

4. Display Controls
Zoom/Pan

Mouse Wheel: Zoom in/out
Fit All: Fit the entire track to the screen
Zoom In/Out: Zoom using the buttons
Reset Zoom: Reset the zoom

Display Settings

Point Size: Adjusts the size of the track points (1-20)
Line Width: Adjusts the thickness of the track lines (1-10)
Show Track Boundaries: Show/hide track boundaries

5. Edit History
Undo/Redo Function

"Undo": Undo the most recent edit
"Redo": Redo an undone operation
Up to 50 edit history entries are maintained
Hover over the button to display the operation details

Keyboard Shortcuts
Operation Shortcuts
Open File Ctrl+O
Save File Ctrl+S
Undo Ctrl+Z
Redo Ctrl+Y
Zoom In Ctrl++
Zoom Out Ctrl+-
Color-Coded Display

Trajectory points are color-coded according to speed:

🔵 Blue: Slow Speed (Default: 0-20 km/h)
🟢 Green: Medium Speed (Default: 20-40 km/h)
🔴 Red: Fast Speed (Default: 40+ km/h)

Troubleshooting
Common Issues
Q: I can't move a trail point

A: Please check the following:

Whether the View Mode is selected
Whether you clicked close to the trail point (within 15 pixels)
Whether the CSV file was loaded correctly

Q: I can't load a CSV file

A: Please check the following:

Whether the file format is correct (x, y, z, and velocity columns are required)
Whether the file path contains Japanese characters
Whether you have read permission for the file

Q: Undo/Redo doesn't work

A:

The Undo/Redo buttons are only enabled after an edit operation has been performed.
A history is maintained for up to 50 edits.

Q: Speed edits aren't reflected.

A:

Make sure a track point is selected.
Make sure you clicked the "Apply" button.
For range edits, make sure the start and end indices are correct.

File Format Specifications
Input CSV File

x,y,z,velocity
# x: X coordinate (meters)
# y: Y coordinate (meters)
# z: Z coordinate (meters, usually 0.0)
# velocity: Speed (km/h)

Example

x,y,z,velocity
3725.71,-124.15,0.0,20.0
3725.85,-123.05,0.0,22.5
3726.12,-121.98,0.0,25.0

System Requirements

OS: Linux/Windows/macOS
Qt: 5.12 or higher
C++: C++17-compatible compiler
Memory: Minimum 512MB

Version Information

Version: 1.0.0
Build Date: January 2025
License: MIT License

Support
For technical issues or questions, please create an issue in the project's GitHub repository.


