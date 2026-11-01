# DrawLess player CPU profile

Result: **complete**; mode: **stages**; sampled frames: 246 / observed: 4912.

Environment: `framebuffer=1920x1129; vsync=false; fpsLimit=260; camera=FIRST_PERSON; renderDistance=7; fov=110; resourcePacks=[vanilla, file/resources.zip]`

CPU timing includes profiling overhead. Percentages describe measured scopes, not a predicted FPS gain.

Coverage: `scene-stages-and-player-name-tags`; schema: 2. World, terrain, frame-pass and GUI scopes cover the whole scene. Player name-tag layout/glyph scopes are attributed separately; mixed draws remain shared.


## Largest self-time scopes

| Stage | Self ms / sampled frame |
| --- | ---: |
| frame/scene_extract/world_extract/entities_extract | 0.49874 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 0.38331 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 0.29034 |
| frame/presentation_cpu_wait | 0.22310 |
| frame/scene_extract/world_extract/particles_extract | 0.18525 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 0.15761 |
| frame/scene_render/gui_render/gui_draw_cpu | 0.10984 |
| frame/scene_extract/gui_extract/hud_extract | 0.10780 |
| frame/scene_extract/world_extract/block_entities_extract | 0.10520 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.10116 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 0.09220 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 0.08699 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 0.08088 |
| frame/scene_render | 0.07780 |
| frame/scene_render/world_view/world_render/feature_frame_prepare | 0.07399 |

## Complete timing tree

| Stage (nested path) | Calls | Inclusive ms | Self ms | ms / sampled frame | % renderFrame | % frame interval |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| frame | 246 | 1003.82620 | 16.03480 | 4.08059 | 100.00000 | 93.14167 |
| frame/surface_acquire_cpu | 246 | 0.04250 | 0.04250 | 0.00017 | 0.00423 | 0.00394 |
| frame/scene_extract | 246 | 243.52860 | 0.88770 | 0.98995 | 24.26004 | 22.59620 |
| frame/scene_extract/window_extract | 246 | 0.02600 | 0.02600 | 0.00011 | 0.00259 | 0.00241 |
| frame/scene_extract/options_extract | 246 | 0.09010 | 0.09010 | 0.00037 | 0.00898 | 0.00836 |
| frame/scene_extract/lightmap_extract | 246 | 0.12570 | 0.12570 | 0.00051 | 0.01252 | 0.01166 |
| frame/scene_extract/camera_extract | 246 | 2.02610 | 2.02610 | 0.00824 | 0.20184 | 0.18800 |
| frame/scene_extract/world_extract | 246 | 206.70660 | 5.30700 | 0.84027 | 20.59187 | 19.17961 |
| frame/scene_extract/world_extract/entities_extract | 246 | 129.72000 | 122.68970 | 0.52732 | 12.92256 | 12.03628 |
| frame/scene_extract/world_extract/entities_extract/player_extract | 1349 | 7.03030 | 7.03030 | 0.02858 | 0.70035 | 0.65232 |
| frame/scene_extract/world_extract/block_entities_extract | 246 | 25.87940 | 25.87940 | 0.10520 | 2.57808 | 2.40126 |
| frame/scene_extract/world_extract/block_outline_extract | 246 | 0.04740 | 0.04740 | 0.00019 | 0.00472 | 0.00440 |
| frame/scene_extract/world_extract/block_damage_extract | 246 | 0.02150 | 0.02150 | 0.00009 | 0.00214 | 0.00199 |
| frame/scene_extract/world_extract/particles_extract | 246 | 45.57050 | 45.57050 | 0.18525 | 4.53968 | 4.22833 |
| frame/scene_extract/world_extract/gizmos_extract | 246 | 0.16080 | 0.16080 | 0.00065 | 0.01602 | 0.01492 |
| frame/scene_extract/gui_extract | 246 | 33.66640 | 0.66900 | 0.13686 | 3.35381 | 3.12379 |
| frame/scene_extract/gui_extract/hud_extract | 246 | 32.93450 | 26.51770 | 0.13388 | 3.28090 | 3.05588 |
| frame/scene_extract/gui_extract/hud_extract/scoreboard_extract | 246 | 0.10440 | 0.10440 | 0.00042 | 0.01040 | 0.00969 |
| frame/scene_extract/gui_extract/hud_extract/chat_extract | 246 | 6.26380 | 6.26380 | 0.02546 | 0.62399 | 0.58120 |
| frame/scene_extract/gui_extract/hud_extract/tab_list_extract | 246 | 0.04860 | 0.04860 | 0.00020 | 0.00484 | 0.00451 |
| frame/scene_extract/gui_extract/debug_overlay_extract | 246 | 0.06290 | 0.06290 | 0.00026 | 0.00627 | 0.00584 |
| frame/pending_render_tasks_cpu | 246 | 0.02230 | 0.02230 | 0.00009 | 0.00222 | 0.00207 |
| frame/scene_render | 246 | 684.05620 | 19.13760 | 2.78072 | 68.14488 | 63.47129 |
| frame/scene_render/lightmap_render_cpu | 246 | 0.82990 | 0.82990 | 0.00337 | 0.08267 | 0.07700 |
| frame/scene_render/world_view | 246 | 564.71450 | 8.53160 | 2.29559 | 56.25620 | 52.39797 |
| frame/scene_render/world_view/world_render | 246 | 532.88480 | 1.82800 | 2.16620 | 53.08536 | 49.44460 |
| frame/scene_render/world_view/world_render/world_feature_submit | 246 | 69.55510 | 1.14470 | 0.28274 | 6.92900 | 6.45379 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 246 | 48.49410 | 16.12500 | 0.19713 | 4.83093 | 4.49961 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit | 1349 | 32.36910 | 10.61190 | 0.13158 | 3.22457 | 3.00342 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/HumanoidArmorLayer | 1349 | 10.66920 | 10.66920 | 0.04337 | 1.06285 | 0.98996 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/PlayerItemInHandLayer | 1349 | 3.90530 | 3.90530 | 0.01588 | 0.38904 | 0.36236 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ArrowLayer | 1349 | 0.32400 | 0.32400 | 0.00132 | 0.03228 | 0.03006 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/Deadmau5EarsLayer | 1349 | 0.28790 | 0.28790 | 0.00117 | 0.02868 | 0.02671 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CapeLayer | 1349 | 0.44430 | 0.44430 | 0.00181 | 0.04426 | 0.04123 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CustomHeadLayer | 1349 | 1.42120 | 1.42120 | 0.00578 | 0.14158 | 0.13187 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/WingsLayer | 1349 | 0.62670 | 0.62670 | 0.00255 | 0.06243 | 0.05815 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ParrotOnShoulderLayer | 1349 | 0.27130 | 0.27130 | 0.00110 | 0.02703 | 0.02517 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/SpinAttackEffectLayer | 1349 | 0.23350 | 0.23350 | 0.00095 | 0.02326 | 0.02167 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/BeeStingerLayer | 1349 | 0.31180 | 0.31180 | 0.00127 | 0.03106 | 0.02893 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/player_name_tag_submit | 1349 | 3.26200 | 3.26200 | 0.01326 | 0.32496 | 0.30267 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 246 | 19.89560 | 19.89560 | 0.08088 | 1.98198 | 1.84605 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_damage_submit | 246 | 0.01180 | 0.01180 | 0.00005 | 0.00118 | 0.00109 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_outline_submit | 246 | 0.00890 | 0.00890 | 0.00004 | 0.00089 | 0.00083 |
| frame/scene_render/world_view/world_render/feature_frame_prepare | 246 | 121.05720 | 18.20240 | 0.49210 | 12.05958 | 11.23249 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ShadowFeatureRenderer/prepare | 246 | 2.80290 | 2.80290 | 0.01139 | 0.27922 | 0.26007 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/CustomFeatureRenderer/prepare | 246 | 0.89780 | 0.89780 | 0.00365 | 0.08944 | 0.08330 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 492 | 19.96290 | 17.81630 | 0.08115 | 1.98868 | 1.85229 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material | 254 | 2.14660 | 0.73590 | 0.00873 | 0.21384 | 0.19918 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer | 254 | 0.46170 | 0.24690 | 0.00188 | 0.04599 | 0.04284 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer/material_match | 254 | 0.21480 | 0.21480 | 0.00087 | 0.02140 | 0.01993 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/setup_animation | 254 | 0.38660 | 0.38660 | 0.00157 | 0.03851 | 0.03587 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/geometry_encode | 254 | 0.56240 | 0.56240 | 0.00229 | 0.05603 | 0.05218 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/TextFeatureRenderer/prepare | 492 | 8.31380 | 8.31380 | 0.03380 | 0.82821 | 0.77141 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 492 | 22.96470 | 22.68010 | 0.09335 | 2.28772 | 2.13082 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare | 492 | 26.51200 | 16.58880 | 0.10777 | 2.64109 | 2.45996 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/text_prepare | 2686 | 6.20460 | 6.20460 | 0.02522 | 0.61810 | 0.57570 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/glyph_encode | 2686 | 3.71860 | 3.71860 | 0.01512 | 0.37044 | 0.34504 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 246 | 21.40070 | 21.40070 | 0.08699 | 2.13191 | 1.98570 |
| frame/scene_render/world_view/world_render/terrain_prepare | 246 | 0.05450 | 0.05450 | 0.00022 | 0.00543 | 0.00506 |
| frame/scene_render/world_view/world_render/frame_graph_cpu | 246 | 339.09760 | 2.77280 | 1.37845 | 33.78051 | 31.46373 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clear | 246 | 10.22570 | 10.22570 | 0.04157 | 1.01867 | 0.94881 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 246 | 38.77270 | 38.77270 | 0.15761 | 3.86249 | 3.59759 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 246 | 272.19470 | 94.29540 | 1.10648 | 27.11572 | 25.25604 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 492 | 71.42470 | 71.42470 | 0.29034 | 7.11525 | 6.62726 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid | 246 | 41.23080 | 7.40360 | 0.16760 | 4.10736 | 3.82567 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 246 | 8.36200 | 0.28030 | 0.03399 | 0.83301 | 0.77588 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 8.08170 | 8.08170 | 0.03285 | 0.80509 | 0.74987 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed | 246 | 25.46520 | 0.57960 | 0.10352 | 2.53681 | 2.36283 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 992 | 24.88560 | 24.88560 | 0.10116 | 2.47907 | 2.30905 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent | 246 | 57.40360 | 2.60690 | 0.23335 | 5.71848 | 5.32629 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed | 246 | 8.46260 | 0.20740 | 0.03440 | 0.84303 | 0.78522 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 8.25520 | 8.25520 | 0.03356 | 0.82237 | 0.76597 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 246 | 6.90200 | 0.20260 | 0.02806 | 0.68757 | 0.64041 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 6.69940 | 6.69940 | 0.02723 | 0.66739 | 0.62161 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed | 492 | 12.82320 | 0.32450 | 0.05213 | 1.27743 | 1.18982 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed/draw_cpu/mixed | 492 | 12.49870 | 12.49870 | 0.05081 | 1.24511 | 1.15971 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed | 492 | 6.79820 | 0.24930 | 0.02763 | 0.67723 | 0.63078 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed | 246 | 6.67700 | 0.14640 | 0.02714 | 0.66515 | 0.61954 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 6.53060 | 6.53060 | 0.02655 | 0.65057 | 0.60595 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 6.54890 | 6.54890 | 0.02662 | 0.65239 | 0.60765 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed | 220 | 11.73440 | 0.31840 | 0.04770 | 1.16897 | 1.08880 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 440 | 11.41600 | 11.41600 | 0.04641 | 1.13725 | 1.05925 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_outline | 246 | 0.05960 | 0.05960 | 0.00024 | 0.00594 | 0.00553 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_after_terrain | 246 | 7.78060 | 7.78060 | 0.03163 | 0.77509 | 0.72194 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clouds | 246 | 14.97800 | 14.97800 | 0.06089 | 1.49209 | 1.38976 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/weather | 246 | 0.15370 | 0.15370 | 0.00062 | 0.01531 | 0.01426 |
| frame/scene_render/world_view/world_render/feature_frame_release | 246 | 0.95430 | 0.95430 | 0.00388 | 0.09507 | 0.08855 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu | 246 | 0.19730 | 0.17930 | 0.00080 | 0.01965 | 0.01831 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu/terrain_translucency_sort | 246 | 0.01800 | 0.01800 | 0.00007 | 0.00179 | 0.00167 |
| frame/scene_render/world_view/world_render/terrain_occlusion_update | 246 | 0.14080 | 0.14080 | 0.00057 | 0.01403 | 0.01306 |
| frame/scene_render/world_view/hand_render | 246 | 21.21540 | 1.86200 | 0.08624 | 2.11345 | 1.96851 |
| frame/scene_render/world_view/hand_render/feature_render_all | 246 | 19.35340 | 0.79000 | 0.07867 | 1.92796 | 1.79574 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare | 246 | 6.12870 | 1.65740 | 0.02491 | 0.61053 | 0.56866 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 246 | 1.99020 | 1.99020 | 0.00809 | 0.19826 | 0.18466 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/shared_staged_upload | 246 | 2.48110 | 2.48110 | 0.01009 | 0.24716 | 0.23021 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_solid | 246 | 0.12680 | 0.12680 | 0.00052 | 0.01263 | 0.01177 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent | 246 | 11.71660 | 0.64620 | 0.04763 | 1.16719 | 1.08714 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 246 | 11.07040 | 0.21780 | 0.04500 | 1.10282 | 1.02719 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 246 | 10.85260 | 10.85260 | 0.04412 | 1.08112 | 1.00698 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_after_terrain | 246 | 0.02740 | 0.02740 | 0.00011 | 0.00273 | 0.00254 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_on_top | 246 | 0.02670 | 0.02670 | 0.00011 | 0.00266 | 0.00248 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_release | 246 | 0.53720 | 0.53720 | 0.00218 | 0.05352 | 0.04984 |
| frame/scene_render/world_view/feature_render_all | 246 | 2.08270 | 0.45390 | 0.00847 | 0.20748 | 0.19325 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare | 246 | 1.40470 | 1.37190 | 0.00571 | 0.13993 | 0.13034 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare/shared_staged_upload | 246 | 0.03280 | 0.03280 | 0.00013 | 0.00327 | 0.00304 |
| frame/scene_render/world_view/feature_render_all/feature_execute_solid | 246 | 0.01830 | 0.01830 | 0.00007 | 0.00182 | 0.00170 |
| frame/scene_render/world_view/feature_render_all/feature_execute_translucent | 246 | 0.01840 | 0.01840 | 0.00007 | 0.00183 | 0.00171 |
| frame/scene_render/world_view/feature_render_all/feature_execute_after_terrain | 246 | 0.01310 | 0.01310 | 0.00005 | 0.00131 | 0.00122 |
| frame/scene_render/world_view/feature_render_all/feature_execute_on_top | 246 | 0.01260 | 0.01260 | 0.00005 | 0.00126 | 0.00117 |
| frame/scene_render/world_view/feature_render_all/feature_frame_release | 246 | 0.16170 | 0.16170 | 0.00066 | 0.01611 | 0.01500 |
| frame/scene_render/world_screenshot_check | 246 | 0.01220 | 0.01220 | 0.00005 | 0.00122 | 0.00113 |
| frame/scene_render/entity_outline_postprocess | 246 | 7.15100 | 7.15100 | 0.02907 | 0.71237 | 0.66352 |
| frame/scene_render/gui_render | 246 | 92.01530 | 3.39350 | 0.37405 | 9.16646 | 8.53779 |
| frame/scene_render/gui_render/gui_prepare | 246 | 58.87890 | 5.39730 | 0.23935 | 5.86545 | 5.46318 |
| frame/scene_render/gui_render/gui_prepare/gui_pictures_prepare | 246 | 0.70380 | 0.70380 | 0.00286 | 0.07011 | 0.06530 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare | 246 | 36.90770 | 7.61780 | 0.15003 | 3.67670 | 3.42454 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all | 246 | 29.28990 | 0.67770 | 0.11906 | 2.91783 | 2.71771 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare | 246 | 10.76590 | 1.63160 | 0.04376 | 1.07249 | 0.99893 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 246 | 7.78330 | 7.78330 | 0.03164 | 0.77536 | 0.72219 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/shared_staged_upload | 246 | 1.35100 | 1.35100 | 0.00549 | 0.13459 | 0.12535 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid | 246 | 17.32040 | 0.33580 | 0.07041 | 1.72544 | 1.60710 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 246 | 16.98460 | 0.37110 | 0.06904 | 1.69199 | 1.57594 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 492 | 16.61350 | 16.61350 | 0.06753 | 1.65502 | 1.54151 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_translucent | 246 | 0.14630 | 0.14630 | 0.00059 | 0.01457 | 0.01357 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_after_terrain | 246 | 0.01890 | 0.01890 | 0.00008 | 0.00188 | 0.00175 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_on_top | 246 | 0.01590 | 0.01590 | 0.00006 | 0.00158 | 0.00148 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_release | 246 | 0.34480 | 0.34480 | 0.00140 | 0.03435 | 0.03199 |
| frame/scene_render/gui_render/gui_prepare/gui_text_prepare | 246 | 2.16050 | 2.16050 | 0.00878 | 0.21523 | 0.20047 |
| frame/scene_render/gui_render/gui_prepare/gui_mesh_encode | 492 | 13.70960 | 13.70960 | 0.05573 | 1.36573 | 1.27207 |
| frame/scene_render/gui_render/shared_staged_upload | 246 | 2.72310 | 2.72310 | 0.01107 | 0.27127 | 0.25267 |
| frame/scene_render/gui_render/gui_draw_cpu | 246 | 27.01980 | 27.01980 | 0.10984 | 2.69168 | 2.50708 |
| frame/scene_render/gui_end_frame | 246 | 0.19570 | 0.19570 | 0.00080 | 0.01950 | 0.01816 |
| frame/shared_command_submit_cpu | 246 | 5.26020 | 5.26020 | 0.02138 | 0.52402 | 0.48808 |
| frame/presentation_cpu_wait | 246 | 54.88160 | 54.88160 | 0.22310 | 5.46724 | 5.09228 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer | 52 | 0.28460 | 0.07690 | 0.00116 | 0.02835 | 0.02641 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode | 26 | 0.20650 | 0.18450 | 0.00084 | 0.02057 | 0.01916 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode/material_match | 52 | 0.02200 | 0.02200 | 0.00009 | 0.00219 | 0.00204 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/glint_encode | 26 | 0.00120 | 0.00120 | 0.00000 | 0.00012 | 0.00011 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed | 26 | 1.39930 | 0.03640 | 0.00569 | 0.13940 | 0.12984 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 52 | 1.36290 | 1.36290 | 0.00554 | 0.13577 | 0.12646 |

## Sampled counters

- player_submissions: 1349
- layer_calls/WingsLayer: 1349
- feature_draw_submissions/ShadowFeatureRenderer/unattributed: 246
- feature_draw_submissions/CustomFeatureRenderer/unattributed: 246
- feature_draw_submissions/ModelFeatureRenderer/mixed: 992
- feature_draw_submissions/NameTagFeatureRenderer/mixed: 492
- name_tag_glyph_passes: 2686
- layer_calls/Deadmau5EarsLayer: 1349
- layer_calls/BeeStingerLayer: 1349
- layer_calls/CapeLayer: 1349
- layer_calls/SpinAttackEffectLayer: 1349
- tagged_submits: 2966
- feature_draw_submissions/ItemFeatureRenderer/unattributed: 1178
- feature_draw_submissions/TextFeatureRenderer/unattributed: 246
- item_preparations: 52
- layer_calls/ArrowLayer: 1349
- layer_calls/CustomHeadLayer: 1349
- model_preparations: 254
- feature_draw_submissions/ItemFeatureRenderer/mixed: 52
- draw_submissions/unattributed: 2408
- name_tag_preparations: 2686
- player_extractions: 1349
- layer_calls/HumanoidArmorLayer: 1349
- setup_animation_calls: 254
- layer_calls/PlayerItemInHandLayer: 1349
- draw_submissions/mixed: 1536
- layer_calls/ParrotOnShoulderLayer: 1349
- feature_draw_submissions/ModelFeatureRenderer/unattributed: 492

Measured recorder bookkeeping: 19.8436 ms. Timing-node overflow: 0.

## Coverage and limitations

- CPU-thread elapsed time, including possible driver waits; GPU execution time is unavailable.
- One instrumented frame every 20 rendered frames. This is diagnostic sampling, not an uninstrumented FPS benchmark or a complete frametime trace.
- Inclusive parents contain their children. Self time removes measured child spans only; unknown work and observer overhead remain.
- Frame-interval percentages use the sum of matched start-to-next-start intervals for sampled frames; render-frame percentages use the renderFrame method's measured elapsed time.
- Shared uploads cover all staged features. Mixed groups are not apportioned to players. Actual draw submissions are CPU calls, not GPU elapsed time.
- Player attribution follows tagged model/item/name-tag submits. Name-tag layout and glyph emission are measured separately; shared or mixed name-tag draws are not apportioned. Other text, shadow, leash and custom bypass paths are not individually attributed.
- Name-tag groups combine submit provenance with observed buffer use, including text-cache hits. Unknown-origin submits prevent a player-only classification even if they emit no glyphs.
- World/GUI extraction, terrain preparation, frame-graph passes and feature phases are CPU scopes for the whole scene. Missing or bypassed hooks remain in parent self time; pass labels do not identify separate views or GPU execution.
- Glint classification uses render-type naming, not shader inspection. Repeated model/state identity is an opportunity counter, not proof that mutable poses or geometry can be reused.
- Deep cube/part hooks describe the vanilla ModelPart path; custom mesh/vertex formats may bypass it. Cube vertex counts are topology counts, not uploaded bytes or visible pixels.
- Measured bookkeeping is a partial observer-cost indicator; clock, call-chain, JIT and allocation effects are not fully isolated or subtracted. Compare control, stages and deep under the same scene.
- No player names/UUIDs are stored. Per-frame attribution maps are bounded and cleared; limits/overflows are disclosed by counters.

Settings, per-frame denominators, mods and all unrounded values: [profile.json](profile.json).
