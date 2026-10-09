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

On a control-room computer, install the applications with the deployment script of your machine: [CLEAR](https://gitlab.cern.ch/flight-simulator/machine-interfaces/-/blob/master/backends/clear/clear_deploy.md), [ATF2](https://gitlab.cern.ch/flight-simulator/machine-interfaces/-/blob/master/backends/atf2/atf2_deploy.md), [ESRF](https://gitlab.cern.ch/flight-simulator/machine-interfaces/-/blob/master/backends/esrf/esrf_deploy.md) or [FACET2](https://gitlab.cern.ch/flight-simulator/machine-interfaces/-/blob/master/backends/facet2/facet2_deploy.md). It creates a shared virtual environment and one launcher per GUI, e.g. `./BumpsApplication_GUI.sh`.

For a local installation, use Python 3.11 or newer and keep the repositories in one directory:

```bash
git clone https://gitlab.cern.ch/flight-simulator/machine-interfaces.git
git clone https://gitlab.cern.ch/flight-simulator/response-matrix.git
git clone https://gitlab.cern.ch/flight-simulator/orbit-bump.git
python3 -m venv venv
source venv/bin/activate
pip install -e machine-interfaces -e machine-interfaces/backends/esrf -e response-matrix -e orbit-bump
cd orbit-bump
python BumpsApplication_GUI.py
```

Replace `esrf` with `atf2` or `facet2` for another machine. The CLEAR control-system packages are available only from the CERN Acc-Py index; elsewhere, install only the CLEAR simulation:

```bash
pip install rf-track cpymad
pip install --no-deps -e machine-interfaces/backends/clear
```

Editable installs pick up `git pull` changes without reinstalling.
