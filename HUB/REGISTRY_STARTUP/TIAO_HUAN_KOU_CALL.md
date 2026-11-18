# 跳環扣 · 立刻卡

**formal:** `TIAO_HUAN_KOU_V1` · **write:** 01765…01787+**01853**+**01859**  
**先讀：** `THK_STITCH_LIAN_V1.md`（**STITCH連** · 多窗必讀）→ `TIAO_HUAN_KOU_CANONICAL.md`（v1.6 · §17 MEDIA · **§18 STITCH連**）

## STITCH連（01853 · 使用前必讀算心法）

```text
多窗 stitch 前必算 J*(m,k)：
  score = ncc(L_end, R[k]) − λ·res − μ·k
主鎖 k*=0 m*=0 · 最多 k=1（1幀 de-overlap）
禁盲 ε=0.25/0.3/0.5s（≈k=6..12 → ncc 崩 0.91→0.64）
禁 stitch scale/crop（784→768 等）
驗：接縫 res ≈ 片內相鄰 res
詳：THK_STITCH_LIAN_V1.md
```

## 片源軸（A13 · 必先）

```text
✓ 連續正源抽 PIN（MEDIA 或指定片 continuous）
✗ hub_gege_hybrid_ext3 dens INDEX 當弧（01770 錯 · 01785 DEL）
audit: 01771 · md5 724b6744799d415f1ed2aad9aff64926
```

## 10 秒級

```text
1. ffprobe 正源 fps
2. 均抽 PIN（6 / 10 / 12…）· 自 continuous select 幀
3. 可 soft 小升清；背影 freeframe 臉 → SRC
4. hero → LOCK FLF；真姿 → HOLD
5. N>6 → 多窗 + **STITCH連**（先讀算心法）
```

## 30s+ MORPH（01786/01787 · stitch 用 01853）

```text
method: THK_MEDIA_MORPH_FLF_30_V1
K=16 · gap_out=2 · T=30 · 3 窗 eng=10
pins = round(i*(N-1)/15) for i=0..15
W0=0..5  W1=5..10  W2=10..15
stitch = THK_STITCH_LIAN_V1 · k*=0 硬切 · 禁盲ε · 禁 scale
金: b1ce1185-7d23-46ca-a3db-8a654285690d
fix peep: 7b384076-3995-42e7-9d07-eebf273dd471（01852C native784 k0）
```

更長：`K = T_out/gap_out + 1` · 同構加窗。

## 主推

| 要 | 調 |
|----|-----|
| 真姿 | **A** HOLD |
| hero 短 | **D** soft FLF SUB6 · **禁再 scale** |
| **hero 30s+** | **`THK_MEDIA_MORPH_FLF_30_V1` + STITCH連** |
| **hero 30s LOOP** | **`THK_MEDIA_MORPH_FLF_30_CLOSED_V1`（闭针）** |
| N>6 stitch | **`THK_STITCH_LIAN_V1`**（替 `THK_MULTIWIN_DEOVERLAP_STITCH_V1`） |
| 算 PIN | `thk_pin_op.py -T N -K K` |

## 禁

dens-hub 索引冒正源 · T2V 無 pin · peep 冒全片 · multi 大段重播 LIE · setpts 壓 T_natural · 01785 · **盲ε秒裁接縫** · **stitch 改分辨率**

## HEAD/TAIL vs MID（01792 · stitch 從 01853）

```text
HEAD = first_frame absolute · freeframe only AFTER
TAIL = last_frame absolute · freeframe only BEFORE
MID  = keyframe bridge · shared junction
stitch = STITCH連 k*=0/1 · 禁 full-concat 大段雙播（STITCH LIE）
正源選 PIN：指定片連續抽 · 非錯軸
```


## 閉針 LOOP（01859 · 要循環必先）

```text
method: THK_MEDIA_MORPH_FLF_30_CLOSED_V1
PREFLIGHT: P_last := P0 bitexact（THK_CLOSED_PIN_PREFLIGHT_V1）
K=16 · 3×10s · STITCH連 k*=0
金: 4a65bef6-c095-421f-bfd0-e56efde924fb
禁: 开环后再换尾／加秒封口当主法（VOID 01856-01858 主用）
循环缝: 对齐 W0 引擎头帧（THK_LOOP_ARRIVE_ENGINE_HEAD_V1）
闪电走位: 去电针 B > 硬prompt A（THK_LT_AB_TRY_V1）
```

## 一句 CALL（Grok 融会）

| 你说 | 我拉 |
|------|------|
| 跳环扣 / THK | 本卡 + CANONICAL + REGISTRY |
| STITCH连 | THK_STITCH_LIAN_V1.md 算心法 |
| 闭针 / CLOSED16 | PREFLIGHT P_last=P0 + 30s CLOSED method |
| 电30 | MEMORY_DIAN30 现行 hero CLOSED16 |
| 30s+ MORPH 开环 | THK_MEDIA_MORPH_FLF_30_V1（非 loop） |
| 30s loop | CLOSED_V1 优先 |
| 下一图 / 融会 | 读 HUB_MEMORY_01859 + 相关技（升清/外力/FOG）再提案 |

