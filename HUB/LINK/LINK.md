# LINK 鏈圖 · write 01764

技能↔技法↔閘↔參考縮圖 SHA 的邊。

## 檔案 LINK（沙盒路徑）

- **skill_atlas** → `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/SKILL_ATLAS.json`
- **link_graph** → `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/LINK_GRAPH.json`
- **ref_atlas** → `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB_THUMBS_SHA/REF_ATLAS.json`
- **boot_branch** → `SETS/BRANCH_GROK_AGENT_THK_20261116/BOOT_BRANCH.json`
- **memory_session** → `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/MEMORY_SESSION.json`
- **readme_branch** → `SETS/BRANCH_GROK_AGENT_THK_20261116/README.md`
- **readme_drive** → `README_MEMORY_DRIVE.md`
- **teach_next** → `SHQ_TEACH_NEXT_GROK_INHERIT.md`
- **thk_canon** → `TIAO_HUAN_KOU/TIAO_HUAN_KOU_CANONICAL.md`
- **parent_boot** → `SETS/SHQ_MEMORY_RESTORE/BOOT.json`
- **intel** → `INTEL/registry.json`
- **restore_py** → `SETS/BRANCH_GROK_AGENT_THK_20261116/restore_branch.py`

## 主產線 PIPE

### PIPE_PIPI · 皮皮畫主鏈
- 口令/call: `ACTIVE ALL + 通行審查`
- 鏈: `PIPI_ACTIVE_DENSIFY → PIPI_SRC_PASS`

### PIPE_GEGE_FACE · 格格臉 dens
- 口令/call: `格格2/3/NO.EXT+3`
- 鏈: `GEGE2_SOFT → GEGE3_ROI_PASTE → GEGE_NO_EXTPLUS3`

### PIPE_PATH1E_ECC · PATH1E ECC 對位硬貼
- 口令/call: `PATH1E + ECC`
- 鏈: `A8B_TRUE → PATH1E_PLATE_ECC → ECC_ALIGN → ECC_PIN_SET`

### PIPE_THK_HERO · 跳環扣 HERO
- 口令/call: `HALF2X → R2V LOCK FLF`
- 鏈: `ECC_PIN_SET → THK_HOLD → THK_HALF2X_LOCK_FLF → R2V_LOCK_FLF`
- 禁: ['I2V_SINGLE as full film', 'OPTICAL_FLOW as dens main']

### PIPE_MEMORY · 記憶掛回
- 口令/call: `RESTORE MEMORY · SKILL_ATLAS`
- 鏈: `MEMORY_BOOT → TEACH_NEXT_BRANCH → SKILL_ATLAS → REF_ATLAS_SHA`

## 邊表（摘）

| from | kind | to | note |
|------|------|-----|------|
| `SHQ_DEFAULT_CHAIN` | compose | `PIPI_ACTIVE_DENSIFY` | ACTIVE ALL 默認含皮皮 dens |
| `SHQ_DEFAULT_CHAIN` | gates | `PIPI_SRC_PASS` | 通行審查閘 |
| `PIPI_ACTIVE_DENSIFY` | gates | `PIPI_SRC_PASS` | 出圖後必審 |
| `GEGE2_SOFT` | feeds | `GEGE3_ROI_PASTE` | soft 全幅 → ROI 羽化貼 |
| `GEGE3_ROI_PASTE` | compose | `GEGE_NO_2PLUS3` | 身I2I+臉格格3 |
| `GEGE2_SOFT` | compose | `GEGE_NO_EXTPLUS3` | EXT身色鎖+臉 |
| `GEGE2_BODY_WEAK` | gates | `PIPI_SRC_PASS` | 身弱後仍過審 |
| `face-densify-soft-roi` | implements | `GEGE2_SOFT` | server skill → 技法 |
| `face-densify-soft-roi` | implements | `GEGE3_ROI_PASTE` | server skill → 技法 |
| `PATH1E_PLATE_ECC` | depends_on | `ECC_ALIGN` | plate 後 ECC 對位硬貼 |
| `ECC_ALIGN` | feeds | `PATH1E_PLATE_ECC` | align peep 服務 PATH1E |
| `A8B_TRUE` | feeds | `PATH1E_PLATE_ECC` | A8B 身份源 → plate/ECC |
| `PATH1E_PLATE_ECC` | feeds | `ECC_PIN_SET` | ECC dens plate pins for THK |
| `AB_IC_PASTE` | feeds | `THK_HALF2X_LOCK_FLF` | 升臉 pin 可進 FLF |
| `FACE_LINE_LOCK_WNOISE` | feeds | `AB_IC_PASTE` | plate 去塑皮後 paste |
| `STITCH_HOMOGRAPHY` | alt | `ECC_ALIGN` | 幾何對位族 · stitch vs ECC |
| `OPTICAL_FLOW_MINTERPOLATE` | alt | `THK_HOLD` | K07 備選 · HOLD 後輔助 |
| `OPTICAL_FLOW_MINTERPOLATE` | kill_default | `THK_HALF2X_LOCK_FLF` | 禁當 dens 升質主鏈 |
| `THK_HOLD` | feeds | `THK_HALF2X_LOCK_FLF` | 先 HOLD 基線再 FLF hero |
| `THK_HALF2X_LOCK_FLF` | depends_on | `R2V_LOCK_FLF` | HERO 引擎 = R2V |
| `R2V_LOCK_FLF` | kill_default | `I2V_SINGLE` | K02 禁 I2V 冒全片 FLF |
| `ECC_PIN_SET` | feeds | `THK_HALF2X_LOCK_FLF` | SUB6 dens pins |
| `tiao-huan-kou` | implements | `THK_HALF2X_LOCK_FLF` | skill → 憲主鏈 |
| `MEMORY_BOOT` | feeds | `TEACH_NEXT_BRANCH` | 父 BOOT → 繼承協議 |
| `TEACH_NEXT_BRANCH` | feeds | `SKILL_ATLAS` | 繼承後掛全技能表 |
| `SKILL_ATLAS` | depends_on | `REF_ATLAS_SHA` | 技能↔縮圖 SHA |
| `pipi-src-pass-review` | implements | `PIPI_SRC_PASS` | skill → 閘 |
| `shengqing-huiwei` | implements | `SHQ_DEFAULT_CHAIN` | skill → 默認鏈 |

## 節點 → 縮圖 SHA

### A8B_TRUE
- `A8B_FIRST` sha16=`47a66d30971daca5` · `COMPARE_A8B_FIRST_TRIAL.jpg`
- `TRUE_A8B` sha16=`5b9e8b647f72d8e4` · `COMPARE_TRUE_A8B_FIRST.jpg`

### AB_IC_PASTE
- `ABIC_FACE_PEEP` sha16=`6f71a2e3d14db887` · `tmp/fei_A_0-140/HUB_FACE_TRUE_AB_IC_ON_DENS/boards/PEEP_FACE_TRUE_ON_DENS.jpg`
- `AB_FACE_PEEP` sha16=`608d71123ae3e230` · `tmp/fei_A_0-140/HUB_FACEAB_ON_DENS/boards/FACE_ONLY_AB_PEEP.jpg`

### ECC_ALIGN
- `ALIGN_WNK_PATH1E` sha16=`6f386063192f6367` · `tmp/amrs_nonhd_wnk_path1e/04_aligned_peep.jpg`
- `ALIGN_SQUARE_WNK` sha16=`434f364ecf333d45` · `tmp/amrs_square_wnk_paste/05_aligned_peep.jpg`
- `ALIGN_DBSS` sha16=`15618a8db7742057` · `tmp/dbss_5c00a572/04_aligned_peep.jpg`
- `ECC_DONOR` sha16=`c28d91b4d888704b` · `tmp/a8b_true_samepose/dens_donor_ECC_peep.jpg`

### ECC_PIN_SET
- `ECC_PIN_A0` sha16=`23223697a39f4c28` · `tmp/fei_A_0-140/src_png_thk_v2/ecc_dens_plate/flf_pins_ecc_all/pin_0000.jpg`
- `ECC_PIN_A55` sha16=`df581bb0a428d0dd` · `tmp/fei_A_0-140/src_png_thk_v2/ecc_dens_plate/flf_pins_ecc_all/pin_0055.jpg`
- `ECC_PIN_A140` sha16=`1c63e4a5327dd2c8` · `tmp/fei_A_0-140/src_png_thk_v2/ecc_dens_plate/flf_pins_ecc_all/pin_0140.jpg`

### GEGE2_BODY_WEAK
- `PIPI_BODY_WEAK` sha16=`271b63f69d1476af` · `COMPARE_BODY_WEAK_A_0003.jpg`

### GEGE2_SOFT
- `GEGE_HYBRID` sha16=`8a0bb080533226ee` · `tmp/a8b_true_samepose/COMPARE_roi_dens_id_hybrid.jpg`

### GEGE3_ROI_PASTE
- `GEGE_HYBRID` sha16=`8a0bb080533226ee` · `tmp/a8b_true_samepose/COMPARE_roi_dens_id_hybrid.jpg`

### I2V_SINGLE
- `STILL_I2V_R2V` sha16=`3778fbd9d5fea7d4` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/boards/PEEP_STILL_vs_I2V_FLF_R2V.jpg`

### PATH1E_PLATE_ECC
- `PATH1E` sha16=`f3031ed7832b82da` · `COMPARE_PATH1E_TRIAL.jpg`
- `PATH1E_B` sha16=`24eee72b24eae1dd` · `COMPARE_PATH1E_B.jpg`
- `ECC_PEEP` sha16=`c299ca8eb0a6e0f3` · `tmp/a8b_ratio_fixed/COMPARE_ecc_peeps.jpg`
- `ECC_HARDPASTE` sha16=`da7e93a3d80e2fa7` · `tmp/ecc_paste_e107/COMPARE_peep_before_after.jpg`

### PIPI_ACTIVE_DENSIFY
- `PIPI_BODY_WEAK` sha16=`271b63f69d1476af` · `COMPARE_BODY_WEAK_A_0003.jpg`

### PIPI_SRC_PASS
- `PIPI_BODY_WEAK` sha16=`271b63f69d1476af` · `COMPARE_BODY_WEAK_A_0003.jpg`

### R2V_LOCK_FLF
- `STILL_I2V_R2V` sha16=`3778fbd9d5fea7d4` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/boards/PEEP_STILL_vs_I2V_FLF_R2V.jpg`

### STITCH_HOMOGRAPHY
- `STITCH_HOMOGRAPHY` sha16=`fe56452e561774a3` · `tmp/cinema_v10/FIG6_peep_stitch_homography.png`
- `STITCH_MESH` sha16=`4608cbfd3cb6a734` · `tmp/cinema_v10/FIG6_peep_stitch_local_mesh.png`
- `STITCH_SIMILARITY` sha16=`4608cbfd3cb6a734` · `tmp/cinema_v10/FIG6_peep_stitch_similarity.png`
- `FILMSTRIP` sha16=`e98aa8a92e9dad71` · `tmp/cinema_v10/FIG5_peep_filmstrip.png`

### THK_HALF2X_LOCK_FLF
- `THK_HALF2X` sha16=`cdf18b6c762e5c88` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/boards/PEEP_HALF2X_FLF_vs_HOLD.jpg`
- `ECC_PIN_A0` sha16=`23223697a39f4c28` · `tmp/fei_A_0-140/src_png_thk_v2/ecc_dens_plate/flf_pins_ecc_all/pin_0000.jpg`
- `ECC_PIN_A140` sha16=`1c63e4a5327dd2c8` · `tmp/fei_A_0-140/src_png_thk_v2/ecc_dens_plate/flf_pins_ecc_all/pin_0140.jpg`

### THK_HOLD
- `THK_HALF2X` sha16=`cdf18b6c762e5c88` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/boards/PEEP_HALF2X_FLF_vs_HOLD.jpg`

### face-densify-soft-roi
- `GEGE_HYBRID` sha16=`8a0bb080533226ee` · `tmp/a8b_true_samepose/COMPARE_roi_dens_id_hybrid.jpg`
- `AB_FACE_PEEP` sha16=`608d71123ae3e230` · `tmp/fei_A_0-140/HUB_FACEAB_ON_DENS/boards/FACE_ONLY_AB_PEEP.jpg`

### pipi-src-pass-review
- `PIPI_BODY_WEAK` sha16=`271b63f69d1476af` · `COMPARE_BODY_WEAK_A_0003.jpg`

### tiao-huan-kou
- `THK_HALF2X` sha16=`cdf18b6c762e5c88` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/boards/PEEP_HALF2X_FLF_vs_HOLD.jpg`
- `THK_ABIC_FLF` sha16=`8bf6132847cbcd80` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/boards/PEEP_LOCK_FLF_ABIC_vs_elev.jpg`
- `THK_GRID05` sha16=`1c0a56be6c8114b3` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/boards/PEEP_GRID05_MID_elev.jpg`
- `ELEV_FACE_HALF2X` sha16=`be440b99d388dd4d` · `tmp/fei_A_0-140/HUB_TRUE_AB_IC_PERSON_FULL/trial_v2v_r2v/out/elev_face_half2x/PEEP_ELEV_FACE_HALF2X_55_85_112.jpg`

