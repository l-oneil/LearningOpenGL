# LearningOpenGL on M1 Mac
This is just a collection of useful information and experiences with Learning OpenGL from: https://learnopengl.com/

## How to install GLFW 
```bash
    $ git clone git@github.com:glfw/glfw.git
    $ cd glfw 
    $ mkdir build && cd build 
    $ cmake -GNinja -DCMAKE_OSX_ARCHITECTURES=arm64
    $ ninja 
    $ ninja install
```

## Generating GLAD Library 
1. Go to: https://glad.dav1d.de/
2. Select: C++, OpenGL, gl v3.3, tick "Generate Loader"
3. Click generate
4. Download glad.zip