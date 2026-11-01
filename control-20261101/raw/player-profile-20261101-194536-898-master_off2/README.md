# DrawLess player CPU profile

Result: **complete**; mode: **stages**; sampled frames: 186 / observed: 3714.

Environment: `framebuffer=1920x1129; vsync=false; fpsLimit=260; camera=FIRST_PERSON; renderDistance=7; fov=110; resourcePacks=[vanilla, file/resources.zip]`

CPU timing includes profiling overhead. Percentages describe measured scopes, not a predicted FPS gain.

Coverage: `scene-stages-and-player-name-tags`; schema: 2. World, terrain, frame-pass and GUI scopes cover the whole scene. Player name-tag layout/glyph scopes are attributed separately; mixed draws remain shared.


## Largest self-time scopes

| Stage | Self ms / sampled frame |
| --- | ---: |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 0.62838 |
| frame/scene_extract/world_extract/entities_extract | 0.39804 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 0.33164 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 0.30487 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 0.26676 |
| frame/presentation_cpu_wait | 0.22636 |
| frame/scene_extract/world_extract/particles_extract | 0.21645 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 0.17605 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.16567 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 0.16521 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 0.13493 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 0.12560 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 0.12436 |
| frame/scene_render/gui_render/gui_draw_cpu | 0.11497 |
| frame/scene_extract/gui_extract/hud_extract | 0.11385 |

## Complete timing tree

| Stage (nested path) | Calls | Inclusive ms | Self ms | ms / sampled frame | % renderFrame | % frame interval |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| frame | 186 | 1016.63620 | 12.54240 | 5.46579 | 100.00000 | 92.51291 |
| frame/surface_acquire_cpu | 186 | 0.03160 | 0.03160 | 0.00017 | 0.00311 | 0.00288 |
| frame/scene_extract | 186 | 172.94900 | 0.73570 | 0.92983 | 17.01189 | 15.73819 |
| frame/scene_extract/window_extract | 186 | 0.01790 | 0.01790 | 0.00010 | 0.00176 | 0.00163 |
| frame/scene_extract/options_extract | 186 | 0.07340 | 0.07340 | 0.00039 | 0.00722 | 0.00668 |
| frame/scene_extract/lightmap_extract | 186 | 0.13350 | 0.13350 | 0.00072 | 0.01313 | 0.01215 |
| frame/scene_extract/camera_extract | 186 | 1.65160 | 1.65160 | 0.00888 | 0.16246 | 0.15029 |
| frame/scene_extract/world_extract | 186 | 144.68160 | 4.16390 | 0.77786 | 14.23140 | 13.16589 |
| frame/scene_extract/world_extract/entities_extract | 186 | 79.16840 | 74.03530 | 0.42564 | 7.78729 | 7.20425 |
| frame/scene_extract/world_extract/entities_extract/player_extract | 955 | 5.13310 | 5.13310 | 0.02760 | 0.50491 | 0.46711 |
| frame/scene_extract/world_extract/block_entities_extract | 186 | 20.92560 | 20.92560 | 0.11250 | 2.05832 | 1.90421 |
| frame/scene_extract/world_extract/block_outline_extract | 186 | 0.03600 | 0.03600 | 0.00019 | 0.00354 | 0.00328 |
| frame/scene_extract/world_extract/block_damage_extract | 186 | 0.00940 | 0.00940 | 0.00005 | 0.00092 | 0.00086 |
| frame/scene_extract/world_extract/particles_extract | 186 | 40.26060 | 40.26060 | 0.21645 | 3.96018 | 3.66368 |
| frame/scene_extract/world_extract/gizmos_extract | 186 | 0.11770 | 0.11770 | 0.00063 | 0.01158 | 0.01071 |
| frame/scene_extract/gui_extract | 186 | 25.65530 | 0.51770 | 0.13793 | 2.52355 | 2.33461 |
| frame/scene_extract/gui_extract/hud_extract | 186 | 25.09060 | 21.17700 | 0.13490 | 2.46800 | 2.28322 |
| frame/scene_extract/gui_extract/hud_extract/scoreboard_extract | 186 | 0.07880 | 0.07880 | 0.00042 | 0.00775 | 0.00717 |
| frame/scene_extract/gui_extract/hud_extract/chat_extract | 186 | 3.78830 | 3.78830 | 0.02037 | 0.37263 | 0.34473 |
| frame/scene_extract/gui_extract/hud_extract/tab_list_extract | 186 | 0.04650 | 0.04650 | 0.00025 | 0.00457 | 0.00423 |
| frame/scene_extract/gui_extract/debug_overlay_extract | 186 | 0.04700 | 0.04700 | 0.00025 | 0.00462 | 0.00428 |
| frame/pending_render_tasks_cpu | 186 | 0.02330 | 0.02330 | 0.00013 | 0.00229 | 0.00212 |
| frame/scene_render | 186 | 784.78890 | 14.74820 | 4.21930 | 77.19466 | 71.41503 |
| frame/scene_render/lightmap_render_cpu | 186 | 1.03150 | 1.03150 | 0.00555 | 0.10146 | 0.09387 |
| frame/scene_render/world_view | 186 | 692.75770 | 7.04530 | 3.72450 | 68.14214 | 63.04028 |
| frame/scene_render/world_view/world_render | 186 | 666.82850 | 1.49470 | 3.58510 | 65.59165 | 60.68075 |
| frame/scene_render/world_view/world_render/world_feature_submit | 186 | 82.01910 | 0.89960 | 0.44096 | 8.06769 | 7.46366 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit | 186 | 65.53150 | 49.61680 | 0.35232 | 6.44591 | 5.96330 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit | 955 | 15.91470 | 5.34320 | 0.08556 | 1.56543 | 1.44822 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/HumanoidArmorLayer | 955 | 3.30740 | 3.30740 | 0.01778 | 0.32533 | 0.30097 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/PlayerItemInHandLayer | 955 | 2.26990 | 2.26990 | 0.01220 | 0.22328 | 0.20656 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ArrowLayer | 955 | 0.24450 | 0.24450 | 0.00131 | 0.02405 | 0.02225 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/Deadmau5EarsLayer | 955 | 0.27430 | 0.27430 | 0.00147 | 0.02698 | 0.02496 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CapeLayer | 955 | 0.33890 | 0.33890 | 0.00182 | 0.03334 | 0.03084 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/CustomHeadLayer | 955 | 0.91200 | 0.91200 | 0.00490 | 0.08971 | 0.08299 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/WingsLayer | 955 | 0.42250 | 0.42250 | 0.00227 | 0.04156 | 0.03845 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/ParrotOnShoulderLayer | 955 | 0.17760 | 0.17760 | 0.00095 | 0.01747 | 0.01616 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/SpinAttackEffectLayer | 955 | 0.15480 | 0.15480 | 0.00083 | 0.01523 | 0.01409 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/layer_submit/BeeStingerLayer | 955 | 0.20700 | 0.20700 | 0.00111 | 0.02036 | 0.01884 |
| frame/scene_render/world_view/world_render/world_feature_submit/entities_submit/player_submit/player_name_tag_submit | 955 | 2.26260 | 2.26260 | 0.01216 | 0.22256 | 0.20589 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_entities_submit | 186 | 15.57480 | 15.57480 | 0.08374 | 1.53199 | 1.41729 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_damage_submit | 186 | 0.00730 | 0.00730 | 0.00004 | 0.00072 | 0.00066 |
| frame/scene_render/world_view/world_render/world_feature_submit/block_outline_submit | 186 | 0.00590 | 0.00590 | 0.00003 | 0.00058 | 0.00054 |
| frame/scene_render/world_view/world_render/feature_frame_prepare | 186 | 262.90480 | 16.96420 | 1.41347 | 25.86026 | 23.92408 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ShadowFeatureRenderer/prepare | 186 | 2.05420 | 2.05420 | 0.01104 | 0.20206 | 0.18693 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/CustomFeatureRenderer/prepare | 186 | 0.76730 | 0.76730 | 0.00413 | 0.07547 | 0.06982 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 930 | 45.93310 | 23.36170 | 0.24695 | 4.51815 | 4.17987 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material | 186 | 1.62330 | 0.55280 | 0.00873 | 0.15967 | 0.14772 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer | 186 | 0.37500 | 0.19960 | 0.00202 | 0.03689 | 0.03412 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/material_buffer/material_match | 186 | 0.17540 | 0.17540 | 0.00094 | 0.01725 | 0.01596 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/setup_animation | 186 | 0.31320 | 0.31320 | 0.00168 | 0.03081 | 0.02850 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/CapeLayer/other_material/geometry_encode | 186 | 0.38230 | 0.38230 | 0.00206 | 0.03760 | 0.03479 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material | 955 | 6.46200 | 1.02790 | 0.03474 | 0.63563 | 0.58804 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer | 955 | 1.28450 | 0.53100 | 0.00691 | 0.12635 | 0.11689 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/material_buffer/material_match | 955 | 0.75350 | 0.75350 | 0.00405 | 0.07412 | 0.06857 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/setup_animation | 955 | 0.34310 | 0.34310 | 0.00184 | 0.03375 | 0.03122 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/body/other_material/geometry_encode | 955 | 3.80650 | 3.80650 | 0.02047 | 0.37442 | 0.34639 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material | 2332 | 9.57560 | 2.06440 | 0.05148 | 0.94189 | 0.87137 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/material_buffer | 2332 | 2.09150 | 0.76840 | 0.01124 | 0.20573 | 0.19032 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/material_buffer/material_match | 1124 | 1.32310 | 1.32310 | 0.00711 | 0.13014 | 0.12040 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/setup_animation | 2332 | 0.71030 | 0.71030 | 0.00382 | 0.06987 | 0.06464 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/other_material/geometry_encode | 2332 | 4.70940 | 4.70940 | 0.02532 | 0.46323 | 0.42855 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint | 1216 | 4.91050 | 1.14150 | 0.02640 | 0.48301 | 0.44685 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/material_buffer | 1216 | 0.76810 | 0.25390 | 0.00413 | 0.07555 | 0.06990 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/material_buffer/material_match | 186 | 0.51420 | 0.51420 | 0.00276 | 0.05058 | 0.04679 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/setup_animation | 1216 | 0.25850 | 0.25850 | 0.00139 | 0.02543 | 0.02352 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ModelFeatureRenderer/prepare/player_model/HumanoidArmorLayer/glint/geometry_encode | 1216 | 2.74240 | 2.74240 | 0.01474 | 0.26975 | 0.24956 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/TextFeatureRenderer/prepare | 372 | 6.94260 | 6.94260 | 0.03733 | 0.68290 | 0.63177 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 372 | 137.21930 | 116.87930 | 0.73774 | 13.49738 | 12.48682 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer | 1942 | 16.94810 | 0.78850 | 0.09112 | 1.66708 | 1.54226 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/main_encode | 971 | 13.56820 | 13.55590 | 0.07295 | 1.33462 | 1.23469 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer | 744 | 3.39190 | 0.29260 | 0.01824 | 0.33364 | 0.30866 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/main_encode | 372 | 3.08610 | 3.08610 | 0.01659 | 0.30356 | 0.28083 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode | 971 | 2.59140 | 1.94250 | 0.01393 | 0.25490 | 0.23581 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/glint_encode/material_match | 186 | 0.64890 | 0.64890 | 0.00349 | 0.06383 | 0.05905 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/CustomHeadLayer/glint_encode | 372 | 0.01320 | 0.01320 | 0.00007 | 0.00130 | 0.00120 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare | 372 | 20.27880 | 13.13100 | 0.10903 | 1.99470 | 1.84535 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/text_prepare | 1906 | 4.62470 | 4.62470 | 0.02486 | 0.45490 | 0.42084 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/NameTagFeatureRenderer/prepare/player_name_tag/glyph_encode | 1906 | 2.52310 | 2.52310 | 0.01357 | 0.24818 | 0.22960 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/shared_staged_upload | 186 | 32.74530 | 32.74530 | 0.17605 | 3.22095 | 2.97979 |
| frame/scene_render/world_view/world_render/terrain_prepare | 186 | 0.04500 | 0.04500 | 0.00024 | 0.00443 | 0.00409 |
| frame/scene_render/world_view/world_render/frame_graph_cpu | 186 | 319.26270 | 2.28830 | 1.71647 | 31.40383 | 29.05260 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clear | 186 | 8.43280 | 8.43280 | 0.04534 | 0.82948 | 0.76738 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/sky | 186 | 30.72920 | 30.72920 | 0.16521 | 3.02263 | 2.79633 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main | 186 | 265.02750 | 6.05260 | 1.42488 | 26.06906 | 24.11725 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/terrain_draw_cpu | 372 | 61.68430 | 61.68430 | 0.33164 | 6.06749 | 5.61321 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid | 186 | 68.63350 | 6.76320 | 0.36900 | 6.75104 | 6.24558 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/mixed | 186 | 12.37810 | 0.34760 | 0.06655 | 1.21755 | 1.12640 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ItemFeatureRenderer/execute/mixed/draw_cpu/mixed | 382 | 12.03050 | 12.03050 | 0.06468 | 1.18336 | 1.09476 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed | 186 | 23.70450 | 0.57360 | 0.12744 | 2.33166 | 2.15709 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 930 | 23.13090 | 23.13090 | 0.12436 | 2.27524 | 2.10489 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only | 372 | 25.78770 | 0.69060 | 0.13864 | 2.53657 | 2.34666 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_solid/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 1124 | 25.09710 | 25.09710 | 0.13493 | 2.46864 | 2.28381 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent | 186 | 122.35350 | 2.53790 | 0.65781 | 12.03513 | 11.13405 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed | 186 | 5.20090 | 0.16390 | 0.02796 | 0.51158 | 0.47328 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ShadowFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 186 | 5.03700 | 5.03700 | 0.02708 | 0.49546 | 0.45836 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed | 186 | 31.58280 | 0.76890 | 0.16980 | 3.10660 | 2.87400 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/mixed/draw_cpu/mixed | 1327 | 30.81390 | 30.81390 | 0.16567 | 3.03097 | 2.80404 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed | 372 | 9.81920 | 0.25080 | 0.05279 | 0.96585 | 0.89354 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/NameTagFeatureRenderer/execute/mixed/draw_cpu/mixed | 372 | 9.56840 | 9.56840 | 0.05144 | 0.94118 | 0.87072 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed | 372 | 5.18320 | 0.19730 | 0.02787 | 0.50984 | 0.47167 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed | 186 | 4.95880 | 0.13210 | 0.02666 | 0.48777 | 0.45125 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/CustomFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 186 | 4.82670 | 4.82670 | 0.02595 | 0.47477 | 0.43923 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/TextFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 186 | 4.98590 | 4.98590 | 0.02681 | 0.49043 | 0.45371 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/players_only | 186 | 4.94690 | 0.16340 | 0.02660 | 0.48659 | 0.45016 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ModelFeatureRenderer/execute/players_only/draw_cpu/players_only | 186 | 4.78350 | 4.78350 | 0.02572 | 0.47052 | 0.43529 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed | 186 | 58.12380 | 1.41820 | 0.31249 | 5.71727 | 5.28921 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_translucent/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 2418 | 56.70560 | 56.70560 | 0.30487 | 5.57777 | 5.16015 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_outline | 186 | 0.04700 | 0.04700 | 0.00025 | 0.00462 | 0.00428 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/main/feature_execute_after_terrain | 186 | 6.25660 | 6.25660 | 0.03364 | 0.61542 | 0.56934 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/clouds | 186 | 12.63860 | 12.63860 | 0.06795 | 1.24318 | 1.15010 |
| frame/scene_render/world_view/world_render/frame_graph_cpu/frame_pass/weather | 186 | 0.14630 | 0.14630 | 0.00079 | 0.01439 | 0.01331 |
| frame/scene_render/world_view/world_render/feature_frame_release | 186 | 0.84740 | 0.84740 | 0.00456 | 0.08335 | 0.07711 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu | 186 | 0.13770 | 0.12800 | 0.00074 | 0.01354 | 0.01253 |
| frame/scene_render/world_view/world_render/terrain_compile_cpu/terrain_translucency_sort | 186 | 0.00970 | 0.00970 | 0.00005 | 0.00095 | 0.00088 |
| frame/scene_render/world_view/world_render/terrain_occlusion_update | 186 | 0.11710 | 0.11710 | 0.00063 | 0.01152 | 0.01066 |
| frame/scene_render/world_view/hand_render | 186 | 17.22950 | 1.73380 | 0.09263 | 1.69476 | 1.56787 |
| frame/scene_render/world_view/hand_render/feature_render_all | 186 | 15.49570 | 0.62880 | 0.08331 | 1.52421 | 1.41009 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare | 186 | 5.18320 | 1.47800 | 0.02787 | 0.50984 | 0.47167 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/features/ModelFeatureRenderer/prepare | 186 | 1.66100 | 1.66100 | 0.00893 | 0.16338 | 0.15115 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_prepare/shared_staged_upload | 186 | 2.04420 | 2.04420 | 0.01099 | 0.20107 | 0.18602 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_solid | 186 | 0.10660 | 0.10660 | 0.00057 | 0.01049 | 0.00970 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent | 186 | 9.09920 | 0.54180 | 0.04892 | 0.89503 | 0.82802 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed | 186 | 8.55740 | 0.17780 | 0.04601 | 0.84174 | 0.77872 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_translucent/features/ModelFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 186 | 8.37960 | 8.37960 | 0.04505 | 0.82425 | 0.76254 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_after_terrain | 186 | 0.02090 | 0.02090 | 0.00011 | 0.00206 | 0.00190 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_execute_on_top | 186 | 0.02140 | 0.02140 | 0.00012 | 0.00210 | 0.00195 |
| frame/scene_render/world_view/hand_render/feature_render_all/feature_frame_release | 186 | 0.43560 | 0.43560 | 0.00234 | 0.04285 | 0.03964 |
| frame/scene_render/world_view/feature_render_all | 186 | 1.65440 | 0.33810 | 0.00889 | 0.16273 | 0.15055 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare | 186 | 1.12310 | 1.09910 | 0.00604 | 0.11047 | 0.10220 |
| frame/scene_render/world_view/feature_render_all/feature_frame_prepare/shared_staged_upload | 186 | 0.02400 | 0.02400 | 0.00013 | 0.00236 | 0.00218 |
| frame/scene_render/world_view/feature_render_all/feature_execute_solid | 186 | 0.01380 | 0.01380 | 0.00007 | 0.00136 | 0.00126 |
| frame/scene_render/world_view/feature_render_all/feature_execute_translucent | 186 | 0.01500 | 0.01500 | 0.00008 | 0.00148 | 0.00136 |
| frame/scene_render/world_view/feature_render_all/feature_execute_after_terrain | 186 | 0.00970 | 0.00970 | 0.00005 | 0.00095 | 0.00088 |
| frame/scene_render/world_view/feature_render_all/feature_execute_on_top | 186 | 0.01500 | 0.01500 | 0.00008 | 0.00148 | 0.00136 |
| frame/scene_render/world_view/feature_render_all/feature_frame_release | 186 | 0.13970 | 0.13970 | 0.00075 | 0.01374 | 0.01271 |
| frame/scene_render/world_screenshot_check | 186 | 0.00780 | 0.00780 | 0.00004 | 0.00077 | 0.00071 |
| frame/scene_render/entity_outline_postprocess | 186 | 5.59560 | 5.59560 | 0.03008 | 0.55040 | 0.50919 |
| frame/scene_render/gui_render | 186 | 70.47180 | 2.79790 | 0.37888 | 6.93186 | 6.41287 |
| frame/scene_render/gui_render/gui_prepare | 186 | 44.26840 | 4.28800 | 0.23800 | 4.35440 | 4.02838 |
| frame/scene_render/gui_render/gui_prepare/gui_pictures_prepare | 186 | 0.55460 | 0.55460 | 0.00298 | 0.05455 | 0.05047 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare | 186 | 28.86230 | 6.05260 | 0.15517 | 2.83900 | 2.62644 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all | 186 | 22.80970 | 0.53880 | 0.12263 | 2.24364 | 2.07566 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare | 186 | 8.48680 | 1.26800 | 0.04563 | 0.83479 | 0.77229 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/features/ItemFeatureRenderer/prepare | 186 | 6.17000 | 6.17000 | 0.03317 | 0.60690 | 0.56146 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_prepare/shared_staged_upload | 186 | 1.04880 | 1.04880 | 0.00564 | 0.10316 | 0.09544 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid | 186 | 13.37170 | 0.23850 | 0.07189 | 1.31529 | 1.21681 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed | 186 | 13.13320 | 0.32950 | 0.07061 | 1.29183 | 1.19511 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_solid/features/ItemFeatureRenderer/execute/unattributed/draw_cpu/unattributed | 372 | 12.80370 | 12.80370 | 0.06884 | 1.25942 | 1.16512 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_translucent | 186 | 0.11160 | 0.11160 | 0.00060 | 0.01098 | 0.01016 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_after_terrain | 186 | 0.01370 | 0.01370 | 0.00007 | 0.00135 | 0.00125 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_execute_on_top | 186 | 0.01330 | 0.01330 | 0.00007 | 0.00131 | 0.00121 |
| frame/scene_render/gui_render/gui_prepare/gui_items_prepare/feature_render_all/feature_frame_release | 186 | 0.27380 | 0.27380 | 0.00147 | 0.02693 | 0.02492 |
| frame/scene_render/gui_render/gui_prepare/gui_text_prepare | 186 | 1.43020 | 1.43020 | 0.00769 | 0.14068 | 0.13015 |
| frame/scene_render/gui_render/gui_prepare/gui_mesh_encode | 372 | 9.13330 | 9.13330 | 0.04910 | 0.89838 | 0.83112 |
| frame/scene_render/gui_render/shared_staged_upload | 186 | 2.02180 | 2.02180 | 0.01087 | 0.19887 | 0.18398 |
| frame/scene_render/gui_render/gui_draw_cpu | 186 | 21.38370 | 21.38370 | 0.11497 | 2.10338 | 1.94590 |
| frame/scene_render/gui_end_frame | 186 | 0.17630 | 0.17630 | 0.00095 | 0.01734 | 0.01604 |
| frame/shared_command_submit_cpu | 186 | 4.19740 | 4.19740 | 0.02257 | 0.41287 | 0.38196 |
| frame/presentation_cpu_wait | 186 | 42.10360 | 42.10360 | 0.22636 | 4.14146 | 3.83139 |
| frame/scene_render/world_view/world_render/feature_frame_prepare/features/ItemFeatureRenderer/prepare/player_item/PlayerItemInHandLayer/main_encode/material_match | 10 | 0.01230 | 0.01230 | 0.00007 | 0.00121 | 0.00112 |

## Sampled counters

- item_preparations: 2686
- feature_draw_submissions/ModelFeatureRenderer/mixed: 2257
- layer_calls/ArrowLayer: 955
- draw_submissions/unattributed: 3534
- layer_calls/BeeStingerLayer: 955
- feature_draw_submissions/ShadowFeatureRenderer/unattributed: 186
- layer_calls/WingsLayer: 955
- setup_animation_calls: 4689
- feature_draw_submissions/ItemFeatureRenderer/mixed: 382
- feature_draw_submissions/NameTagFeatureRenderer/mixed: 372
- player_submissions: 955
- repeated_model_state_preparations: 1774
- feature_draw_submissions/CustomFeatureRenderer/unattributed: 186
- layer_calls/ParrotOnShoulderLayer: 955
- layer_calls/PlayerItemInHandLayer: 955
- layer_calls/Deadmau5EarsLayer: 955
- name_tag_preparations: 1906
- player_extractions: 955
- layer_calls/CustomHeadLayer: 955
- draw_submissions/mixed: 3011
- layer_calls/HumanoidArmorLayer: 955
- name_tag_glyph_passes: 1906
- feature_draw_submissions/ModelFeatureRenderer/players_only: 1310
- tagged_submits: 7938
- layer_calls/CapeLayer: 955
- feature_draw_submissions/ItemFeatureRenderer/unattributed: 2790
- feature_draw_submissions/TextFeatureRenderer/unattributed: 186
- draw_submissions/players_only: 1310
- layer_calls/SpinAttackEffectLayer: 955
- model_preparations: 4689
- feature_draw_submissions/ModelFeatureRenderer/unattributed: 186

Measured recorder bookkeeping: 22.9876 ms. Timing-node overflow: 0.

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
