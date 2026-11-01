# DrawLess player CPU profile

Result: **complete**; mode: **stages**; sampled frames: 234 / observed: 4677.

Environment: `framebuffer=1920x1129; vsync=false; fpsLimit=260; camera=FIRST_PERSON; renderDistance=7; fov=110; resourcePacks=[vanilla, file/resources.zip]`

CPU timing includes profiling overhead. Percentages describe measured scopes, not a predicted FPS gain.

Coverage: `scene-stages-and-player-name-tags`; schema: 2. World, terrain, frame-pass and GUI scopes cover the whole scene. Player name-tag layout/glyph scopes are attributed separately; mixed draws remain shared.


## Largest self-time scopes

| Stage | Self ms / sampled frame |
| --- | ---: |
| frame/scene_extract/world_extract/entities_extract | 0.53891 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 0.38097 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 0.29151 |
| frame/presentation_cpu_wait | 0.22403 |
| frame/scene_extract/world_extract/particles_extract | 0.18504 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 0.15687 |
| frame/scene_render/gui_render/gui_draw_cpu | 0.11135 |
| frame/scene_extract/gui_extract/hud_extract | 0.10622 |
| frame/scene_extract/world_extract/block_entities_extract | 0.10431 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 0.10005 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 0.09941 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.09816 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 0.08163 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.07709 |
| frame/scene_render | 0.07689 |

## Complete timing tree

| Stage (nested path) | Calls | Inclusive ms | Self ms | ms / sampled frame | % renderFrame | % frame interval |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| frame | 234 | 1005.92760 | 15.50900 | 4.29884 | 100.00000 | 95.02819 |
| frame/surface_acquire_cpu | 234 | 0.04500 | 0.04500 | 0.00019 | 0.00447 | 0.00425 |
| frame/scene_extract | 234 | 244.34980 | 0.82940 | 1.04423 | 24.29099 | 23.08329 |
| frame/scene_extract/window_extract | 234 | 0.01820 | 0.01820 | 0.00008 | 0.00181 | 0.00172 |
| frame/scene_extract/options_extract | 234 | 0.08350 | 0.08350 | 0.00036 | 0.00830 | 0.00789 |
| frame/scene_extract/lightmap_extract | 234 | 0.15440 | 0.15440 | 0.00066 | 0.01535 | 0.01459 |
| frame/scene_extract/camera_extract | 234 | 1.87870 | 1.87870 | 0.00803 | 0.18676 | 0.17748 |
| frame/scene_extract/world_extract | 234 | 208.09020 | 4.87380 | 0.88927 | 20.68640 | 19.65791 |
| frame/scene_extract/world_extract/entities_extract | 234 | 135.32180 | 126.10550 | 0.57830 | 13.45244 | 12.78361 |
| frame/scene_extract/world_extract/entities_extract/player_extract | 1929 | 9.21630 | 9.21630 | 0.03939 | 0.91620 | 0.87065 |
| frame/scene_extract/world_extract/block_entities_extract | 234 | 24.40900 | 24.40900 | 0.10431 | 2.42652 | 2.30587 |
| frame/scene_extract/world_extract/block_outline_extract | 234 | 0.04240 | 0.04240 | 0.00018 | 0.00422 | 0.00401 |
| frame/scene_extract/world_extract/block_damage_extract | 234 | 0.00980 | 0.00980 | 0.00004 | 0.00097 | 0.00093 |
| frame/scene_extract/world_extract/particles_extract | 234 | 43.29870 | 43.29870 | 0.18504 | 4.30436 | 4.09035 |
| frame/scene_extract/world_extract/gizmos_extract | 234 | 0.13470 | 0.13470 | 0.00058 | 0.01339 | 0.01272 |
| frame/scene_extract/gui_extract | 234 | 33.29540 | 0.60970 | 0.14229 | 3.30992 | 3.14536 |
| frame/scene_extract/gui_extract/hud_extract | 234 | 32.62920 | 24.85520 | 0.13944 | 3.24369 | 3.08242 |
| frame/scene_extract/gui_extract/hud_extract/scoreboard_extract | 234 | 0.09670 | 0.09670 | 0.00041 | 0.00961 | 0.00914 |
| frame/scene_extract/gui_extract/hud_extract/chat_extract | 234 | 7.63270 | 7.63270 | 0.03262 | 0.75877 | 0.72105 |
| frame/scene_extract/gui_extract/hud_extract/tab_list_extract | 234 | 0.04460 | 0.04460 | 0.00019 | 0.00443 | 0.00421 |
| frame/scene_extract/gui_extract/debug_overlay_extract | 234 | 0.05650 | 0.05650 | 0.00024 | 0.00562 | 0.00534 |
| frame/pending_render_tasks_cpu | 234 | 0.02360 | 0.02360 | 0.00010 | 0.00235 | 0.00223 |
| frame/scene_render | 234 | 688.44890 | 17.99200 | 2.94209 | 68.43921 | 65.03654 |
| frame/scene_render/lightmap_render_cpu | 234 | 1.03910 | 1.03910 | 0.00444 | 0.10330 | 0.09816 |
| frame/scene_render/world_view | 234 | 570.63320 | 8.05800 | 2.43860 | 56.72706 | 53.90670 |
| frame/scene_render/world_view/world_render | 234 | 539.74330 | 1.73420 | 2.30660 | 53.65628 | 50.98859 |
| frame/scene_render/world_view/world_render/world_feature_submit | 234 | 79.15930 | 1.06040 | 0.33829 | 7.86928 | 7.47804 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 234 | 58.98100 | 16.54190 | 0.25206 | 5.86334 | 5.57183 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit | 1929 | 42.43910 | 14.23170 | 0.18136 | 4.21890 | 4.00915 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/HumanoidArmorLayer | 1929 | 13.23700 | 13.23700 | 0.05657 | 1.31590 | 1.25048 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/PlayerItemInHandLayer | 1929 | 5.31090 | 5.31090 | 0.02270 | 0.52796 | 0.50171 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ArrowLayer | 1929 | 0.43770 | 0.43770 | 0.00187 | 0.04351 | 0.04135 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/Deadmau5EarsLayer | 1929 | 0.41630 | 0.41630 | 0.00178 | 0.04138 | 0.03933 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CapeLayer | 1929 | 0.56300 | 0.56300 | 0.00241 | 0.05597 | 0.05319 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CustomHeadLayer | 1929 | 1.96660 | 1.96660 | 0.00840 | 0.19550 | 0.18578 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/WingsLayer | 1929 | 0.76170 | 0.76170 | 0.00326 | 0.07572 | 0.07196 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ParrotOnShoulderLayer | 1929 | 0.37450 | 0.37450 | 0.00160 | 0.03723 | 0.03538 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/SpinAttackEffectLayer | 1929 | 0.34120 | 0.34120 | 0.00146 | 0.03392 | 0.03223 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/BeeStingerLayer | 1929 | 0.39730 | 0.39730 | 0.00170 | 0.03950 | 0.03753 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/player_name_tag_submit | 1929 | 4.40120 | 4.40120 | 0.01881 | 0.43753 | 0.41577 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 234 | 19.10110 | 19.10110 | 0.08163 | 1.89885 | 1.80445 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_damage_submit | 234 | 0.00860 | 0.00860 | 0.00004 | 0.00085 | 0.00081 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_outline_submit | 234 | 0.00820 | 0.00820 | 0.00004 | 0.00082 | 0.00077 |
| frame/scene_render/world_view/world_render/feature_frame_prepare | 234 | 128.45650 | 17.68200 | 0.54896 | 12.76995 | 12.13506 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ShadowFeatureRenderer/prepare | 234 | 2.78850 | 2.78850 | 0.01192 | 0.27721 | 0.26342 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/CustomFeatureRenderer/prepare | 234 | 0.83420 | 0.83420 | 0.00356 | 0.08293 | 0.07881 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 468 | 17.04390 | 15.10790 | 0.07284 | 1.69435 | 1.61011 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material | 234 | 1.83000 | 0.58520 | 0.00782 | 0.18192 | 0.17288 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer | 234 | 0.42270 | 0.25740 | 0.00181 | 0.04202 | 0.03993 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer/material_match | 234 | 0.16530 | 0.16530 | 0.00071 | 0.01643 | 0.01562 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/setup_animation | 234 | 0.35600 | 0.35600 | 0.00152 | 0.03539 | 0.03363 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/geometry_encode | 234 | 0.46610 | 0.46610 | 0.00199 | 0.04634 | 0.04403 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material | 11 | 0.10600 | 0.01760 | 0.00045 | 0.01054 | 0.01001 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer | 11 | 0.01700 | 0.01050 | 0.00007 | 0.00169 | 0.00161 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer/material_match | 11 | 0.00650 | 0.00650 | 0.00003 | 0.00065 | 0.00061 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/setup_animation | 11 | 0.00840 | 0.00840 | 0.00004 | 0.00084 | 0.00079 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/geometry_encode | 11 | 0.06300 | 0.06300 | 0.00027 | 0.00626 | 0.00595 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/TextFeatureRenderer/prepare | 468 | 8.03690 | 8.03690 | 0.03435 | 0.79895 | 0.75923 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 468 | 29.19740 | 23.41110 | 0.12478 | 2.90253 | 2.75823 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer | 468 | 3.82930 | 0.30030 | 0.01636 | 0.38067 | 0.36175 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/main_encode | 234 | 1.43480 | 1.30720 | 0.00613 | 0.14263 | 0.13554 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/main_encode/material_match | 234 | 0.12760 | 0.12760 | 0.00055 | 0.01268 | 0.01205 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer | 468 | 1.95700 | 0.40440 | 0.00836 | 0.19455 | 0.18487 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode | 234 | 1.54410 | 1.38650 | 0.00660 | 0.15350 | 0.14587 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode/material_match | 376 | 0.15760 | 0.15760 | 0.00067 | 0.01567 | 0.01489 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode | 234 | 2.09420 | 1.39070 | 0.00895 | 0.20819 | 0.19784 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode/material_match | 234 | 0.70350 | 0.70350 | 0.00301 | 0.06994 | 0.06646 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/glint_encode | 234 | 0.00850 | 0.00850 | 0.00004 | 0.00084 | 0.00080 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare | 468 | 29.61270 | 16.87660 | 0.12655 | 2.94382 | 2.79746 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/text_prepare | 3853 | 8.09410 | 8.09410 | 0.03459 | 0.80464 | 0.76464 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/glyph_encode | 3853 | 4.64200 | 4.64200 | 0.01984 | 0.46146 | 0.43852 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 234 | 23.26090 | 23.26090 | 0.09941 | 2.31238 | 2.19742 |
| frame/scene_render/world_view/world_render/terrain_prepare | 234 | 0.05020 | 0.05020 | 0.00021 | 0.00499 | 0.00474 |
| frame/scene_render/world_view/world_render/frame_graph_cpu | 234 | 329.07590 | 2.69060 | 1.40631 | 32.71368 | 31.08721 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clear | 234 | 9.65620 | 9.65620 | 0.04127 | 0.95993 | 0.91220 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 234 | 36.70710 | 36.70710 | 0.15687 | 3.64908 | 3.46765 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 234 | 265.42640 | 89.14670 | 1.13430 | 26.38623 | 25.07436 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 468 | 68.21320 | 68.21320 | 0.29151 | 6.78112 | 6.44398 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid | 234 | 39.02710 | 7.49900 | 0.16678 | 3.87971 | 3.68682 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 234 | 7.94170 | 0.28770 | 0.03394 | 0.78949 | 0.75024 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 234 | 7.65400 | 7.65400 | 0.03271 | 0.76089 | 0.72306 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed | 234 | 23.58640 | 0.61600 | 0.10080 | 2.34474 | 2.22817 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 936 | 22.97040 | 22.97040 | 0.09816 | 2.28350 | 2.16997 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent | 234 | 61.17060 | 2.61480 | 0.26141 | 6.08101 | 5.77868 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed | 234 | 8.15590 | 0.21720 | 0.03485 | 0.81078 | 0.77047 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 234 | 7.93870 | 7.93870 | 0.03393 | 0.78919 | 0.74995 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed | 11 | 0.56810 | 0.01410 | 0.00243 | 0.05648 | 0.05367 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 22 | 0.55400 | 0.55400 | 0.00237 | 0.05507 | 0.05234 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed | 468 | 12.20810 | 0.33720 | 0.05217 | 1.21362 | 1.15328 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed/draw_cpu/mixed | 468 | 11.87090 | 11.87090 | 0.05073 | 1.18009 | 1.12142 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed | 468 | 6.49510 | 0.24550 | 0.02776 | 0.64568 | 0.61358 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed | 234 | 6.25370 | 0.14720 | 0.02673 | 0.62168 | 0.59078 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 234 | 6.10650 | 6.10650 | 0.02610 | 0.60705 | 0.57687 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 234 | 6.24960 | 6.24960 | 0.02671 | 0.62128 | 0.59039 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed | 234 | 18.49650 | 0.45680 | 0.07904 | 1.83875 | 1.74733 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 702 | 18.03970 | 18.03970 | 0.07709 | 1.79334 | 1.70418 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_outline | 234 | 0.05120 | 0.05120 | 0.00022 | 0.00509 | 0.00484 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_after_terrain | 234 | 7.81760 | 7.81760 | 0.03341 | 0.77715 | 0.73851 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clouds | 234 | 14.45400 | 14.45400 | 0.06177 | 1.43688 | 1.36544 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/weather | 234 | 0.14160 | 0.14160 | 0.00061 | 0.01408 | 0.01338 |
| frame/scene_render/world_view/world_render/feature_frame_release | 234 | 0.93700 | 0.93700 | 0.00400 | 0.09315 | 0.08852 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu | 234 | 0.20290 | 0.18990 | 0.00087 | 0.02017 | 0.01917 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu/terrain_translucency_sort | 234 | 0.01300 | 0.01300 | 0.00006 | 0.00129 | 0.00123 |
| frame/scene_render/world_view/world_render/terrain_occlusion_update | 234 | 0.12730 | 0.12730 | 0.00054 | 0.01265 | 0.01203 |
| frame/scene_render/world_view/hand_render | 234 | 20.72400 | 1.84390 | 0.08856 | 2.06019 | 1.95776 |
| frame/scene_render/world_view/hand_render/feature_render_all | 234 | 18.88010 | 0.81980 | 0.08068 | 1.87688 | 1.78357 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare | 234 | 6.04220 | 1.68380 | 0.02582 | 0.60066 | 0.57080 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 234 | 1.94940 | 1.94940 | 0.00833 | 0.19379 | 0.18416 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/shared_staged_upload | 234 | 2.40900 | 2.40900 | 0.01029 | 0.23948 | 0.22757 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_solid | 234 | 0.14460 | 0.14460 | 0.00062 | 0.01437 | 0.01366 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent | 234 | 11.31440 | 0.67860 | 0.04835 | 1.12477 | 1.06885 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 234 | 10.63580 | 0.21590 | 0.04545 | 1.05731 | 1.00475 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 234 | 10.41990 | 10.41990 | 0.04453 | 1.03585 | 0.98435 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_after_terrain | 234 | 0.02800 | 0.02800 | 0.00012 | 0.00278 | 0.00265 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_on_top | 234 | 0.02590 | 0.02590 | 0.00011 | 0.00257 | 0.00245 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_release | 234 | 0.50520 | 0.50520 | 0.00216 | 0.05022 | 0.04773 |
| frame/scene_render/world_view/feature_render_all | 234 | 2.10790 | 0.55320 | 0.00901 | 0.20955 | 0.19913 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare | 234 | 1.33200 | 1.30330 | 0.00569 | 0.13242 | 0.12583 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare/shared_staged_upload | 234 | 0.02870 | 0.02870 | 0.00012 | 0.00285 | 0.00271 |
| frame/scene_render/world_view/feature_render_all/feature_execute_solid | 234 | 0.01960 | 0.01960 | 0.00008 | 0.00195 | 0.00185 |
| frame/scene_render/world_view/feature_render_all/feature_execute_translucent | 234 | 0.01780 | 0.01780 | 0.00008 | 0.00177 | 0.00168 |
| frame/scene_render/world_view/feature_render_all/feature_execute_after_terrain | 234 | 0.01150 | 0.01150 | 0.00005 | 0.00114 | 0.00109 |
| frame/scene_render/world_view/feature_render_all/feature_execute_on_top | 234 | 0.01180 | 0.01180 | 0.00005 | 0.00117 | 0.00111 |
| frame/scene_render/world_view/feature_render_all/feature_frame_release | 234 | 0.16200 | 0.16200 | 0.00069 | 0.01610 | 0.01530 |
| frame/scene_render/world_screenshot_check | 234 | 0.01000 | 0.01000 | 0.00004 | 0.00099 | 0.00094 |
| frame/scene_render/entity_outline_postprocess | 234 | 6.66630 | 6.66630 | 0.02849 | 0.66270 | 0.62975 |
| frame/scene_render/gui_render | 234 | 91.91660 | 3.25940 | 0.39281 | 9.13750 | 8.68320 |
| frame/scene_render/gui_render/gui_prepare | 234 | 59.43560 | 5.19660 | 0.25400 | 5.90854 | 5.61478 |
| frame/scene_render/gui_render/gui_prepare/gui_pictures_prepare | 234 | 0.75050 | 0.75050 | 0.00321 | 0.07461 | 0.07090 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare | 234 | 34.81420 | 7.12290 | 0.14878 | 3.46091 | 3.28884 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all | 234 | 27.69130 | 0.64110 | 0.11834 | 2.75281 | 2.61595 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare | 234 | 10.15300 | 1.53160 | 0.04339 | 1.00932 | 0.95914 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 234 | 7.32110 | 7.32110 | 0.03129 | 0.72780 | 0.69161 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/shared_staged_upload | 234 | 1.30030 | 1.30030 | 0.00556 | 0.12926 | 0.12284 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid | 234 | 16.38760 | 0.32570 | 0.07003 | 1.62910 | 1.54811 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 234 | 16.06190 | 0.37820 | 0.06864 | 1.59673 | 1.51734 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 468 | 15.68370 | 15.68370 | 0.06702 | 1.55913 | 1.48161 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_translucent | 234 | 0.14030 | 0.14030 | 0.00060 | 0.01395 | 0.01325 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_after_terrain | 234 | 0.01920 | 0.01920 | 0.00008 | 0.00191 | 0.00181 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_on_top | 234 | 0.01620 | 0.01620 | 0.00007 | 0.00161 | 0.00153 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_release | 234 | 0.33390 | 0.33390 | 0.00143 | 0.03319 | 0.03154 |
| frame/scene_render/gui_render/gui_prepare/gui_text_prepare | 234 | 2.54920 | 2.54920 | 0.01089 | 0.25342 | 0.24082 |
| frame/scene_render/gui_render/gui_prepare/gui_mesh_encode | 468 | 16.12510 | 16.12510 | 0.06891 | 1.60301 | 1.52331 |
| frame/scene_render/gui_render/shared_staged_upload | 234 | 3.16540 | 3.16540 | 0.01353 | 0.31467 | 0.29903 |
| frame/scene_render/gui_render/gui_draw_cpu | 234 | 26.05620 | 26.05620 | 0.11135 | 2.59027 | 2.46148 |
| frame/scene_render/gui_end_frame | 234 | 0.19170 | 0.19170 | 0.00082 | 0.01906 | 0.01811 |
| frame/shared_command_submit_cpu | 234 | 5.12720 | 5.12720 | 0.02191 | 0.50970 | 0.48436 |
| frame/presentation_cpu_wait | 234 | 52.42410 | 52.42410 | 0.22403 | 5.21152 | 4.95241 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 223 | 6.37840 | 0.18820 | 0.02726 | 0.63408 | 0.60256 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 223 | 6.19020 | 6.19020 | 0.02645 | 0.61537 | 0.58478 |

## Sampled counters

- player_submissions: 1929
- layer_calls/WingsLayer: 1929
- feature_draw_submissions/ShadowFeatureRenderer/unattributed: 234
- feature_draw_submissions/CustomFeatureRenderer/unattributed: 234
- feature_draw_submissions/ModelFeatureRenderer/mixed: 958
- feature_draw_submissions/NameTagFeatureRenderer/mixed: 468
- name_tag_glyph_passes: 3853
- layer_calls/Deadmau5EarsLayer: 1929
- layer_calls/BeeStingerLayer: 1929
- layer_calls/CapeLayer: 1929
- layer_calls/SpinAttackEffectLayer: 1929
- tagged_submits: 4566
- item_preparations: 936
- feature_draw_submissions/ItemFeatureRenderer/unattributed: 702
- feature_draw_submissions/TextFeatureRenderer/unattributed: 234
- layer_calls/ArrowLayer: 1929
- layer_calls/CustomHeadLayer: 1929
- model_preparations: 245
- feature_draw_submissions/ItemFeatureRenderer/mixed: 702
- draw_submissions/unattributed: 1861
- name_tag_preparations: 3853
- player_extractions: 1929
- layer_calls/HumanoidArmorLayer: 1929
- setup_animation_calls: 245
- layer_calls/PlayerItemInHandLayer: 1929
- draw_submissions/mixed: 2128
- layer_calls/ParrotOnShoulderLayer: 1929
- feature_draw_submissions/ModelFeatureRenderer/unattributed: 457

Measured recorder bookkeeping: 21.9598 ms. Timing-node overflow: 0.

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
