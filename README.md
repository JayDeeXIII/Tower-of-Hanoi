# Tower of Hanoi

An interactive Tower of Hanoi game with an optimal auto-solver, in a single Jupyter notebook.

- **Play:** click a tower to pick up its top disk, then click the tower to drop it on. Illegal moves are rejected.
- **Solve:** one button resets the puzzle and animates the optimal solution (2^n - 1 moves).
- **Verified:** the solver is checked by replaying its moves through the game's rule-enforcing simulator, and cross-checked against a second, independent algorithm.

## Setup

Requires Python 3.9+. The notebook runs in VS Code (with the Python and Jupyter extensions) or JupyterLab.

```bash
git clone https://github.com/JayDeeXIII/Tower-of-Hanoi.git
cd Tower-of-Hanoi
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Open `tower_of_hanoi.ipynb`, select the `.venv` kernel, and **Run All**. The game appears at the bottom.

For JupyterLab instead of VS Code: `pip install jupyterlab`, then `jupyter lab`.

> The notebook preview on GitHub is static. The buttons only work when the notebook is run locally.

## How it works

| Section | What it does |
|---|---|
| Simulator | `Hanoi` class: state, move validation, history, drawing. No UI or solver logic. |
| Solver | Recursive generator that yields the optimal move sequence. An iterative version exists only as a cross-check. |
| Verification | Replays both solvers for n = 1..12; asserts the puzzle ends solved in exactly 2^n - 1 moves and that both solvers agree. |
| Game UI | `HanoiApp`: `ipywidgets` buttons over the simulator, with a disk-count dropdown (1-7). |

The minimum for n disks is 2^n - 1 moves, so the disk count is capped at 7 (127 moves) to keep the Solve animation watchable.

## Project structure

```
Tower-of-Hanoi/
├── tower_of_hanoi.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```

## Troubleshooting

- `ModuleNotFoundError`: the notebook kernel isn't the venv you installed into. Reselect the `.venv` kernel and restart it.
- Buttons don't render: confirm `ipywidgets` is installed in that same environment, then restart the kernel.
