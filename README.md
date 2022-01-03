# OpenPose_macOS_environment-setup
macOSにOpenPoseを環境構築する方法を記載。ターミナルで各コードを上から1行ずつ入力。

## 1) Homebrew/wget swig/Xquartzインストール
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew install wget swig

brew install --cask xquartz

## 2) reboot

## 3) anaconda仮想環境作成(python3.6)
例：conda create -n pose python=3.6　*"pose"の部分を任意の名前に変更する

## 4) git clone *poseフォルダがある場合は不要
cd ~/Desktop

mkdir pose

cd pose

git clone https://github.com/jiajunhua/ildoonet-tf-pose-estimation

cd ildoonet-tf-pose-estimation

## 5) viエディタで編集 *poseフォルダがある場合は不要
requirements.txtの2行目dillの右に ==0.2.7.1 を書き足す。

## 6) 各種モジュールインストール
pip install -r requirements.txt

## 7) TensorFlow インストール
pip install tensorflow==1.14

## 8) OpneCV インストール
pip install opencv-python==3.4.0.14

## 9) 必須ファイルインストール
cd models/graph/cmu

bash download.sh

## 10) pafprocessをbuild
cd ../../../tf_pose/pafprocess
swig -python -c++ pafprocess.i && python3 setup.py build_ext --inplace
