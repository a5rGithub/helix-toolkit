<img src='https://avatars3.githubusercontent.com/u/8432523?s=200&v=4' width='64' />

# Helix Toolkit

**Helix Toolkit is a collection of 3D components for .NET Framework.**

[**HelixToolkit.WPF:**](https://github.com/helix-toolkit/helix-toolkit/tree/develop/Source/HelixToolkit.Wpf) 
Adds variety of functionalities/models on the top of internal WPF 3D model (Media3D namespace). 

[**HelixToolkit.SharpDX.WPF:**](https://github.com/helix-toolkit/helix-toolkit/tree/develop/Source/HelixToolkit.Wpf.SharpDX) 
3D Components and XAML/MVVM compatible Scene Graphs based on [SharpDX](https://github.com/sharpdx/SharpDX)(DirectX 11) for high performance usage.

[**HelixToolkit.UWP:**](https://github.com/helix-toolkit/helix-toolkit/tree/develop/Source/HelixToolkit.UWP) 
3D Components and XAML/MVVM compatible Scene Graphs based on [SharpDX](https://github.com/sharpdx/SharpDX)(DirectX 11) for Universal Windows App.

[**Examples:**](https://github.com/helix-toolkit/helix-toolkit/tree/develop/Source/Examples)
Please download full source code to run examples.

[![Build status](https://ci.appveyor.com/api/projects/status/tmqafdk9p7o98gw7?svg=true)](https://ci.appveyor.com/project/objorke/helix-toolkit)

Description         | Value
--------------------|-----------------------
License             | The MIT License (MIT)
Web page            | http://helix-toolkit.org/
Documentation       | http://docs.helix-toolkit.org/
Forum               | http://forum.helix-toolkit.org/
Chat                | https://gitter.im/helix-toolkit/helix-toolkit
Source repository   | http://github.com/helix-toolkit/helix-toolkit
Latest build        | http://ci.appveyor.com/project/objorke/helix-toolkit
Issue tracker       | http://github.com/helix-toolkit/helix-toolkit/issues
NuGet packages      | http://www.nuget.org/packages?q=HelixToolkit
MyGet feed          | https://www.myget.org/F/helix-toolkit
StackOverflow       | http://stackoverflow.com/questions/tagged/helix-3d-toolkit
Twitter             | https://twitter.com/hashtag/Helix3DToolkit

## Project Build

**Visual Studio 2017. Windows 10 SDK (Min Ver.10.0.10586.0).**

Windows 10 SDK **Ver.10.0.10586.0** can be selected and installed using Visual Studio 2017 installer.If you installed the higher version only, please change the target version in **HelixToolkit.Native.ShaderBuilder** property to the proper version installed on your machine.

## Notes

#### 1. Right-handed Cartesian coordinate system by default
HelixToolkit default is using right-handed Cartesian coordinate system, including Meshbuilder etc. To use left-handed Cartesian coordinate system (Camera.CreateLeftHandedSystem = true), user must manually correct the triangle winding order or IsFrontCounterClockwise in raster state description if using SharpDX.

#### 2. Performance [Topics](https://github.com/helix-toolkit/helix-toolkit/wiki/Tips-on-performance-optimization-(WPF.SharpDX-and-UWP)) for WPF.SharpDX and UWP.

#### 3. Following features are not supported currently on FeatureLevel 10 graphics card:
FXAA, Order Independant Transparent Rendering, Particle system, Tessellation.

## News

#### 2018-05-04
[V2.1.0](https://github.com/helix-toolkit/helix-toolkit/tree/release/2.1.0) releases are available on nuget. [Release Note](https://github.com/helix-toolkit/helix-toolkit/blob/master/CHANGELOG.md)
- [WPF](https://www.nuget.org/packages/HelixToolkit.Wpf/2.1.0)
- [WPF.SharpDX](https://www.nuget.org/packages/HelixToolkit.Wpf.SharpDX/2.1.0)
- [UWP](https://www.nuget.org/packages/HelixToolkit.UWP/2.1.0)

##### Note: 2.0 Breaking changes from version 1.x.x. (HelixToolkit.SharpDX only)
1. New architecture for backend rendering and shader management. No more dependency from obsoleted Effects framework. EffectsManager is mandatory to be provided from ViewModel for resource live cycle management by user to avoid memory leak.
2. Many performance improvements. Viewports binding with same EffectsManager will share common resources. Models binding with same geometry3D will share same geometry buffers. Materials binding with same texture will share same resources.
3. Support basic direct2d rendering and layouts arrangement. (Still needs a lot of implementations)
4. No more HelixToolkit.WPF project dependency.
5. Unify dependency property types. All WPF.SharpDx model's dependency properties are using class under System.Windows.Media. Such as Vector3D and Color. More Xaml friendly.
6. Post effect support.(Note: Post effect elements does not recommend to be used in ModelContainer3DX for model sharing between viewports)
7. Supports transparent meshes rendered after opaque meshes. IsTransparent property is added in MaterialGeometryModel3D.
8. Rendering order by RenderType flag: 
    ##### Pre(such as shadow map)->Opaque->Particle->Transparent->Post(post effects)->ScreenSpaced(ViewBox/CoordinateSystem).
9. Core implementation are separated from platform dependent controls(Element3D) into its own Scene Node classes. Scene Node serves as complete Scene Graph for traversal inside render host. Element3D will only be used as a wrapper to manipulate scene node properties from XAML.
10. Supports [Order independent transparent(OIT)](https://developer.nvidia.com/content/transparency-or-translucency-rendering) rendering.
11. Supports [FXAA](https://docs.nvidia.com/gameworks/content/gameworkslibrary/graphicssamples/d3d_samples/fxaa311sample.htm). Prefer FXAA over MSAA if using OIT or post effects. Note: FXAA does not support transparent background for now.
12. High performance static octree for Mesh/Point/Line/Instancing Models hit test.

#### 2018-02-06

[V1.1.0](https://github.com/helix-toolkit/helix-toolkit/tree/release/1.1.0) releases are available.
- [WPF](https://www.nuget.org/packages/HelixToolkit.Wpf/1.1.0)
- [WPF.SharpDX](https://www.nuget.org/packages/HelixToolkit.Wpf.SharpDX/1.1.0)
