[![pypi](https://badge.fury.io/py/moderngl-window.svg)](https://pypi.python.org/pypi/moderngl-window) [![rtd](https://readthedocs.org/projects/moderngl-window/badge/?version=latest)](https://moderngl-window.readthedocs.io)

# moderngl_window

A cross platform helper library for [ModernGL](https://github.com/moderngl/moderngl) making window creation and resource loading simple.

* [moderngl_window Documentation](https://moderngl-window.readthedocs.io)
* [moderngl_window on PyPI](https://pypi.org/project/moderngl-window)
* [moderngl_window on Github](https://github.com/moderngl/moderngl_window)
* [ModernGL](https://github.com/moderngl/moderngl)
* [ModernGL Discord Server](https://discord.gg/UEMtW8D)

Please report bugs or post questions/feedback on [github](https://github.com/moderngl/moderngl_window/issues).

## Features

* Cross platform support. Tested on Windows 10, Linux and Mac OS X.
  This can save users a lot of time and is often more difficult than most people
  imagine it to be.
* Easily create a window for ModernGL using Pyglet, PySide2, GLFW, SDL2, PyQt5
  or tkinter supporing window, keyboard and mouse controls. These events are unified
  into a single system so your project can work with any window.
* Load 2D textures and texture arrays
* Load shaders as single or multiple `glsl` files
* Load objects/scenes from wavefront/obj, GLTF 2.0 or STL
* Resource finder system supporting multiple resource directories
* A highly pluggable library supporting custom loaders,
  resource finders and windows.
* Type hints everywhere making code completion and linting a breeze

We are not trying to force the user into using every aspect of this
library. If you have an exiting project and just need texture loading
you will be able to do this without unnecessary hurdles as long as
you provide us your `moderngl.Context`.

## Install

```bash
pip install moderngl-window
```

## Supported Platforms

* [x] Windows
* [x] Linux
* [x] Mac OS X

## Sample Usage

Simple example opening a window clearing every frame using red (color).

```py
# test.py
import moderngl_window as mglw

class Test(mglw.WindowConfig):
    gl_version = (3, 3)

    def render(self, time, frametime):
        self.ctx.clear(1.0, 0.0, 0.0, 0.0)

mglw.run_window_config(Test)
```

Run the example with different window backends:

```bash
python test.py --window pyglet
python test.py --window glfw
python test.py --window sdl2
python test.py --window pyside2
python test.py --window pyqt5
python test.py --window tk
```


`WindowConfig` classes are the simplest way to get started without knowing
a lot about this library. For more advanced usage see documenation
or examples.

## Setup from source

We assume the user knows how to handle vitrualenvs.

```bash
# Install the package in editable mode
$ pip install -e .

# Set up and dev requirements
pip install -r requirements.txt
pip install -r tests/requirements.txt
```

## Running Tests

Tests are set up with `tox` running pytest with coverage and flake8.

```bash
pip install -r tests/requirements.txt
tox -e py35
tox -e py36
tox -e py37
tox -e py38
tox -e pep8
```

## Building Docs

```bash
pip install -r docs/requirements.txt
python setup.py build_sphinx
```

## Contributing

Contributions are welcome regardless of experience level.
Don't hesitate submitting issues, opening partial or completed
pull requests.

### Plugins

We are interested in contributions providing new loaders, windows etc.
For these to be included in this library we require them
to work cross platforms (win10/linux/osx) and be fairly easy to set up.

If it requires more than manually downloading a precompiled dll
(like SDL2, GLEW etc.) it would most likely not be included,
but you are welcome to present your case if you still think it should
be included.

If you create your own repo/package containing plugins for
this library, please make an issue and we'll link back to it.
Be sure to include what platforms are suppored, install
instructions, how you configure it in `moderngl_window` and
of course a clear and concise description of what exactly
your package provides. 

## Attributions

We can't build everything from scratch. We rely on certain packages
and resources to make this project possible.

### Windows

* Pyglet (https://github.com/pyglet/pyglet)
* pyGLFW (https://github.com/FlorianRhiem/pyGLFW)
* PySDL2 (https://github.com/marcusva/py-sdl2)
* PySide2 (https://wiki.qt.io/Qt_for_Python)
* PyQt5 (https://www.riverbankcomputing.com/software/pyqt/intro)
* tkinter (https://github.com/jonwright/pyopengltk)

### Loaders

* Pillow (https://python-pillow.org/)
* pywavefront (https://github.com/pywavefront/PyWavefront)
* trimesh (https://github.com/mikedh/trimesh)

### Testing & Utility

* Pyrr (https://github.com/adamlwgriffiths/Pyrr)
* numpy (https://github.com/numpy/numpy)
* pytest (https://docs.pytest.org/en/latest/)
* flake8 (https://gitlab.com/pycqa/flake8)
* coverage (https://github.com/nedbat/coveragepy)
* tox (https://tox.readthedocs.io/en/latest/)

## Resources

* NASA 3D Resources (https://github.com/nasa/NASA-3D-Resources)
* glTF Sample Models (https://github.com/KhronosGroup/glTF-Sample-Models)

## Some History

The majority of the code in this library comes from [demosys-py](https://github.com/Contraz/demosys-py) (somewhat modified).
Because `demosys-py` is a framework we decided to split out a lot useful functionality into this
library. Frameworks are a lot less appealing to users and it would be a shame to not make this
more available to the ModernGL user base.
