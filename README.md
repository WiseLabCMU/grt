# GRT: Towards Foundational Models for Single-Chip Radar

Implementation of the *Generalizable Radar Transformer (GRT)* and the experiments shown in *Towards Foundational Models for Single-Chip Radar*.


> [!IMPORTANT]
> This repository is **research code**, and may contain bugs, outdated links, dependency incompatibilities, and other issues. Use at your own risk!
> 
> Future research should instead build on the [Neural Radar Development Kit](https://radarml.github.io/nrdk/) and [RadarML ecosystem](https://radarml.github.io/), which are being actively developed, maintained, and supported.

## Setup

1. Install dependencies:

    ```sh
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
    pip install -r requirements.txt
    pip install "roverd[video,ouster]@git+ssh://git@github.com/WiseLabCMU/red-rover.git#subdirectory=format"
    ```

2. Get data:

    See [red-rover](https://github.com/WiseLabCMU/red-rover/tree/main/processing) for full instructions.

    For each target dataset:
    ```sh
    export SRC=path/to/dataset      # e.g. `radarhd/data` on a network server
    export DST=path/to/destination  # e.g. `data/data` on a local drive

    roverp export -p $SRC -o $DST --metadata
    roverp align -p $DST --mode left
    ```

## Usage

1. Create model in `models`. See existing examples in `models/`.

2. Create config. See examples in `config`.

3. Train:

    ```sh
    python train.py -c your/config/file.yaml -n model/name
    ```

4. Observe with tensorboard:

    ```sh
    tensorboard --logdir=path/to/results --host=0.0.0.0
    ```
