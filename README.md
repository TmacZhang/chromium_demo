# Demo

[中文 README](./README_zh.md)

---

> This project is migrating to chromium version `91.0.4472`,not done yet,if you want to build all demos,please checkout this project to `c/80.0.3987`, and checkout chromium to `80.0.3987.165`,then run `gclient sync`. If you are interested in this, please feel free to contact me in the Discussions channel.  
> I have built a WeChat group, used to facilitate technical discussions, if you are interested, welcome to add my WeChat, I will pull you into the discussion group. WeChat:  
> <img src="https://user-images.githubusercontent.com/1212025/126026381-b153090c-f53f-4aa8-8204-d830d8fe0a6d.jpeg" width="200">

This project is used to demonstrate how to use some basic mechanisms in chromium, including asynchronous multitasking, mojo, multi-process, etc.

> Tips:   
> 1. If you are new to chromium, it is recommended to study these demos in order.  
> 2. These demos are ONLY tested on Linux and Android.
> 3. Welcome PR/MR.

Demo list:

1. [v91] `demo_exe`: The simplest demo to demonstrate gn and create your own exe;
2. [v91] `demo_log`: Demo log library;
3. [v91] `demo_tracing_console`: Demonstrate using Trace to output to the console;
4. [v91] `demo_task_thread_pool`: Demonstrate the use of thread pool ThreadPool;
5. [v91] `demo_task_executor`: Demonstrate using the message loop SingleThreadTaskExecutor;
6. [v91] `demo_mojo_single_process`: Demonstrate the use of the `mojo` library in a single process;
7. [v91] `demo_mojo_multiple_process`: Demonstrate the use of the `mojo` library in multiple processes;
8. [v91] `demo_mojo_multiple_process_binding`: Demonstrate using the binding layer of the `mojo` library in multiple processes;
9. `demo_services`: Demonstrate the use of servcies and multi-process architecture based on `mojo`;
10. `demo_ipc`: Demonstrate the use of IPC interface based on `mojo`;
11. [v91] `demo_memory`: Demonstrate the use of SharedMemory;
12. [v91] `demo_tracing_perfetto`: Demonstrate the output of Trace as Json format (used to interface with perfetto);
13. [v91] `demo_tracing_perfetto_content`: Demonstrate how the content module is connected to perfetto;
14. [v91] `demo_resources`: Demo resources related content, including grit, l10n, pak, etc.;
15. `demo_gl`: Demonstrate using `//ui/gl` for GPU rendering;
16. `demo_viz_gui`: Demonstrate using `viz` to display the GUI interface;
17. `demo_viz_offscreen`: Demonstrate using `viz` for off-screen rendering;
18. `demo_viz_gui_gpu`: Demonstrate the use of `viz` for hardware accelerated rendering;
19. `demo_viz_layer`: Demonstrate the use of `viz` for interactive rendering;
20. `demo_viz_layer_offscreen`, demonstrate using VIZ's `CopyOutput` interface for off-screen rendering;
21. `demo_cc_gui`: Demonstrate using `cc` to display GUI interface;
22. `demo_cc_offscreen`: Demonstrate using `cc` for off-screen rendering;
23. `demo_views`: Demonstrate the use of `//ui/views` to create UI;
24. `demo_apk`: Demonstrate the creation of Android applications, the use of base::android::* and JNI;
25. `demo_android_skia`: Demonstrate the use of Skia for software rendering and hardware rendering on Android;
26. `demo_skia`: Demonstrate the use of Skia for software rendering and hardware rendering on Linux;
27. `demo_x11`: Demonstrate using X11 to create transparent windows;
28. `demo_x11_glx`: Demonstrate the use of glx in a transparent window;
29. `demo_x11_egl`: Demonstrate the use of egl in a transparent window;
30. `demo_shell`: Demonstrate the use of content api to create a streamlined browser that supports Linux and Android;

Documents:

Public documents are in the [docs](./docs) directory, and other documents are in the corresponding directory of the code.

## Usage

1. Go to the `src` directory of chromium and switch to a supported branch, such as `80.0.3987.165` for version 80 or `91.0.4472.144` for version 91 (the last version number does not matter). And run `gclient sync` to synchronize the code.
2. Run the following command to clone this repository to the `src/demo` directory and switch to the corresponding branch, e.g. `c/80.0.3987` for version 80 or `c/91.0.4472` for version 91.

    ```sh
    git clone <address of current repository> demo
    git checkout <the branch>
    ```

3. Find the `out/Default/args.gn` file in your compilation output directory and add the following parameters:

    ```python
    # add extra deps to gn root
    root_extra_deps = ["//demo"]
    
    # If you want to compile the demo of android platform, you need to add the following parameters
    target_os="android"
    target_cpu="arm64" # Other architectures can be selected as needed x86, x64, arm, mipsel
    ```

4. Run `ninja -C out/Default <name in demo list>` to generate the required demo (see [BUILD.gn](. /BUILD.gn)), for example using the name `demo_exe` to generate the demo_exe program. Or use `demo` to generate all programs.

> REPEAT: These demos are ONLY tested on Linux and Android.

## TODO

- Improve the documentation of the process initialization part ([docs/startup.md](docs/startup.md));
- Improve the documentation of the UI part ([docs/ui.md](docs/ui.md));
- Improve the documentation of the content module ([docs/content.md](docs/content.md));
- Improve the documentation of demo_shell ([demo_shell/README.md](demo_shell/README.md));
- Add demo to demonstrate how to create aar component;
- Add demo to demonstrate how to use aura to create UI interface;
- Add demo to demonstrate how to use PlatformWindow to create UI interface;
- Add demo to demonstrate how to implement off-screen rendering of web pages;
- Add a demo to demonstrate how to inject new JS objects into Blink;
- Add a demo to demonstrate the principle of `navigator.mediaDevices.getUserMedia()`;
- Add a demo to demonstrate the principle of `tab capture api`;

## Changelog

### 2021.7.29

- Migrate below demos to v91：  
    - demo_resources

### 2021.7.22

- Migrate below demos to v91：  
    - demo_memory

### 2021.7.17

- Migrate below demos to v91：  
    - demo_exe
    - demo_tracing_perfetto
    - demo_tracing_perfetto_content
    - demo_messageloop
    - demo_tasks
    - demo_mojo_single_process
    - demo_mojo_multiple_process
    - demo_mojo_multiple_process_binding
-  Rename below demos：
    - demo_messageloop to demo_task_executor
    - demo_tasks to demo_task_thread_pool

### 2020.8.10

- Add demo_gl, the demo uses the `//ui/gl` module to call GL for rendering;

### 2020.7.31

- demo_viz_layer_offscreen supports off-screen rendering using the SkiaOutputDeviceOffscreen interface;

### 2020.7.28

- Add demo_viz_layer_offscreen to demonstrate using VIZ's CopyOutput interface for off-screen rendering;

### 2020.7.24

- Add demo_viz_layer, demonstrate the use of VIZ for handwriting writing, and support the use of command lines to switch between software and hardware rendering;

### 2020.7.18

- Add demo_viz_gui_gpu to demonstrate the use of VIZ for hardware accelerated rendering and VIZ Client nesting;

### 2020.7.15

- Add demo_x11_glx and demo_x11_egl;

### 2020.7.11

- Add demo_x11 to demonstrate the use of X11 to create transparent windows;
- Update demo_skia, use software rendering by default, support transparent windows, GL rendering supports GL_RGB565 pixel format;

### 2020.6.28

- Add demo_skia to demonstrate the software/hardware rendering using Skia in Linux;

### 2020.6.4

- Update demo_android_skia, add multi-thread rendering and frame rate synchronization;

### 2020.5.31

- Add demo_android_skia to demonstrate the use of Skia in Android for software/hardware rendering;

### 2020.5.21

- Add demo_tracing_perfetto_content to demonstrate how the content module saves trace to a file, which can be used for chrome://tracing;
- Add demo_tracing documentation [demo_tracing](./demo_tracing/README.md);

### 2020.5.18

- Move demo_tracing to demo_tracing folder and rename it to demo_tracing_console, add Flush function;
- Add demo_tracing_perfetto to demonstrate the integration and use of trace and perfetto;

### 2020.4.29

- Add demo_cc_gui to demonstrate using `cc` to display GUI interface;

### 2020.4.17

- Added TRACE.txt of demo_cc to help understand the runtime behavior of cc;

### 2020.4.10

- Add demo_cc_offscreen, demonstrate the use of `cc` for off-screen rendering;

### 2020.4.6

- Add demo_viz_offscreen, demonstrate using `viz` for off-screen rendering;
- Modify demo_viz to demo_viz_gui, the function is unchanged;

### 2020.3.31

- Add demo_viz, demonstrate using `viz` module;
- Add documentation for `viz`: [viz](./demo_viz/README.md)

### 2020.3.21

- Add demo_views, demonstrate using `//ui/views` to develop UI;

### 2020.3.12

- demo_apk supports JNI to call instance method of C++ class;
- Add document: [browser startup process brief description] (./docs/startup.md)

### 2020.3.7

- demo_apk supports JNI;
- Add document: [demo_apk](./demo_android/README.md)

### 2020.3.4

- Add demo_tracing to demonstrate the use of trace;
- Add demo_apk to demonstrate how to use gn to create Android applications;
- Add demo_shell to demonstrate how to use the Content API to create a streamlined browser;

### Earlier

Add the following demo and related documents:

- demo_exe: the simplest demo, demonstrate gn and create your own exe;
- demo_log: demonstrate the use of log library;
- demo_tracing: demonstrate the use of Trace;
- demo_tasks: demonstrate the use of thread pool ThreadPool;
- demo_messageloop: demonstrate the use of message loop MessageLoop;
- demo_mojo_single_process: demonstrate the use of mojo library in a single process;
- demo_mojo_multiple_process: demonstrate the use of the mojo library in multiple processes;
- demo_mojo_multiple_process_binding: demonstrate the use of the binding layer of the mojo library in multiple processes;
- demo_services: demonstrate the use of mojo-based servcies and multi-process architecture;
- demo_ipc: demonstrate the use of mojo-based IPC interface;
- demo_memory: demonstrate the use of SharedMemory;
