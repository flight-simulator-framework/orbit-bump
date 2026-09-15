# Orbit Bump

Create a desired beam trajectory by changing selected corrector settings. The application combines a measured response matrix with live BPM readings to calculate the corrector changes needed to approach target beam positions.

The GUI displays the desired, predicted and measured trajectories so that the result can be compared with the requested bump.

## Usage

1. Select a machine or simulation interface and choose the correctors and BPMs to use.
2. Load the directory containing the measured response matrix.
3. Record a reference orbit, then edit the desired horizontal and vertical positions on the target-orbit plot.
4. Set the BPM sample count, maximum corrector strengths and matrix inversion settings.
5. Compute the bump and see the proposed corrector settings and predicted trajectory.
6. Apply the correction and compare the live orbit with the target. Use the iterative bump controls when further adjustment is needed.

The reference controls let you restore the saved corrector settings. The application records bump-session data for later inspection.

## Application

`BumpsApplication_GUI.py` contains the orbit-bump GUI. It uses the response-matrix code to reconstruct the measured response, including coupling between the horizontal and vertical planes.

## Installation and startup

Use Python 3.11 or newer and Poetry 2 or newer; the local setup was tested with Python 3.13. Keep this repository and `machine-interfaces`, `response-matrix` in the same parent directory. From this repository, run:

```bash
poetry install
poetry run python BumpsApplication_GUI.py
```