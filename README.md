# Affect & Register Atlas

> **Tri-Platform Agent Skill** for Claude Desktop / Code, Grok CLI, and Google Antigravity / Gemini.  
> Generates exhaustive Affect & Register Atlas reports specifying a speaker's acoustic state transformations across baseline, tired, angry, intimate, public/oratorical, intoxicated, reading, and laughing-while-talking registers with delta matrices for F0, rate, SPL, and phonation shifts.

---

## Overview

A fundamental challenge in AI voice cloning and speech synthesis is avoiding the "frozen interview take"—where a voice model produces flat, monotonic line reads regardless of narrative tension, fatigue, or intimacy.

**`affect-register-atlas`** documents and parameterizes the exact mathematical acoustic state transformations of a speaker across 8 primary physiological and communicative registers.

---

## Standard 8-State Register Taxonomy

1. **Conversational Baseline**: Neutral dialogue in a relaxed, comfortable setting.
2. **Fatigued / Sleep-Deprived**: Vocal fold dehydration, circadian low, compressed dynamic pitch ceiling.
3. **High-Arousal / Combative / Angry**: High-stakes confrontation, elevated F0, sharp sound pressure increase, pressed hyperfunctional phonation.
4. **Intimate / Confidential**: Low projection, close-proximity aside, drop in SPL, emergence of creaky fry or breathy decay.
5. **Public / Oratorical / Rally**: High-volume projection, large space acoustic impedance, elevated larynx, sustained high closed quotient.
6. **Inebriated / Sedated**: Slurred articulatory timing, reduced coordination, erratic tempo drift.
7. **Scripted / Formal Reading**: Monitored cadence reading from text, formalized boundary tones.
8. **Laughing-while-Talking**: Phonation interrupted and modulated by diaphragm spasms and glottal turbulence.

---

## Quantitative Delta Parameters

Every operational register defines concrete numerical deltas relative to baseline:
- **$\Delta\text{F0}$**: Mean pitch shift in semitones (st) and Hz.
- **$\Delta\text{SPL}$**: Sound pressure level variation in decibels (dB).
- **$\Delta\text{Rate}$**: Articulation speed multiplier (percentage).
- **$\Delta\text{Perturbation}$**: Changes in Jitter (%), Shimmer (dB), and Harmonics-to-Noise Ratio ($\text{HNR}$ in dB).
- **Glottal Closed Quotient ($\text{CQ}$)**: Adduction duration percentage and phonation type (modal, pressed, breathy, creaky fry).
- **Supraglottic Posture**: Larynx height vertical displacement (mm) and velopharyngeal port nasality.

---

## Machine Output Schema (`register_matrix.json`)

```json
{
  "$schema": "https://json-schemas.voice/affect-register-atlas.v1.json",
  "speaker_id": "SPEAKER_ID",
  "registers": {
    "baseline": {
      "f0_mean_hz": 158,
      "spl_mean_db": 68.0,
      "rate_sps": 4.5,
      "phonation": "MODAL",
      "closed_quotient": 0.52
    },
    "combative_angry": {
      "delta_f0_st": 3.4,
      "delta_spl_db": 8.5,
      "rate_multiplier": 1.15,
      "phonation": "PRESSED_HYPERFUNCTIONAL",
      "closed_quotient": 0.68,
      "spectral_tilt_boost_db": 5.0,
      "larynx_height_shift_mm": 3.5
    },
    "intimate_aside": {
      "delta_f0_st": -2.2,
      "delta_spl_db": -9.0,
      "rate_multiplier": 0.85,
      "phonation": "MILD_CREAKY",
      "closed_quotient": 0.44,
      "spectral_tilt_boost_db": -4.5,
      "larynx_height_shift_mm": -2.0
    }
  }
}
```

---

## Tri-Platform Architecture

Zero duplicate code across tools. Canonical source resides in `.agents`:
- **Canonical**: `C:\Users\<you>\.agents\skills\affect-register-atlas`
- **Claude**: `C:\Users\<you>\.claude\skills\affect-register-atlas` (NTFS Junction)
- **Grok**: `C:\Users\<you>\.grok\skills\affect-register-atlas` (NTFS Junction)
- **Antigravity**: `C:\Users\<you>\.gemini\config\skills\affect-register-atlas` (NTFS Junction)

---

## Documentation Suite

- [`HOW_TO_USE.txt`](file:///C:/Users/<you>/.agents/skills/affect-register-atlas/HOW_TO_USE.txt): Standardized user guide and prompt templates.
- [`IMPLEMENTATION_PLAN.md`](file:///C:/Users/<you>/.agents/skills/affect-register-atlas/IMPLEMENTATION_PLAN.md): Feature checklist and roadmap.
- [`App Changes Tracker.html`](file:///C:/Users/<you>/.agents/skills/affect-register-atlas/App%20Changes%20Tracker.html): Interactive visual version log.
- [`SKILL.md`](file:///C:/Users/<you>/.agents/skills/affect-register-atlas/SKILL.md): Agent system instructions and triggers.
