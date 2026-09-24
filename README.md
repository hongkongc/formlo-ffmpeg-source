# Formlo for Windows — FFmpeg corresponding source

Formlo for Windows ships an **unmodified** LGPL build of FFmpeg (`ffmpeg.exe`, `ffprobe.exe` and the
`avcodec` / `avformat` / `avutil` / `avfilter` / `avdevice` / `swresample` / `swscale` DLLs) in the `ffmpeg`
folder of its installation directory. This repository provides the complete corresponding source of those
files, as required by the GNU LGPL 3.0 / GPL 3.0 section 6.

The source archives are attached to the [releases](../../releases), one release per FFmpeg build shipped.

| Release | FFmpeg | Binary build | Shipped since |
|---|---|---|---|
| `ffmpeg-n9.0.2-3-ga5923073bf` | n9.0.2-3-ga5923073bf (release/9.0, commit `a5923073bfd8f25b7300d93af3f8e690174ebd30`) | [BtbN/FFmpeg-Builds `autobuild-2026-09-20-13-11`](https://github.com/BtbN/FFmpeg-Builds/releases/tag/autobuild-2026-09-20-13-11), `ffmpeg-n9.0.2-3-ga5923073bf-win64-lgpl-shared-9.0.zip` (sha256 `b532987f6e2ad6d114c1c21434ace634491fbeea358ca34b51f2a34b9f468f2c`) | Formlo for Windows 0.20.0 |

Each archive contains:

- `ffmpeg/` — FFmpeg at the exact commit;
- `FFmpeg-Builds/` — the build scripts at the commit used for that build (`./build.sh win64 lgpl-shared 9.0`);
  they pin every statically linked dependency by repository and commit in `scripts.d/`;
- `deps/<name>/` — every one of those dependencies at the pinned revision, fetched the same way the build
  scripts do (git submodules, extra repositories, `cargo vendor` for the Rust crates of rav1e / librsvg,
  LAME svn r6761, opus model data, meson subprojects);
- `COMPONENTS.tsv` and `FFMPEG-THIRD-PARTY-LICENSES.txt` — component list and all license texts
  (the same files are installed with Formlo in its `licenses` folder).

FFmpeg in this configuration is licensed under the GNU LGPL version 3 or later (`--enable-version3`,
no `--enable-gpl` / `--enable-nonfree`). Formlo does not own FFmpeg. The archive was produced by
`installer/ffmpeg-compliance/collect.py` in the Formlo for Windows source tree.

---

Formlo Windows 版在安装目录的 `ffmpeg` 文件夹里随附**未经修改**的 LGPL 版 FFmpeg。按 LGPL 3.0 / GPL 3.0 第 6 条，
这里提供与之完全对应的全部源码（见 Releases，每个随包的 FFmpeg 构建一个 Release）：FFmpeg 本体、构建脚本，以及构建时
静态链接进 DLL 的每个库在同一版本的源码，另附组件清单和全部许可证原文。
