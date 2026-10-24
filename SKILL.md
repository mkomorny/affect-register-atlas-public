---
name: affect-register-atlas
description: Generates exhaustive Affect & Register Atlas reports specifying a speaker's acoustic state transformations across baseline, tired, angry, intimate, public/oratorical, intoxicated, reading, and laughing-while-talking registers with delta matrices for F0, rate, SPL, and phonation shifts. Trigger with 'affect atlas for', 'register matrix of', 'map emotional acoustics for', or '/affect-register-atlas'.
disable-model-invocation: true
---

# Affect & Register Atlas

## Purpose & Scope

This skill documents and models the **acoustic state transformations** of a speaker across distinct emotional, physiological, and communicative environments. While baseline profiles describe a single "interview take," real human voices radically reshape their pitch, volume, spectral tilt, phonation type, and resonance when shifting between intimacy, confrontation, fatigue, or public projection.

This skill owns:
- Standard 8-state register transformation taxonomy
- Concrete numerical delta matrix: ΔF0 (Hz/st), Δrate (%), ΔSPL (dB), ΔHNR (dB)
- Phonation state shifts (transitions between modal, pressed, creak, and breathy phonation)
- Supraglottic and vocal tract posture adjustments per register
- Environmental and emotional trigger conditions for state transitions

This skill does **not** own linguistic personality traits (owned by `speaking-personality-profile`) or non-speech bodily noises (owned by `non-speech-vocalization-library`).

---

## Activation Triggers

Activate automatically when:
- User asks for emotional shifts, vocal registers, or situational voice adaptations (e.g., *"affect atlas for [speaker]"*, *"how does [subject] sound when angry vs tired?"*).
- User triggers `/affect-register-atlas [subject]`.
- Directing neural TTS or voice conversion models to synthesize emotional scenes (rage, intimacy, exhaustion, triumph).
- Parameterizing game or dialogue systems requiring dynamic voice state switching.

---

## Mandatory Report Schema & Structure

### 1. Register Taxonomy Definitions
Define baseline and 7 primary operational registers:
1. **Conversational Baseline:** Neutral dialogue in comfortable setting.
2. **Fatigued / Sleep-Deprived:** Vocal exhaustion, circadian low, post-loading depletion.
3. **High-Arousal / Combative / Angry:** Confrontational, high-stakes defense or attack.
4. **Intimate / Confidential:** Low-projection, close-proximity aside or private disclosure.
5. **Public / Oratorical / Rally:** High-volume projection, large space, crowd engagement.
6. **Inebriated / Sedated:** Altered motor control, slurred articulation, slowed timing.
7. **Scripted / Formal Reading:** Monitored delivery reading aloud from prepared text.
8. **Laughing-while-Talking:** Phonation modulated by concurrent respiratory spasms.

### 2. Quantitative Acoustic Transformation Matrix
For each register, specify exact deltas relative to conversational baseline:
- **ΔF0:** Shift in mean fundamental frequency (Hz and semitones).
- **ΔF0 Range:** Expansion or compression of pitch excursions (st).
- **ΔSPL:** Change in sound pressure level (dB).
- **ΔRate:** Articulation rate modification (percentage multiplier).
- **ΔPerturbation:** Shift in jitter (%), shimmer (dB), and HNR (dB).

### 3. Glottal Source & Phonation Transitions
- **Closed Quotient (Qc / CQ %):** Glottal adduction duration change across states.
- **Phonation Class:** Shift to pressed (hyperfunctional), breathy (hypofunctional), or creaky/fry.
- **Spectral Tilt (Alpha Ratio):** High-frequency boost or roll-off in dB.

### 4. Supraglottic & Articulatory Adjustments
- **Laryngeal Elevation:** Vertical larynx displacement (mm up or down).
- **Velopharyngeal Port:** Nasality shifts (hyponasal twang vs. hypernasal leakage).
- **Vowel Space Expansion/Reduction:** Articulatory centralization factor.

### 5. Transition Latency & Trigger Dynamics
- **Switching Speed:** Time required to shift into and out of each register (ms).
- **Carryover / Recovery:** Vocal recovery time following prolonged hyperfunctional states.

---

## Machine Output Block

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
    },
    "fatigued_exhausted": {
      "delta_f0_st": -1.8,
      "delta_spl_db": -3.5,
      "rate_multiplier": 0.88,
      "phonation": "BREATHY_CREAK",
      "closed_quotient": 0.46,
      "hnr_delta_db": -3.2,
      "larynx_height_shift_mm": -1.0
    },
    "public_oratorical": {
      "delta_f0_st": 2.8,
      "delta_spl_db": 10.0,
      "rate_multiplier": 0.95,
      "phonation": "PRESSED_PROJECTED",
      "closed_quotient": 0.65,
      "spectral_tilt_boost_db": 6.5,
      "larynx_height_shift_mm": 2.0
    }
  }
}
```

---

## Biometric & Personality Crosswalk

| Register Parameter | Core Biometric Section | Personality Profile Section | Synthesis Compiler Target |
| :--- | :--- | :--- | :--- |
| ΔF0 & ΔSPL | §1 Mean F0 & §5 Loudness | §4.2 Emotional Expression | Prosody Pitch & Volume Gain |
| Phonation Shift | §1 Glottal Source & Phonation | §4.1 Dominant Attitude | Klatt OQ / Breathiness / Glottal Flow |
| Rate Multiplier | §5 Speaking Rate & Rhythm | §2.3 Enthusiasm & Positivity | Synthesis Speed Parameter |
| Nasality Shift | §3 Resonance Profile | §5.3 Repair Strategies | Nasal Pole-Zero Filter Modulation |

---

## Calibration Reference Example: Queens Orator Baseline

- **Public Oratorical Register:** F0 shifts upward to ~178 Hz (+2.2 st); SPL peaks at +10 dB above baseline; Closed Quotient spikes to 0.66 producing intense pressed phonation and high-frequency projection.
- **Intimate / Conspiratorial Register:** F0 drops to ~138 Hz (-2.4 st); SPL drops by -8 to -11 dB; vocal fold vibration exhibits low-frequency creaky fry; used strategically for dramatic storytelling asides.
- **Fatigue Register (Late Rally):** Roughness increases (HNR drops by -4 dB); pitch ceiling compresses downwards by 3 semitones; voice acquires gravelly raspy edge due to laryngeal dehydration.

---

## Generation Rules

1. Define all state modifications as explicit mathematical deltas (st, dB, %) relative to baseline.
2. Specify exact glottal closed quotient (CQ) and phonation classification for every register.
3. Every profile must output the machine-readable `register_matrix.json` block.
