# 2022.01.12: GLUtils 更改 API 规范

> Updated: 2022.01.12
>
> Author: squid233

GLUtils 即将大规模更改 API 规范。具体内容如下。

---

`Stitcher`:  
旧规范:  
  - `stitchStb(Class/ClassLoader, TexParam, String[])`
  - `stitchAwt`
  - `stitchFsStb(TexParam, String[])`
  - `stitchFsAwt`

新规范:  
  - `stitch(Object, TexParam, boolean=true, String[])`
  - `stitchFs(TexParam, boolean=true, String[])`

---

`Texture2D`: 移除

---

`Textures`:  
旧规范:
  - `bind2D(int)`
  - `unbind2D()`
  - `active(int)`
  - `loadAWT(Class/ClassLoader, String, TexParam)`
  - `loadFS(String, TexParam)`
  - `load(String, ByteBuffer, TexParam)`
  - `load(String, int, int, int[], TexParam)`
  - `texParameter2D(TexParam)`
  - `pushToGL2D(TexParam, int, int, ByteBuffer)`
  - `gen()`
  - `hasGenMipmap()`
  - `genMipmapCubeMap()`
  - `genMipmap3D()`
  - `genMipmap2D()`
  - `genMipmap(int)`
  - `pushToGL2D(TexParam, int, int, int[])`
  - `getMaxSize()`
  - `free()`

新规范:  
  - `active(int)`
  - `load(Object, String, TexParam, boolean)`
  - `loadFs(String, TexParam, boolean)`
  - `hasGenMipmap()`
  - `genMipmap(int)`
  - `getMaxSize()`
