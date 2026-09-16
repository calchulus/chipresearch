# Gerber File Coverage Guide & Production Readiness Template

## What Are Gerber Files?

Gerber files are the industry-standard format for PCB fabrication. They describe each layer of your PCB design as individual files that manufacturers use to create your board.

---

## Complete Gerber File Set

### Required Files (Must Have)

| File | Extension | Layer | Purpose |
|------|-----------|-------|---------|
| **Front Copper** | .gtl | F.Cu | Top copper traces |
| **Back Copper** | .gbl | B.Cu | Bottom copper traces |
| **Front Solder Mask** | .gts | F.Mask | Green coating (top) |
| **Back Solder Mask** | .gbs | B.Mask | Green coating (bottom) |
| **Front Silkscreen** | .gto | F.SilkS | White text/markings (top) |
| **Back Silkscreen** | .gbo | B.SilkS | White text/markings (bottom) |
| **Board Outline** | .gko | Edge.Cuts | Board shape and size |
| **Drill File** | .drl | N/A | Hole locations and sizes |

### Optional Files (May Need)

| File | Extension | Layer | Purpose |
|------|-----------|-------|---------|
| **Front Paste** | .gtp | F.Paste | Solder paste stencil (top) |
| **Back Paste** | .gbp | B.Paste | Solder paste stencil (bottom) |
| **Front Fabrication** | .gm1 | F.Fab | Assembly drawing (top) |
| **Back Fabrication** | .gm2 | B.Fab | Assembly drawing (bottom) |
| **Assembly Drawing** | .gm3 | F.Fab | Component placement |
| **Paste Stencil** | .gtp | F.Paste | For SMD assembly |

### For Multi-Layer Boards (4+ layers)

| File | Extension | Layer | Purpose |
|------|-----------|-------|---------|
| **Inner Layer 1** | .gl2 | In1.Cu | Inner copper layer 1 |
| **Inner Layer 2** | .gl3 | In2.Cu | Inner copper layer 2 |
| **Inner Layer 3** | .gl4 | In3.Cu | Inner copper layer 3 |
| **Inner Layer 4** | .gl5 | In4.Cu | Inner copper layer 4 |

---

## What to Look For in Each File

### 1. Front Copper (.gtl)

**Check for:**
| Item | What to Look For | Acceptable |
|------|------------------|------------|
| **Trace width** | Minimum trace width | ≥6mil (0.15mm) |
| **Trace spacing** | Minimum spacing between traces | ≥6mil (0.15mm) |
| **Copper pour** | Ground/power plane coverage | >80% fill |
| **Thermal relief** | Connections to pads | Proper relief pattern |
| **Annular ring** | Via/pad ring width | ≥4mil (0.1mm) |
| **Acid traps** | Sharp angles in traces | No acute angles <90° |
| **Copper balance** | Even distribution | No large copper-free areas |

**Common defects:**
- Missing traces
- Traces too close together
- Copper pours with gaps
- Isolated copper islands

### 2. Back Copper (.gbl)

**Same checks as front copper**
- Verify layer is not empty (unless 1-layer board)
- Check routing direction (usually perpendicular to front)

### 3. Front Solder Mask (.gts)

**Check for:**
| Item | What to Look For | Acceptable |
|------|------------------|------------|
| **Mask openings** | Pads have proper openings | All pads exposed |
| **Solder mask dams** | Between fine-pitch pads | ≥4mil (0.1mm) |
| **Mask bridging** | Unwanted mask on pads | None |
| **Clearance to pads** | Mask-to-pad clearance | 2-4mil (0.05-0.1mm) |
| **Test point coverage** | Test points exposed | All test points open |

**Common defects:**
- Missing mask openings on pads
- Mask on vias (should be open for test points)
- Mask bridging between fine-pitch pads

### 4. Back Solder Mask (.gbs)

**Same checks as front solder mask**
- Verify layer is not empty (unless 1-layer board)

### 5. Front Silkscreen (.gto)

**Check for:**
| Item | What to Look For | Acceptable |
|------|------------------|------------|
| **Text legibility** | All text readable | Minimum 30mil height |
| **Reference designators** | All components labeled | 100% coverage |
| **Polarity markings** | Diodes, ICs marked | Correct orientation |
| **Logo** | Company logo present | Clear and centered |
| **Version number** | Board revision marked | Present |
| **Date code** | Manufacturing date | Present |

**Common defects:**
- Text overlapping pads
- Missing reference designators
- Illegible text
- Polarity markings missing

### 6. Back Silkscreen (.gbo)

**Same checks as front silkscreen**
- Verify layer is not empty (unless 1-layer board)
- Check for bottom-side component labels

### 7. Board Outline (.gko)

**Check for:**
| Item | What to Look For | Acceptable |
|------|------------------|------------|
| **Closed outline** | No gaps in outline | 100% closed |
| **Dimensions** | Correct board size | Matches design |
| **Mounting holes** | All holes present | Correct diameter |
| **Corner radius** | Rounded corners | 0-5mm radius |
| **Complex shapes** | Cutouts, slots | Properly defined |
| **Panel frame** | If panelized | Breakout tabs defined |

**Common defects:**
- Open outline (gaps)
- Incorrect dimensions
- Missing mounting holes
- Overlapping lines

### 8. Drill File (.drl)

**Check for:**
| Item | What to Look For | Acceptable |
|------|------------------|------------|
| **Format** | Excellon format | Metric, leading zero |
| **Units** | Metric (mm) | Consistent |
| **Hole sizes** | All sizes present | Match design |
| **Hole count** | Total holes | Matches design |
| **Plated holes** |PTH holes marked | Correct |
| **Non-plated holes** | NPTH holes marked | Correct |
| **Slot holes** | Oval/oblong holes | Properly defined |
| **Drill hits** | No missing holes | 100% coverage |

**Common defects:**
- Missing holes
- Wrong hole sizes
- Plated/non-plated mismatch
- Slots not defined

---

## Production Readiness Checklist

### Level 1: Basic (Prototype)

| # | Check | Status | Notes |
|---|-------|--------|-------|
| 1 | All 8 required files present | ☐ | |
| 2 | File extensions correct | ☐ | |
| 3 | Board outline closed | ☐ | |
| 4 | No empty layers | ☐ | |
| 5 | Drill file present | ☐ | |

**Pass Criteria:** All 5 checks pass

### Level 2: Standard (Production)

| # | Check | Status | Notes |
|---|-------|--------|-------|
| 1 | All Level 1 checks pass | ☐ | |
| 2 | Trace width ≥6mil | ☐ | |
| 3 | Trace spacing ≥6mil | ☐ | |
| 4 | Annular ring ≥4mil | ☐ | |
| 5 | Solder mask clearance correct | ☐ | |
| 6 | Silkscreen legible | ☐ | |
| 7 | All pads have mask openings | ☐ | |
| 8 | Drill format correct | ☐ | |
| 9 | No acid traps | ☐ | |
| 10 | Copper balance >80% | ☐ | |

**Pass Criteria:** All 10 checks pass

### Level 3: High-Reliability (Automotive/Medical)

| # | Check | Status | Notes |
|---|-------|--------|-------|
| 1 | All Level 2 checks pass | ☐ | |
| 2 | Trace width ≥8mil | ☐ | |
| 3 | Trace spacing ≥8mil | ☐ | |
| 4 | Annular ring ≥6mil | ☐ | |
| 5 | Drill-to-copper clearance ≥15mil | ☐ | |
| 6 | Impedance control specified | ☐ | |
| 7 | Stackup defined | ☐ | |
| 8 | Material specification | ☐ | |
| 9 | Surface finish specified | ☐ | |
| 10 |IPC class defined | ☐ | |

**Pass Criteria:** All 10 checks pass

---

## Measurement Template

### Gerber File Validation Report

**Project Name:** _______________
**Date:** _______________
**Version:** _______________

### File Inventory

| File | Extension | Present | Size | Status |
|------|-----------|---------|------|--------|
| Front Copper | .gtl | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Back Copper | .gbl | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Front Solder Mask | .gts | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Back Solder Mask | .gbs | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Front Silkscreen | .gto | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Back Silkscreen | .gbo | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Board Outline | .gko | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |
| Drill File | .drl | ☐ Yes ☐ No | _____ KB | ☐ Pass ☐ Fail |

### Layer Analysis

| Layer | Trace Count | Min Width | Max Width | Spacing | Status |
|-------|-------------|-----------|-----------|---------|--------|
| Front Copper | _____ | _____ mil | _____ mil | _____ mil | ☐ Pass ☐ Fail |
| Back Copper | _____ | _____ mil | _____ mil | _____ mil | ☐ Pass ☐ Fail |

### Drill Analysis

| Parameter | Value | Acceptable | Status |
|-----------|-------|------------|--------|
| Total holes | _____ | _____ | ☐ Pass ☐ Fail |
| Min hole size | _____ mil | _____ mil | ☐ Pass ☐ Fail |
| Max hole size | _____ mil | _____ mil | ☐ Pass ☐ Fail |
| PTH count | _____ | _____ | ☐ Pass ☐ Fail |
| NPTH count | _____ | _____ | ☐ Pass ☐ Fail |
| Slot count | _____ | _____ | ☐ Pass ☐ Fail |

### Board Outline Analysis

| Parameter | Value | Acceptable | Status |
|-----------|-------|------------|--------|
| Width | _____ mm | _____ mm | ☐ Pass ☐ Fail |
| Height | _____ mm | _____ mm | ☐ Pass ☐ Fail |
| Mounting holes | _____ | _____ | ☐ Pass ☐ Fail |
| Corner radius | _____ mm | _____ mm | ☐ Pass ☐ Fail |

### Defect Summary

| Defect Type | Count | Severity | Action |
|-------------|-------|----------|--------|
| Missing files | _____ | Critical | |
| Open outline | _____ | Critical | |
| Trace too thin | _____ | Major | |
| Spacing violation | _____ | Major | |
| Missing mask | _____ | Major | |
| Drill errors | _____ | Critical | |
| Silkscreen issues | _____ | Minor | |

### Final Assessment

| Level | Pass/Fail | Notes |
|-------|-----------|-------|
| Level 1 (Prototype) | ☐ Pass ☐ Fail | |
| Level 2 (Production) | ☐ Pass ☐ Fail | |
| Level 3 (High-Reliability) | ☐ Pass ☐ Fail | |

**Overall Status:** ☐ Ready for Manufacturing ☐ Needs Revision ☐ Rejected

**Reviewer:** _______________
**Date:** _______________
**Signature:** _______________

---

## Common Gerber File Issues

### Critical Issues (Must Fix)

| Issue | Description | Fix |
|-------|-------------|-----|
| **Open outline** | Board outline has gaps | Close the outline |
| **Missing layers** | Required layers not exported | Re-export all layers |
| **Wrong format** | Not RS-274X format | Re-export in correct format |
| **Drill errors** | Missing/wrong holes | Verify drill file |
| **Copper shorts** | Traces shorted together | Fix routing |

### Major Issues (Should Fix)

| Issue | Description | Fix |
|-------|-------------|-----|
| **Trace too thin** | Below minimum width | Widen traces |
| **Spacing violation** | Traces too close | Increase spacing |
| **Missing mask** | Pads not exposed | Add mask openings |
| **Acid traps** | Sharp angles in traces | Reroute traces |
| **Copper imbalance** | Uneven copper distribution | Add copper pours |

### Minor Issues (Can Fix Later)

| Issue | Description | Fix |
|-------|-------------|-----|
| **Illegible text** | Silkscreen too small | Increase text size |
| **Missing labels** | Components unlabeled | Add reference designators |
| **Cosmetic defects** | Minor visual issues | Clean up silkscreen |

---

## How to Validate Gerber Files

### Using KiCad

1. Open KiCad PCB editor
2. File → Fabrication Outputs → Gerbers
3. Export all layers
4. Use Gerber Viewer to inspect

### Using Gerber Viewer (Free)

1. **Gerber Viewer**: https://gerbview.io/
2. **EasyEDA Gerber Viewer**: https://easyeda.com/gerber-viewer
3. **Altium 365 Viewer**: https://365.altium.com/

### Using Command Line

```bash
# Check Gerber file format
head -20 board.gtl

# Check drill file
head -20 board.drl

# Count holes in drill file
grep -c "G81" board.drl
```

---

## Production Readiness Score

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| File Completeness | 25% | _____ | _____ |
| Trace Compliance | 20% | _____ | _____ |
| Drill Compliance | 20% | _____ | _____ |
| Mask Compliance | 15% | _____ | _____ |
| Silkscreen Quality | 10% | _____ | _____ |
| Board Outline | 10% | _____ | _____ |
| **TOTAL** | 100% | _____ | _____ |

**Scoring:**
- 90-100%: Production Ready
- 80-89%: Minor Revisions Needed
- 70-79%: Major Revisions Needed
- <70%: Redesign Required
