# STITCH連 · THK_STITCH_LIAN_V1

**formal:** `THK_STITCH_LIAN_V1` · **zh:** STITCH連  
**write:** 01853 · **asof:** 2026-11-17T19:39+08  
**parent:** 跳環扣 TIAO_HUAN_KOU_V1 · **gold fix:** 01852 / DIAN30_THK_MORPH30_FIX

> **使用跳環扣做多窗／30s+ MORPH 前 · 必先讀本卡。**  
> 接縫不順 = 算錯 k，不是「多裁一點就好」。

---

## 一句

多窗 LOCK FLF 硬接時：**在 shared pin 上 k=0（或最多 1 幀）硬切**；  
**禁盲 ε 秒裁**；**禁 scale 改解析**；接縫 residual 必須 ≈ 片內相鄰幀 residual。

---

## 算心法（必背）

### 符號

| 符 | 義 |
|----|----|
| L | 左窗末幀序列 `left_tail` |
| R | 右窗首幀序列 `right_head` |
| m | 左窗末裁幀數（通常 0） |
| k | 右窗首丟幀數 |
| J | 接縫：`L[-(1+m)]` 接 `R[k]` |
| res | 兩幀 mean abs pixel residual |
| ncc | 灰階 NCC |

### 搜 J*

```text
for m in 0..Mmax:          # 建議 Mmax=6
  for k in 0..Kmax:        # 建議 Kmax=36（~1.5s@24fps）
    score = ncc(L[-(1+m)], R[k]) - λ·res - μ·k - ν·m
取 score 最大 → (m*, k*)
```

### 決策表（01852 實測 · 24fps）

| k | t≈ | ncc(W0末,W1[k]) | res | 判 |
|---|-----|-----------------|-----|----|
| **0** | 0 | **0.907** | **16.0** | **順 · 主鎖** |
| 1 | 1/24s | ~0.84 | ~22 | 可 · A7-S 去重 1 幀 |
| 6 | **0.25s** | **0.64** | **37** | **斷 · 禁** |
| 12 | 0.5s | 0.50 | 47 | 斷 |

片內相鄰幀 residual ≈ **16–17**  
→ **接縫 res 必須落在片內步長帶**；遠高 = JUMP。

### 主鎖規則

```text
THK-SL-0  先算 J*（ncc/res 搜）· 禁憑感覺裁秒
THK-SL-1  主鎖 k*=0 · m*=0（shared pin 硬切）
THK-SL-2  若憲要「junction 只出現一次」→ 最多 k=1（1 幀 de-overlap）
THK-SL-3  禁 ε∈{0.25,0.3,0.5}s 盲裁（≈k=6..12）· 舊 A11「ε at J」作廢重釋
THK-SL-4  禁 stitch 時 scale/crop 改寬高（如 784→768）· 原生引擎分辨率直通
THK-SL-5  禁 setpts 壓 T_natural
THK-SL-6  驗收：cut 左右 ncc ≥ 片內 ncc−0.05 · res ≤ 片內 res×1.3
THK-SL-7  可選 0.3–0.5s xfade 只做視覺柔 · 不取代算 J* · 不代替 k 決策
```

### 錯路（VOID）

| 錯 | 寫 | 果 |
|----|-----|-----|
| 盲 ε=0.25s de-overlap | 01850 舊 stitch | ncc 0.91→0.64 · FRAME 不順 |
| 784→768 force crop | 同 | 二次損 · 偽降維 |
| full-concat 後 setpts 壓長 | A11 舊 | T 假 |

---

## 工序（多窗 stitch）

```text
1. 各窗 ENGINE 出片 · 同 fps · 同 w×h（記錄 native）
2. 抽 left_tail / right_head 各 ≥48 幀（串流 · 禁整片入 RAM）
3. 跑 J* 搜 → 寫 RECEIPT m,k,ncc,res
4. ffmpeg：
   - 左窗：trim end 僅當 m*>0
   - 右窗：trim start = k*/fps 僅當 k*>0
   - 全程 setsar=1,fps=<src>,format=yuv420p
   - **無 scale · 無 crop · 無 pad 改畫幅**
5. concat filter · 硬切
6. 驗 cut 左右 ncc/res vs 片內步
```

### ffmpeg 形（k=0 主鎖）

```bash
# 每窗只統一 sar/fps/format · 不改幾何
ffmpeg -i Wi.mp4 -vf "setsar=1,fps=24,format=yuv420p" -an -c:v libx264 -crf 18 Si.mp4
# concat
ffmpeg -i S0 -i S1 -i S2 -filter_complex \
  "[0:v]setsar=1,format=yuv420p[v0];[1:v]...[v1];[2:v]...[v2];
   [v0][v1][v2]concat=n=3:v=1:a=0[outv]" \
  -map "[outv]" -r 24 -c:v libx264 -crf 18 out.mp4
```

---

## 與 A7-S / A11 關係

| 舊名 | 新釋（STITCH連） |
|------|------------------|
| A7-S de-overlap | = 本卡 · **k 由算得 · 默認 0 最多 1 幀** |
| A11 ε at J | **ε 秒禁作默認**；ε 若出現必須 = k*/fps 且 k* 已搜 |
| STITCH LIE | full-concat 雙播大段重播仍禁；**k=0 在 pin 上 1 幀級相接 ≠ LIE** |

method_id：`THK_STITCH_LIAN_V1`  
alias：`STITCH連` · 替換／約束 `THK_MULTIWIN_DEOVERLAP_STITCH_V1`

---

## 6PIN 單窗

無 stitch → **不套本卡**；成片 **禁再 scale**（同 THK-SL-4）。

---

## 記憶一句

> **接縫 k 要算，不盲裁秒；res≈片內步才算連；分辨率原生直通。**

*write 01853 · gold 01852 ncc curve · 入跳環扣必讀*
