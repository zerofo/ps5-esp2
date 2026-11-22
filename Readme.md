# Ps5-AIO ESP 一键烧录与插件管家 V2

这是一个专为 PS5 玩家打造的 ESP 系列芯片（ESP32）网页端一键烧录工具与配套固件系统。无需配置复杂的本地环境，通过浏览器即可完成设备识别、固件匹配、全片擦除与一键烧录。

## 🌐 网页端在线烧录

## [链接: ps5-esp2.pages.dev](https://ps5-esp2.pages.dev)
## [链接: zerofo.github.io/ps5-esp2](https://zerofo.github.io/ps5-esp2)

访问部署好的静态网页（支持桌面端 Chrome / Edge / Opera）。

### ✨ 核心特性
- **全自动识别**：自动读取芯片型号（C3 / C5 / C6 / S2 / S3 / S31 等）与 Flash 大小。
- **智能降档**：若设备 Flash 较大（如 32MB / 16MB），但无对应精确档位固件，会自动降档匹配（如 `32MB → 16MB → 8MB → 4MB`），确保设备能正常开机使用，不会因为找不到大容量固件而报错。
- **全片擦除**：烧录前默认执行全片擦除（Erase All），避免旧分区表残留导致的启动失败。
- **多接口自动兼容**：桌面端原生 Web Serial 直连；
- 
### 🎯 支持的设备与 Flash 容量
| 芯片型号 | 支持 Flash 容量 |
| :--- | :--- |
| **ESP32-C3** | 4MB |
| **ESP32-C5** | 8MB |
| **ESP32-C6** | 4MB / 8MB |
| **ESP32-OLD** (含 PICO) | 4MB |
| **ESP32-S2** | 4MB |
| **ESP32-S3** | 4MB / 8MB / 16MB |
| **ESP32-S31** | 8MB / 16MB |


---

## 🎮 ESP 端 Y2JB 菜单功能

烧录固件后，ESP 开发板将作为 PS5 破解与插件管理核心。通过连接 PS5 浏览器（或用户指南），即可访问专属菜单。

### 🛠️ 核心破解固件
固件内已按 PS5 系统版本内置对应破解方案：
- **PS5 4.0 - 13.6 版本**：使用 [`wobkot`(含`relapse`)](https://github.com/ufm42/wobkot) + `pldmgr` 方案。

### 📦 一键安装功能 (ESP -> Y2JB 菜单)

#### 1. 一键安装 YouTube 插件
- **使用方式**：将对应版本的 YouTube PKG 文件放入 U 盘（无需特定改名）。
- **特性**：系统自动扫描 U 盘，并**核对 MD5 校验值**，防止下载或拷贝过程中文件损坏，确保安装包纯净安全。

#### 2. 一键离线激活 + 假登录插件
- PS5 应用离线激活状态 + 假登录， 能够打开YouTube应用。

#### 3. 一键配置 download0.dat 与升级屏蔽
- **使用方式**：将 `download0.dat` 放入 U 盘，通过菜单触发。
- **特性**：
  - 自动扫描 PS5 内的 YouTube 应用（支持同时处理多个区的 YouTube, 一键将 download0.dat  拷贝至 多个YouTube应用对应download 内。
  - 一键应用升级屏蔽插件，阻止应用后台强制更新。

### 🧩 其他通用插件
固件内置了大量实用通用插件。根据设备不同的 Flash Size（4MB / 8MB / 16MB），会提供不同的插件支持。

---

### 目录结构
```text
/ (根目录)
├── index.html
├── /firmware/
│   ├── esp32-c3-4mb.bin       # 合并后的完整固件，从 0x0 开始
│   ├── esp32-s3-8mb.bin
│   ├── esp32-s3-16mb.bin
│   └── ...
├── /firmware/chips.js         # 动态渲染支持列表的脚本
└── /firmware/build-info.js    # 版本信息脚本
```
