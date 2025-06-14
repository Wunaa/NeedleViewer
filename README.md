<p align="center">
  <img src="https://github.com/Wunaa/NeedleViewer/blob/main/sys.png" width="128" height="128" alt="NeedleViewer Logo" />
</p>

<h1 align="center">NeedleViewer</h1>

<p align="center"><em>
A real-time material viewer for <strong>Sonic Frontiers</strong> and <strong>Shadow Generations</strong> modding.
</em></p>

---

**NeedleViewer** is a standalone viewer built in Godot that lets you preview **character models and materials** outside the game engine.

If you're modding *Sonic Frontiers* or *Shadow Generations*, this tool helps you check your **textures**, **packed maps**, and **material values** without having to constantly boot the game.

---

## Preview

<img src="https://github.com/Wunaa/NeedleViewer/blob/main/Preview.png" alt="NeedleViewer Preview" />

---

## What It Does

NeedleViewer simulates the behavior of shaders from the Hedgehog Engine so you can:

- ✅ Test PRM texture packing (F0, Gloss, Metal, AO)
- ✅ Preview parallax-based eyes
- ✅ Visualize fur direction maps
- ✅ Tweak fresnel/SSS settings
  
---

## Shader Accuracy

Not all shaders in NeedleViewer are equally accurate to the in-game materials. Here's what you can expect:

| Shader           | Fidelity to In-Game | Notes |
|------------------|---------------------|-------|
| `common_dpn`     | ✅ 100% Accurate     | Matches the Hedgehog Engine's behavior directly |
| `ChrEyeCDRF`     | ⚠️ Functional Match  | Not pixel-perfect, but visually works the same (shine/parallax/UV behavior) |
| `ChrSkinCDRF_dpncf` | ⚠️ Close Match   | Fresnel and base shading are accurate, but SSS is approximate |
| `Fur`            | ❌ Not Accurate      | Fur shader is custom and does **not** match in-game visuals (for preview use only) |

---

## Supported Shader Types

### `common_dpn`
> Basic material PBR  
- **Textures:** `Abd`, `PRM`, `Nrm`  
- **Floats:** `specular_intensity`, `smoothness_scale`, `metallic_scale`, `ao_intensity`  
- **Bools:** `apply_gamma_correction`

---

### `ChrSkinCDRF_dpncf`
> Character skin shader  
- **Textures:** `Abd`, `PRM`, `Nrm`, `Fal`, `CDR`  
- **Extra Floats:** `fresnel_power`, `fresnel_intensity`, `sss_blend`  
- *Note:* SSS is not identical to Hedgehog Engine but follows similar logic

---

### `Fur`
> Custom fur preview (approximate)  
- **Textures:** `Fur_Abd`, `Fur_Fal`, `Fur_Flowmap`, `Fur_Fur`, `Fur_Nrm`, `Fur_Prm`  
- **Extra Floats:** `fur_intensity`, `flow_uv_offset`  
- *Note:* This is **not** accurate to the game's fur shader. Intended for general direction previews.

---

### `ChrEyeCDRF`
> Eye shader with parallax highlight  
- **Textures:** `Abd`, `PRM`, `Nrm`, `SPT`  
- **Extra Floats:** `shine_uv_scale`, `shine_parallax_strength`, `shine_intensity`, `ao_threshold`  
- *Note:* Shine behavior is similar to the in-game version, but not exact.
