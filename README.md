# 3D Tilesの生成方法

## データの取得
https://www.geospatial.jp/ckan/dataset/road-pointcloud-saitama

## LASのマージ
pdal pipeline merge-pipeline.json

## LASのメタ情報を表示
pdal info --metadata merged.las

## LASの先頭行を確認
pdal info -p 0 merged.las

## X座標とY座標を入れ替え
pdal pipeline xy_switch_pipeline.json

## 3D Tilesの生成
py3dtiles convert --srs_in 6677 --srs_out 4978 --out Syomaru-TN merged_swaped.las
