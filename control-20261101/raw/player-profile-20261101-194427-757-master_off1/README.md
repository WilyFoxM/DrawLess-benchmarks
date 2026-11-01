# DrawLess player CPU profile

Result: **complete**; mode: **stages**; sampled frames: 170 / observed: 3389.

Environment: `framebuffer=1920x1129; vsync=false; fpsLimit=260; camera=FIRST_PERSON; renderDistance=7; fov=110; resourcePacks=[vanilla, file/resources.zip]`

CPU timing includes profiling overhead. Percentages describe measured scopes, not a predicted FPS gain.

Coverage: `scene-stages-and-player-name-tags`; schema: 2. World, terrain, frame-pass and GUI scopes cover the whole scene. Player name-tag layout/glyph scopes are attributed separately; mixed draws remain shared.


## Largest self-time scopes

| Stage | Self ms / sampled frame |
| --- | ---: |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 0.67808 |
| frame/scene_extract/world_extract/entities_extract | 0.45297 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 0.35546 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 0.29726 |
| frame/presentation_cpu_wait | 0.24970 |
| frame/scene_extract/world_extract/particles_extract | 0.23855 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.23503 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 0.19396 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 0.18718 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.17842 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 0.17732 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 0.16697 |
| frame/scene_extract/gui_extract/hud_extract | 0.13876 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.12950 |
| frame/scene_extract/world_extract/block_entities_extract | 0.12455 |

## Complete timing tree

| Stage (nested path) | Calls | Inclusive ms | Self ms | ms / sampled frame | % renderFrame | % frame interval |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| frame | 170 | 1061.32320 | 13.64510 | 6.24308 | 100.00000 | 92.67913 |
| frame/surface_acquire_cpu | 170 | 0.09150 | 0.09150 | 0.00054 | 0.00862 | 0.00799 |
| frame/scene_extract | 170 | 186.70240 | 2.53210 | 1.09825 | 17.59147 | 16.30363 |
| frame/scene_extract/window_extract | 170 | 0.11630 | 0.11630 | 0.00068 | 0.01096 | 0.01016 |
| frame/scene_extract/options_extract | 170 | 0.22230 | 0.22230 | 0.00131 | 0.02095 | 0.01941 |
| frame/scene_extract/lightmap_extract | 170 | 0.25340 | 0.25340 | 0.00149 | 0.02388 | 0.02213 |
| frame/scene_extract/camera_extract | 170 | 2.06090 | 2.06090 | 0.01212 | 0.19418 | 0.17997 |
| frame/scene_extract/world_extract | 170 | 152.64430 | 7.81170 | 0.89791 | 14.38245 | 13.32953 |
| frame/scene_extract/world_extract/entities_extract | 170 | 82.59470 | 77.00530 | 0.48585 | 7.78224 | 7.21251 |
| frame/scene_extract/world_extract/entities_extract/player_extract | 915 | 5.58940 | 5.58940 | 0.03288 | 0.52664 | 0.48809 |
| frame/scene_extract/world_extract/block_entities_extract | 170 | 21.17320 | 21.17320 | 0.12455 | 1.99498 | 1.84893 |
| frame/scene_extract/world_extract/block_outline_extract | 170 | 0.13890 | 0.13890 | 0.00082 | 0.01309 | 0.01213 |
| frame/scene_extract/world_extract/block_damage_extract | 170 | 0.17110 | 0.17110 | 0.00101 | 0.01612 | 0.01494 |
| frame/scene_extract/world_extract/particles_extract | 170 | 40.55360 | 40.55360 | 0.23855 | 3.82104 | 3.54131 |
| frame/scene_extract/world_extract/gizmos_extract | 170 | 0.20110 | 0.20110 | 0.00118 | 0.01895 | 0.01756 |
| frame/scene_extract/gui_extract | 170 | 28.87310 | 1.51240 | 0.16984 | 2.72048 | 2.52132 |
| frame/scene_extract/gui_extract/hud_extract | 170 | 27.25660 | 23.58860 | 0.16033 | 2.56817 | 2.38016 |
| frame/scene_extract/gui_extract/hud_extract/scoreboard_extract | 170 | 0.25000 | 0.25000 | 0.00147 | 0.02356 | 0.02183 |
| frame/scene_extract/gui_extract/hud_extract/chat_extract | 170 | 3.35620 | 3.35620 | 0.01974 | 0.31623 | 0.29308 |
| frame/scene_extract/gui_extract/hud_extract/tab_list_extract | 170 | 0.06180 | 0.06180 | 0.00036 | 0.00582 | 0.00540 |
| frame/scene_extract/gui_extract/debug_overlay_extract | 170 | 0.10410 | 0.10410 | 0.00061 | 0.00981 | 0.00909 |
| frame/pending_render_tasks_cpu | 170 | 0.04330 | 0.04330 | 0.00025 | 0.00408 | 0.00378 |
| frame/scene_render | 170 | 814.33280 | 16.74910 | 4.79019 | 76.72807 | 71.11091 |
| frame/scene_render/lightmap_render_cpu | 170 | 1.47350 | 1.47350 | 0.00867 | 0.13884 | 0.12867 |
| frame/scene_render/world_view | 170 | 719.90540 | 8.57230 | 4.23474 | 67.83093 | 62.86512 |
| frame/scene_render/world_view/world_render | 170 | 690.57500 | 4.74710 | 4.06221 | 65.06736 | 60.30386 |
| frame/scene_render/world_view/world_render/world_feature_submit | 170 | 85.30580 | 2.04320 | 0.50180 | 8.03768 | 7.44926 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 170 | 68.24860 | 50.53500 | 0.40146 | 6.43052 | 5.95975 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit | 915 | 17.71360 | 6.34510 | 0.10420 | 1.66901 | 1.54682 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/HumanoidArmorLayer | 915 | 3.82610 | 3.82610 | 0.02251 | 0.36050 | 0.33411 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/PlayerItemInHandLayer | 915 | 2.20830 | 2.20830 | 0.01299 | 0.20807 | 0.19284 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ArrowLayer | 915 | 0.22820 | 0.22820 | 0.00134 | 0.02150 | 0.01993 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/Deadmau5EarsLayer | 915 | 0.25520 | 0.25520 | 0.00150 | 0.02405 | 0.02229 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CapeLayer | 915 | 0.34270 | 0.34270 | 0.00202 | 0.03229 | 0.02993 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CustomHeadLayer | 915 | 1.04850 | 1.04850 | 0.00617 | 0.09879 | 0.09156 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/WingsLayer | 915 | 0.45950 | 0.45950 | 0.00270 | 0.04330 | 0.04013 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ParrotOnShoulderLayer | 915 | 0.19260 | 0.19260 | 0.00113 | 0.01815 | 0.01682 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/SpinAttackEffectLayer | 915 | 0.15790 | 0.15790 | 0.00093 | 0.01488 | 0.01379 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/BeeStingerLayer | 915 | 0.20740 | 0.20740 | 0.00122 | 0.01954 | 0.01811 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/player_name_tag_submit | 915 | 2.44210 | 2.44210 | 0.01437 | 0.23010 | 0.21325 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 170 | 14.89110 | 14.89110 | 0.08759 | 1.40307 | 1.30035 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_damage_submit | 170 | 0.08460 | 0.08460 | 0.00050 | 0.00797 | 0.00739 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_outline_submit | 170 | 0.03830 | 0.03830 | 0.00023 | 0.00361 | 0.00334 |
| frame/scene_render/world_view/world_render/feature_frame_prepare | 170 | 274.54320 | 14.75250 | 1.61496 | 25.86801 | 23.97425 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ShadowFeatureRenderer/prepare | 170 | 2.44160 | 2.44160 | 0.01436 | 0.23005 | 0.21321 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/CustomFeatureRenderer/prepare | 170 | 0.91690 | 0.91690 | 0.00539 | 0.08639 | 0.08007 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 850 | 59.63080 | 32.97390 | 0.35077 | 5.61853 | 5.20721 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material | 170 | 1.98160 | 0.80470 | 0.01166 | 0.18671 | 0.17304 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer | 170 | 0.39580 | 0.21360 | 0.00233 | 0.03729 | 0.03456 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer/material_match | 170 | 0.18220 | 0.18220 | 0.00107 | 0.01717 | 0.01591 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/setup_animation | 170 | 0.34560 | 0.34560 | 0.00203 | 0.03256 | 0.03018 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/geometry_encode | 170 | 0.43550 | 0.43550 | 0.00256 | 0.04103 | 0.03803 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material | 915 | 7.44580 | 1.22760 | 0.04380 | 0.70156 | 0.65020 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer | 915 | 1.39850 | 0.59950 | 0.00823 | 0.13177 | 0.12212 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer/material_match | 915 | 0.79900 | 0.79900 | 0.00470 | 0.07528 | 0.06977 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/setup_animation | 915 | 0.35520 | 0.35520 | 0.00209 | 0.03347 | 0.03102 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/geometry_encode | 915 | 4.46450 | 4.46450 | 0.02626 | 0.42065 | 0.38986 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material | 2279 | 11.12660 | 2.45240 | 0.06545 | 1.04837 | 0.97162 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/material_buffer | 2279 | 2.68730 | 1.09540 | 0.01581 | 0.25320 | 0.23467 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/material_buffer/material_match | 1238 | 1.59190 | 1.59190 | 0.00936 | 0.14999 | 0.13901 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/setup_animation | 2279 | 0.74070 | 0.74070 | 0.00436 | 0.06979 | 0.06468 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/geometry_encode | 2279 | 5.24620 | 5.24620 | 0.03086 | 0.49431 | 0.45812 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint | 1347 | 6.10290 | 1.45190 | 0.03590 | 0.57503 | 0.53293 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/material_buffer | 1347 | 0.83260 | 0.30140 | 0.00490 | 0.07845 | 0.07271 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/material_buffer/material_match | 170 | 0.53120 | 0.53120 | 0.00312 | 0.05005 | 0.04639 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/setup_animation | 1347 | 0.32950 | 0.32950 | 0.00194 | 0.03105 | 0.02877 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/geometry_encode | 1347 | 3.48890 | 3.48890 | 0.02052 | 0.32873 | 0.30467 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/TextFeatureRenderer/prepare | 340 | 6.33980 | 6.33980 | 0.03729 | 0.59735 | 0.55362 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 340 | 137.23460 | 115.27380 | 0.80726 | 12.93052 | 11.98389 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer | 1708 | 17.05960 | 0.84510 | 0.10035 | 1.60739 | 1.48971 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/main_encode | 854 | 12.88290 | 12.88290 | 0.07578 | 1.21385 | 1.12499 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer | 898 | 4.90120 | 0.37530 | 0.02883 | 0.46180 | 0.42799 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode | 449 | 4.50570 | 4.16850 | 0.02650 | 0.42454 | 0.39346 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode | 854 | 3.33160 | 2.64810 | 0.01960 | 0.31391 | 0.29093 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode/material_match | 170 | 0.68350 | 0.68350 | 0.00402 | 0.06440 | 0.05969 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/glint_encode | 449 | 0.02020 | 0.02020 | 0.00012 | 0.00190 | 0.00176 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode/material_match | 327 | 0.33720 | 0.33720 | 0.00198 | 0.03177 | 0.02945 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare | 340 | 21.40660 | 13.84640 | 0.12592 | 2.01697 | 1.86931 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/text_prepare | 1825 | 4.77430 | 4.77430 | 0.02808 | 0.44984 | 0.41691 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/glyph_encode | 1825 | 2.78590 | 2.75470 | 0.01639 | 0.26249 | 0.24328 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/glyph_encode/material_match | 26 | 0.03120 | 0.03120 | 0.00018 | 0.00294 | 0.00272 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 170 | 31.82040 | 31.82040 | 0.18718 | 2.99818 | 2.77869 |
| frame/scene_render/world_view/world_render/terrain_prepare | 170 | 0.15810 | 0.15810 | 0.00093 | 0.01490 | 0.01381 |
| frame/scene_render/world_view/world_render/frame_graph_cpu | 170 | 323.88100 | 3.49320 | 1.90518 | 30.51672 | 28.28263 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clear | 170 | 8.92460 | 8.92460 | 0.05250 | 0.84089 | 0.77933 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 170 | 30.14430 | 30.14430 | 0.17732 | 2.84026 | 2.63232 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 170 | 269.12860 | 9.07610 | 1.58311 | 25.35784 | 23.50142 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 340 | 60.42820 | 60.42820 | 0.35546 | 5.69367 | 5.27684 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid | 170 | 70.18390 | 6.07420 | 0.41285 | 6.61287 | 6.12875 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/mixed | 170 | 12.25310 | 0.55030 | 0.07208 | 1.15451 | 1.06999 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 340 | 11.70280 | 11.70280 | 0.06884 | 1.10266 | 1.02194 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed | 170 | 22.65620 | 0.64140 | 0.13327 | 2.13471 | 1.97843 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 850 | 22.01480 | 22.01480 | 0.12950 | 2.07428 | 1.92242 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only | 340 | 29.20040 | 0.81620 | 0.17177 | 2.75132 | 2.54990 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 1238 | 28.38420 | 28.38420 | 0.16697 | 2.67442 | 2.47863 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent | 170 | 123.19800 | 2.70430 | 0.72469 | 11.60796 | 10.75816 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed | 170 | 5.02130 | 0.15380 | 0.02954 | 0.47312 | 0.43848 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 170 | 4.86750 | 4.86750 | 0.02863 | 0.45863 | 0.42505 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed | 170 | 31.04880 | 0.71680 | 0.18264 | 2.92548 | 2.71131 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 1255 | 30.33200 | 30.33200 | 0.17842 | 2.85794 | 2.64872 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed | 340 | 9.56560 | 0.24770 | 0.05627 | 0.90129 | 0.83531 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed/draw_cpu/mixed | 340 | 9.31790 | 9.31790 | 0.05481 | 0.87795 | 0.81368 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed | 340 | 5.12780 | 0.18770 | 0.03016 | 0.48315 | 0.44778 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed | 170 | 4.80490 | 0.14460 | 0.02826 | 0.45273 | 0.41958 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 170 | 4.66030 | 4.66030 | 0.02741 | 0.43910 | 0.40696 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 170 | 4.94010 | 4.94010 | 0.02906 | 0.46547 | 0.43139 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/players_only | 170 | 4.79520 | 0.14530 | 0.02821 | 0.45181 | 0.41874 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 170 | 4.64990 | 4.64990 | 0.02735 | 0.43812 | 0.40605 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed | 109 | 40.97740 | 1.02290 | 0.24104 | 3.86097 | 3.57832 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 1635 | 39.95450 | 39.95450 | 0.23503 | 3.76459 | 3.48899 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_outline | 170 | 0.13080 | 0.13080 | 0.00077 | 0.01232 | 0.01142 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_after_terrain | 170 | 6.11160 | 6.11160 | 0.03595 | 0.57585 | 0.53369 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clouds | 170 | 12.03650 | 12.03650 | 0.07080 | 1.13410 | 1.05108 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/weather | 170 | 0.15380 | 0.15380 | 0.00090 | 0.01449 | 0.01343 |
| frame/scene_render/world_view/world_render/feature_frame_release | 170 | 0.84560 | 0.84560 | 0.00497 | 0.07967 | 0.07384 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu | 170 | 0.68580 | 0.55410 | 0.00403 | 0.06462 | 0.05989 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu/terrain_translucency_sort | 170 | 0.13170 | 0.13170 | 0.00077 | 0.01241 | 0.01150 |
| frame/scene_render/world_view/world_render/terrain_occlusion_update | 170 | 0.40840 | 0.40840 | 0.00240 | 0.03848 | 0.03566 |
| frame/scene_render/world_view/hand_render | 170 | 18.92230 | 2.86600 | 0.11131 | 1.78290 | 1.65237 |
| frame/scene_render/world_view/hand_render/feature_render_all | 170 | 16.05630 | 1.18350 | 0.09445 | 1.51286 | 1.40210 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare | 170 | 5.45110 | 1.56210 | 0.03207 | 0.51361 | 0.47601 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 170 | 1.79830 | 1.79830 | 0.01058 | 0.16944 | 0.15703 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/shared_staged_upload | 170 | 2.09070 | 2.09070 | 0.01230 | 0.19699 | 0.18257 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_solid | 170 | 0.10560 | 0.10560 | 0.00062 | 0.00995 | 0.00922 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent | 170 | 8.78250 | 0.48370 | 0.05166 | 0.82750 | 0.76692 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 170 | 8.29880 | 0.15630 | 0.04882 | 0.78193 | 0.72469 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 170 | 8.14250 | 8.14250 | 0.04790 | 0.76720 | 0.71104 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_after_terrain | 170 | 0.03550 | 0.03550 | 0.00021 | 0.00334 | 0.00310 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_on_top | 170 | 0.06980 | 0.06980 | 0.00041 | 0.00658 | 0.00610 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_release | 170 | 0.42830 | 0.42830 | 0.00252 | 0.04036 | 0.03740 |
| frame/scene_render/world_view/feature_render_all | 170 | 1.83580 | 0.53300 | 0.01080 | 0.17297 | 0.16031 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare | 170 | 1.11290 | 1.07450 | 0.00655 | 0.10486 | 0.09718 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare/shared_staged_upload | 170 | 0.03840 | 0.03840 | 0.00023 | 0.00362 | 0.00335 |
| frame/scene_render/world_view/feature_render_all/feature_execute_solid | 170 | 0.01870 | 0.01870 | 0.00011 | 0.00176 | 0.00163 |
| frame/scene_render/world_view/feature_render_all/feature_execute_translucent | 170 | 0.01590 | 0.01590 | 0.00009 | 0.00150 | 0.00139 |
| frame/scene_render/world_view/feature_render_all/feature_execute_after_terrain | 170 | 0.01220 | 0.01220 | 0.00007 | 0.00115 | 0.00107 |
| frame/scene_render/world_view/feature_render_all/feature_execute_on_top | 170 | 0.01670 | 0.01670 | 0.00010 | 0.00157 | 0.00146 |
| frame/scene_render/world_view/feature_render_all/feature_frame_release | 170 | 0.12640 | 0.12640 | 0.00074 | 0.01191 | 0.01104 |
| frame/scene_render/world_screenshot_check | 170 | 0.07190 | 0.07190 | 0.00042 | 0.00677 | 0.00628 |
| frame/scene_render/entity_outline_postprocess | 170 | 5.54480 | 5.54480 | 0.03262 | 0.52244 | 0.48419 |
| frame/scene_render/gui_render | 170 | 70.34450 | 3.28610 | 0.41379 | 6.62800 | 6.14277 |
| frame/scene_render/gui_render/gui_prepare | 170 | 45.94530 | 5.32860 | 0.27027 | 4.32906 | 4.01213 |
| frame/scene_render/gui_render/gui_prepare/gui_pictures_prepare | 170 | 0.63700 | 0.63700 | 0.00375 | 0.06002 | 0.05563 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare | 170 | 29.80550 | 7.03650 | 0.17533 | 2.80833 | 2.60274 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all | 170 | 22.76900 | 0.75200 | 0.13394 | 2.14534 | 1.98828 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare | 170 | 8.66870 | 1.35320 | 0.05099 | 0.81678 | 0.75699 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 170 | 6.31840 | 6.31840 | 0.03717 | 0.59533 | 0.55175 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/shared_staged_upload | 170 | 0.99710 | 0.99710 | 0.00587 | 0.09395 | 0.08707 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid | 170 | 12.92740 | 0.26380 | 0.07604 | 1.21805 | 1.12887 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 170 | 12.66360 | 0.28280 | 0.07449 | 1.19319 | 1.10584 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 340 | 12.38080 | 12.38080 | 0.07283 | 1.16654 | 1.08114 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_translucent | 170 | 0.10870 | 0.10870 | 0.00064 | 0.01024 | 0.00949 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_after_terrain | 170 | 0.02560 | 0.02560 | 0.00015 | 0.00241 | 0.00224 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_on_top | 170 | 0.02760 | 0.02760 | 0.00016 | 0.00260 | 0.00241 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_release | 170 | 0.25900 | 0.25900 | 0.00152 | 0.02440 | 0.02262 |
| frame/scene_render/gui_render/gui_prepare/gui_text_prepare | 170 | 1.37010 | 1.37010 | 0.00806 | 0.12909 | 0.11964 |
| frame/scene_render/gui_render/gui_prepare/gui_mesh_encode | 340 | 8.80410 | 8.80410 | 0.05179 | 0.82954 | 0.76881 |
| frame/scene_render/gui_render/shared_staged_upload | 170 | 1.73880 | 1.73880 | 0.01023 | 0.16383 | 0.15184 |
| frame/scene_render/gui_render/gui_draw_cpu | 170 | 19.37430 | 19.37430 | 0.11397 | 1.82549 | 1.69184 |
| frame/scene_render/gui_end_frame | 170 | 0.24360 | 0.24360 | 0.00143 | 0.02295 | 0.02127 |
| frame/shared_command_submit_cpu | 170 | 4.05920 | 4.05920 | 0.02388 | 0.38247 | 0.35447 |
| frame/presentation_cpu_wait | 170 | 42.44890 | 42.44890 | 0.24970 | 3.99962 | 3.70681 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed | 61 | 19.15270 | 0.40900 | 0.11266 | 1.80461 | 1.67249 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 793 | 18.74370 | 18.74370 | 0.11026 | 1.76607 | 1.63678 |

## Sampled counters

- item_preparations: 2606
- feature_draw_submissions/ModelFeatureRenderer/mixed: 2105
- layer_calls/ArrowLayer: 915
- draw_submissions/unattributed: 1813
- layer_calls/BeeStingerLayer: 915
- feature_draw_submissions/ShadowFeatureRenderer/unattributed: 170
- layer_calls/WingsLayer: 915
- setup_animation_calls: 4711
- feature_draw_submissions/ItemFeatureRenderer/mixed: 1975
- feature_draw_submissions/NameTagFeatureRenderer/mixed: 340
- player_submissions: 915
- repeated_model_state_preparations: 1813
- feature_draw_submissions/CustomFeatureRenderer/unattributed: 170
- layer_calls/ParrotOnShoulderLayer: 915
- layer_calls/PlayerItemInHandLayer: 915
- layer_calls/Deadmau5EarsLayer: 915
- name_tag_preparations: 1825
- player_extractions: 915
- layer_calls/CustomHeadLayer: 915
- draw_submissions/mixed: 4420
- layer_calls/HumanoidArmorLayer: 915
- name_tag_glyph_passes: 1825
- feature_draw_submissions/ModelFeatureRenderer/players_only: 1408
- tagged_submits: 7839
- layer_calls/CapeLayer: 915
- feature_draw_submissions/ItemFeatureRenderer/unattributed: 1133
- feature_draw_submissions/TextFeatureRenderer/unattributed: 170
- draw_submissions/players_only: 1408
- layer_calls/SpinAttackEffectLayer: 915
- model_preparations: 4711
- feature_draw_submissions/ModelFeatureRenderer/unattributed: 170

Measured recorder bookkeeping: 23.7841 ms. Timing-node overflow: 0.

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
