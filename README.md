# 3D Tilesの生成方法

1. データの取得  
https://www.geospatial.jp/ckan/dataset/road-pointcloud-saitama

2. LASのマージ  
```
pdal pipeline merge-pipeline.json
```

3. LASのメタ情報を表示
```
pdal info --metadata merged.las
```

4. LASの先頭行を確認
```
pdal info -p 0 merged.las
```

5. X座標とY座標を入れ替え
```
pdal pipeline xy_switch_pipeline.json
```

6. 3D Tilesの生成
```
py3dtiles convert --srs_in 6677 --srs_out 4978 --out Syomaru-TN merged_swaped.las
```
