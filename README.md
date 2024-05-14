# Description
[PyPi Page](https://pypi.org/project/WGSE-NG-3rd-party/)

This repository is just a placeholder that build a wheel that is used to distribute 3rd party executables that are used by WGSE-NG on Windows.

The executables are contained in a zip folder distribuited as a release archive (to not check-in the binaries). The setup.py here is just to download that file a build a wheel containing the executables.
Once installed, this package will be available with `import wgse.third_party` but it doesn't offer any feature. The package is used by by discover the executables through its location on disk.

## Make a new release
```batch
git clone https://github.com/WGSE-NG/External
cd External
rem Remember to bump the version inside setup.py
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
