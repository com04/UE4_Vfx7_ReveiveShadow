# UE4_Vfx7_ReveiveShadow

- 第7回VFX技術者交流会で講演しました「UE4でTranslucencyやUnlitに影を落としたい！」のサンプルプロジェクトになります
https://atnd.org/events/101394

- スライド
https://www.slideshare.net/com044/ue4translucencyunlit

- ※必要に応じてライトビルドしてください


## レベル
- 各項目ごとにディレクトリで分けています

### スライド「UE4のおさらい - Translucecnyについて」P.16～
/Vfx7_ReceiveShadow/SampleLevel/0_UE4/LV_UE4
- Forward Shading (P.17～)
- Lighting Volume (P.27～)
- Self Shadow (P.37～)

### Unlitフェイク実装 P.45～
/Vfx7_ReceiveShadow/SampleLevel/1_UnlitFakeShadow/LV_1_UnlitFakeShadow
- 真ん中から右側で確認出来ます
マテリアルはDefaultLitです
- 陰影が付いているように見えるのは、自身が落とす影になります
メッシュを選択して、「Cast Shadow」をOFFにして頂くと陰影が無いのを確認出来ます
- 法線を操作出来ないTranslucency（パーティクル）には適用できていません

### Component単位での簡易的な影 P.68～
/Vfx7_ReceiveShadow/SampleLevel/1_UnlitFakeShadow/LV_1_UnlitFakeShadow
- 「シミュレート」再生等でプレイして確認してください
- コンポーネント「BPC_ComponentShadow」をActorに追加しています
このコンポーネントをアタッチして使います

### DistanceFieldを用いた影 P.83～
/Vfx7_ReceiveShadow/SampleLevel/3_DistanceFieldShadow/LV_3_DistanceFieldShadow
- マテリアルでの処理は「MF_DistanceFieldShadow」で行っています
- 現状、スフィア辺りを見ると若干アーティファクトが出ています

### ShadowMapでの影 P.128～
/Vfx7_ReceiveShadow/SampleLevel/4_ShadowMapShadow/LV_4_ShadowMapShadow
- 「シミュレート」再生等でプレイして確認してください
- 「BP_ShadowMapShadow」をシーンに配置しています
このBPでシャドウマップの生成を行っています
- マテリアルでの処理は「MF_ShadowMapShadow」で行っています
-- MF_ShadowMapShadowの「OrthoWidth」: BP_ShadowMapShadowのSceneCaptureComponent2D - OrthoWidth
-- MF_ShadowMapShadowの「ShadowMapYAxisMultiplier」: BP_ShadowMapShadowのSceneCaptureComponent2D - TextureTargetに設定されているテクスチャのアスペクト比



