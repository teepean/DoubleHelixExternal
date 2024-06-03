# Description
[PyPi Page](https://pypi.org/project/WGSE-NG-3rd-party/)

This repository build a wheel that is used to distribute 3rd party executable dependencies used by WGSE-NG on Windows.

The executables are built under msys2, packaged in a wheel and distribuited on PyPI by a couple of GitHub action.
Once installed, this package will be available with `import wgse.third_party` but it doesn't offer any feature as there isn't any python code inside. The package is used to discover the executables through its location on disk.

## Make a new release
```batch
git clone https://github.com/WGSE-NG/External
cd External
rem Remember to bump the version inside setup.py
python -m build
rmdir /s /q WGSE_NG_3rd_party.egg-info & rmdir /s /q dist & python -m build
rem Upload (for testing)
python3 -m twine upload --repository testpypi dist/*
rem Upload (prod)
python3 -m twine upload --repository pypi dist/*
```

## Install (prod)
```batch
python -m pip install WGSE-NG-3rd-party
```

## Example usage
```python
from wgse import third_party
from pathlib import Path
from subprocess import Popen
folder = Path(third_party.__file__).parent
# Launch something, e.g., bcftools
Popen(folder.joinpath("bcftools.exe"))
```

## Latest release Content

Tools | Version
------|--------
minimap2 | 2.28
htslib suite (tabix, bcftools, htsfile, samtools, bgzip) | v1.20
bwa |0.7.18
