# LINK_GRAPH · BRANCH_THK HUB

- schema: `LINK_GRAPH_V1`
- write_id: `01764`
- nodes: 31 · links: 28

## Pipelines
- **PIPE_PIPI** (皮皮畫主鏈): PIPI_ACTIVE_DENSIFY → PIPI_SRC_PASS
- **PIPE_GEGE_FACE** (格格臉 dens): GEGE2_SOFT → GEGE3_ROI_PASTE → GEGE_NO_EXTPLUS3
- **PIPE_PATH1E_ECC** (PATH1E ECC 對位硬貼): A8B_TRUE → PATH1E_PLATE_ECC → ECC_ALIGN → ECC_PIN_SET
- **PIPE_THK_HERO** (跳環扣 HERO): ECC_PIN_SET → THK_HOLD → THK_HALF2X_LOCK_FLF → R2V_LOCK_FLF
- **PIPE_MEMORY** (記憶掛回): MEMORY_BOOT → TEACH_NEXT_BRANCH → SKILL_ATLAS → REF_ATLAS_SHA

## Edges
| id | from | kind | to | note |
|----|------|------|-----|------|
| L000 | `SHQ_DEFAULT_CHAIN` | compose | `PIPI_ACTIVE_DENSIFY` | ACTIVE ALL 默認含皮皮 dens |
| L001 | `SHQ_DEFAULT_CHAIN` | gates | `PIPI_SRC_PASS` | 通行審查閘 |
| L002 | `PIPI_ACTIVE_DENSIFY` | gates | `PIPI_SRC_PASS` | 出圖後必審 |
| L003 | `GEGE2_SOFT` | feeds | `GEGE3_ROI_PASTE` | soft 全幅 → ROI 羽化貼 |
| L004 | `GEGE3_ROI_PASTE` | compose | `GEGE_NO_2PLUS3` | 身I2I+臉格格3 |
| L005 | `GEGE2_SOFT` | compose | `GEGE_NO_EXTPLUS3` | EXT身色鎖+臉 |
| L006 | `GEGE2_BODY_WEAK` | gates | `PIPI_SRC_PASS` | 身弱後仍過審 |
| L007 | `face-densify-soft-roi` | implements | `GEGE2_SOFT` | server skill → 技法 |
| L008 | `face-densify-soft-roi` | implements | `GEGE3_ROI_PASTE` | server skill → 技法 |
| L009 | `PATH1E_PLATE_ECC` | depends_on | `ECC_ALIGN` | plate 後 ECC 對位硬貼 |
| L010 | `ECC_ALIGN` | feeds | `PATH1E_PLATE_ECC` | align peep 服務 PATH1E |
| L011 | `A8B_TRUE` | feeds | `PATH1E_PLATE_ECC` | A8B 身份源 → plate/ECC |
| L012 | `PATH1E_PLATE_ECC` | feeds | `ECC_PIN_SET` | ECC dens plate pins for THK |
| L013 | `AB_IC_PASTE` | feeds | `THK_HALF2X_LOCK_FLF` | 升臉 pin 可進 FLF |
| L014 | `FACE_LINE_LOCK_WNOISE` | feeds | `AB_IC_PASTE` | plate 去塑皮後 paste |
| L015 | `STITCH_HOMOGRAPHY` | alt | `ECC_ALIGN` | 幾何對位族 · stitch vs ECC |
| L016 | `OPTICAL_FLOW_MINTERPOLATE` | alt | `THK_HOLD` | K07 備選 · HOLD 後輔助 |
| L017 | `OPTICAL_FLOW_MINTERPOLATE` | kill_default | `THK_HALF2X_LOCK_FLF` | 禁當 dens 升質主鏈 |
| L018 | `THK_HOLD` | feeds | `THK_HALF2X_LOCK_FLF` | 先 HOLD 基線再 FLF hero |
| L019 | `THK_HALF2X_LOCK_FLF` | depends_on | `R2V_LOCK_FLF` | HERO 引擎 = R2V |
| L020 | `R2V_LOCK_FLF` | kill_default | `I2V_SINGLE` | K02 禁 I2V 冒全片 FLF |
| L021 | `ECC_PIN_SET` | feeds | `THK_HALF2X_LOCK_FLF` | SUB6 dens pins |
| L022 | `tiao-huan-kou` | implements | `THK_HALF2X_LOCK_FLF` | skill → 憲主鏈 |
| L023 | `MEMORY_BOOT` | feeds | `TEACH_NEXT_BRANCH` | 父 BOOT → 繼承協議 |
| L024 | `TEACH_NEXT_BRANCH` | feeds | `SKILL_ATLAS` | 繼承後掛全技能表 |
| L025 | `SKILL_ATLAS` | depends_on | `REF_ATLAS_SHA` | 技能↔縮圖 SHA |
| L026 | `pipi-src-pass-review` | implements | `PIPI_SRC_PASS` | skill → 閘 |
| L027 | `shengqing-huiwei` | implements | `SHQ_DEFAULT_CHAIN` | skill → 默認鏈 |

## File anchors (sandbox)
- **skill_atlas**: `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/SKILL_ATLAS.json`
- **link_graph**: `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/LINK_GRAPH.json`
- **ref_atlas**: `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB_THUMBS_SHA/REF_ATLAS.json`
- **boot_branch**: `SETS/BRANCH_GROK_AGENT_THK_20261116/BOOT_BRANCH.json`
- **memory_session**: `SETS/BRANCH_GROK_AGENT_THK_20261116/MEMORY/MEMORY_SESSION.json`
- **readme_branch**: `SETS/BRANCH_GROK_AGENT_THK_20261116/README.md`
- **readme_drive**: `README_MEMORY_DRIVE.md`
- **teach_next**: `SHQ_TEACH_NEXT_GROK_INHERIT.md`
- **thk_canon**: `TIAO_HUAN_KOU/TIAO_HUAN_KOU_CANONICAL.md`
- **parent_boot**: `SETS/SHQ_MEMORY_RESTORE/BOOT.json`
- **intel**: `INTEL/registry.json`
- **restore_py**: `SETS/BRANCH_GROK_AGENT_THK_20261116/restore_branch.py`
- **hub**: `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB`
- **hub_link**: `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB/LINK/LINK_GRAPH.json`
- **hub_link_md**: `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB/LINK/LINK.md`
- **hub_manifest**: `SETS/BRANCH_GROK_AGENT_THK_20261116/HUB/HUB_MANIFEST.json`
