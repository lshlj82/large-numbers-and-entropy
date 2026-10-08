# Large Systems and Entropy, Interactively

An interactive, single-page web demo of the statistics of very large systems: very large numbers and Stirling's approximation, the extreme sharpness of multiplicity peaks, the multiplicity of an ideal gas, and entropy, from S = k<sub>B</sub> ln Ω to the Sackur–Tetrode equation, the entropy of mixing, and the Gibbs paradox.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 2, The Second Law, Sections 2.4 to 2.6). It follows the demo for Sections 2.1 to 2.3 (microstates and macrostates).

## What's inside

**Very large numbers.** Small, large, and very large numbers, why 10<sup>23</sup> + 23 ≈ 10<sup>23</sup> and 10<sup>10<sup>23</sup></sup> × 10<sup>23</sup> ≈ 10<sup>10<sup>23</sup></sup>, and the logarithm as the tool for handling them. Stirling's approximation, N! ≈ N<sup>N</sup>e<sup>−N</sup>√(2πN) and ln N! ≈ N ln N − N, with a chart of their errors from N = 1 to 10<sup>6</sup> that reproduces the lecture's table (0.83% and 13.8% at N = 10; 0.083% and 0.89% at N = 100).

**How sharp is the peak?** The large Einstein solid, Ω ≈ (eq/N)<sup>N</sup>, and two such solids sharing energy, whose multiplicity is the Gaussian Ω<sub>max</sub> e<sup>−N(2x/q)²</sup>. A slider takes N from 1 to 10<sup>24</sup>, drawing the exact multiplicity (up to 10<sup>6</sup>) and the Gaussian against the full axis, with the peak's width as a fraction of the axis. For N = 10<sup>20</sup>, drawing the peak 1 cm wide needs an axis of 10<sup>5</sup> km, about three times around the Earth.

**The ideal gas.** Counting states in position and momentum space, the uncertainty principle, hyperspheres, and the 1/N! for indistinguishable molecules, leading to Ω = f(N)V<sup>N</sup>U<sup>3N/2</sup>. A rotatable 3D surface of the total multiplicity of two gases over every division of energy and volume shows the peak narrowing into a spike as N grows. A simulation of molecules in a box counts how often they are all in the left half, compared with the prediction 1/2<sup>N</sup> and the binomial distribution.

**Entropy.** S = k<sub>B</sub> ln Ω, its additivity, the second law as "entropy tends to increase," and Maxwell's demon. The Sackur–Tetrode equation for the molar entropy of the noble gases at any temperature and pressure (126 J/K for a mole of helium at room temperature and atmospheric pressure). An experiment with a removable partition compares free expansion (ΔS = Nk<sub>B</sub> ln 2 with no heat or work), mixing two different gases (ΔS = 2Nk<sub>B</sub> ln 2), and "mixing" the same gas (ΔS = 0 only with the 1/N!), resolving the Gibbs paradox; plus reversible and irreversible processes.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The 3D surface is drawn with a lightweight hand-written projection (no 3D library); its grid packs more points near the peak as N grows, so even a very narrow spike is resolved.
- Factorials and multiplicities are computed through the logarithm of the gamma function (Lanczos approximation, accurate to about 13 digits), so the exact multiplicity can be drawn for systems of up to a million oscillators.
- The "all on the left" simulation uses noninteracting molecules bouncing in a box; the fraction of time they are all on the left converges to 1/2<sup>N</sup>.
- The Sackur–Tetrode values use the atomic masses of He, Ne, Ar, Kr, and Xe with V = nRT/P and U = (3/2)nRT; argon's 154.9 J/K at 300 K matches its measured standard entropy closely.
- The animations pause when scrolled off screen and are reduced when the system asks for reduced motion.
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode: it follows `prefers-color-scheme`, and a sun/moon button in the top-right corner switches by hand, and the choice is remembered across pages; and is responsive down to phone widths.

## Caveats

- The 3D multiplicity surface of two gases plots the factor (V<sub>A</sub>V<sub>B</sub>)<sup>N</sup>(U<sub>A</sub>U<sub>B</sub>)<sup>3N/2</sup> relative to its maximum; the prefactor f(N) cancels.
- The partition experiment illustrates the entropy changes with simple moving dots; the ΔS values come from the formulas, not from the animation.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Sections 2.4 to 2.6).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
