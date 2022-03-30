# BundleFusion

![BundleFusion](img/teaser.jpg)

You are free to use this code with proper attribution in non-commercial applications (Please see [License.txt](License.txt)).

More information about this project can be found in our [paper](https://arxiv.org/pdf/1604.01093.pdf) and [project website](http://graphics.stanford.edu/projects/bundlefusion/).

## Installation

The code was updated to compile with Visual Studio 2019 or higher. Start by cloning the repository, including the submodules:

```
git clone https://github.com/crud89/BundleFusion.git . --recurse-submodules
```

Make sure you have the following dependencies installed on your system:

- [DirectX SDK June 2010](https://www.microsoft.com/en-us/download/details.aspx?id=6812)
- [NVIDIA CUDA 11.5](https://developer.nvidia.com/cuda-toolkit-archive)
- **Optional**: Kinect SDK (2.0 and above) 
- **Optional**: Prime sense SDK

Download the [mLib external libraries](http://kaldir.vc.in.tum.de/mLib/mLibExternal.zip) and extract them into the `external` directory, next to the `mLib` submodule, such as:

```
external/
|-- mLib
|-- mLibExternal
FriedLiver/
img/
...
```

### Troubleshooting

The following issues need to be addressed individually.

#### Unable to install DirectX SDK June 2010 (Error S1023)

This is caused by the Visual Studio 2010 runtime already installed on your system (it is likely too recent). Uninstall both of them (i.e. x86 and x64 versions), then re-install the DirectX SDK. After this, you can run a Windows Update or manually update the SDK, though it might just work fine if you continue using the version provided by the DirectX SDK.

#### Unable to compile against Eigen3 library shipped with mLibExternal (Compiler error C2280 or similar).

Downgrade Eigen3 to version 3.2.10. Simply download the sources from [here](https://gitlab.com/libeigen/eigen/-/releases/3.2.10) and replace the `Eigen` directory with the one existing in `external/mLibExternal/`. Make sure to remove or rename the existing one beforehand!

#### Up/Downgrading CUDA version

Unfortunately, I haven't found how to do this from the Visual Studio GUI, but this should not be that hard from a text editor. First, open the `FriedLiver.vcxproj` file. You can also easily do this by unloading it from the project explorer in Visual Studio and editing it there. Find the import groups called `ExtensionSettings` and `ExtensionTargets`. Adjust the linked `.props` and `.targets` files according to your installed version of CUDA. Reload the project and try to compile it. Note that due to some features beeing removed from CUDA in future releases, supporting them might not be possible without refactoring the codebase itself.

## Citation:

All credit goes to the original authors, so cite them, if you are using this project!

```
@article{dai2017bundlefusion,
  title={BundleFusion: Real-time Globally Consistent 3D Reconstruction using On-the-fly Surface Re-integration},
  author={Dai, Angela and Nie{\ss}ner, Matthias and Zoll{\"o}fer, Michael and Izadi, Shahram and Theobalt, Christian},
  journal={ACM Transactions on Graphics 2017 (TOG)},
  year={2017}
}
```

## Contact:

If you have any questions, please email Angela Dai at adai@cs.stanford.edu.

We are also looking for active participation in this open source effort making large-scale 3D scanning publically accessible. Please contact us :)
