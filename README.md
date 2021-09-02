# LearningOpenGL on M1 Mac
This is just a collection of useful information and experiences with Learning OpenGL from: https://learnopengl.com/

## Third Party Software
### How to install GLFW 
```bash
    $ git clone git@github.com:glfw/glfw.git
    $ cd glfw 
    $ mkdir build && cd build 
    $ cmake -GNinja -DCMAKE_OSX_ARCHITECTURES=arm64
    $ ninja 
    $ ninja install
```

### Generating GLAD Library 
1. Go to: https://glad.dav1d.de/
2. Select: C++, OpenGL, gl v3.3, tick "Generate Loader"
3. Click generate
4. Download glad.zip

### How to install GLM (OpenGL Mathematics)
```bash
    $ git clone git@github.com:g-truc/glm.git
```

Header only, so no compilation required, just need to include through CMake:
```CMake
    set(glm_DIR <path to glm root>/cmake/glm) # if necessary
    find_package(glm REQUIRED)
    target_link_libraries(<your executable> glm::glm)
```

### STB Image
```bash
    $ wget https://raw.githubusercontent.com/nothings/stb/master/stb_image.h
```

### ImGui
Location: https://github.com/ocornut/imgui

### ASSIMP
```bash
    $ cd thirdparty/assimp
    $ mkdir build && cd build 
    $ cmake ..
    $ ninja
```