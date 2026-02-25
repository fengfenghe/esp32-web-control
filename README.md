# ESP32 Web控制台

一个漂亮的Web控制台，通过MQTT远程控制ESP32设备。

## ✨ 特性

- 🎨 现代化UI设计
- 📱 响应式布局（手机/平板/电脑自适应）
- ⚡ 实时GPIO控制
- 📊 系统状态监控
- 🔄 自动重连
- 🌐 完全免费部署

## 🚀 快速开始

### 方法1: 直接打开（本地测试）

1. 下载`index.html`文件
2. 双击打开（或用浏览器打开）
3. 输入设备ID
4. 点击"连接设备"

### 方法2: 部署到Cloudflare Pages（推荐）

#### 步骤1: 创建GitHub仓库

```bash
# 创建新仓库
git init
git add index.html README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/esp32-web-control.git
git push -u origin main
```

#### 步骤2: 连接Cloudflare Pages

1. 访问 https://dash.cloudflare.com
2. 进入 "Workers & Pages"
3. 点击 "Create application"
4. 选择 "Pages" → "Connect to Git"
5. 授权GitHub并选择仓库
6. 配置:
   - Framework preset: None
   - Build command: (留空)
   - Build output directory: /
7. 点击 "Save and Deploy"

#### 步骤3: 访问

部署完成后，你会得到一个网址：
```
https://esp32-web-control.pages.dev
```

## 📝 使用说明

### 1. ESP32端配置

确保ESP32已经：
- ✅ 连接到WiFi
- ✅ 启用MQTT功能
- ✅ 配置MQTT Broker为 `broker.emqx.io`

### 2. Web控制台使用

1. 打开Web控制台
2. 输入设备ID（如: `esp32_8173a0`）
3. 点击"连接设备"
4. 等待连接成功
5. 开始控制GPIO！

### 3. 功能说明

#### GPIO控制
- **开启**: 设置GPIO为高电平
- **关闭**: 设置GPIO为低电平
- **切换**: 切换GPIO状态
- **刷新**: 获取最新状态

#### 系统信息
- 查看内存使用
- 查看运行时间
- 查看MAC地址
- 重启设备

## 🎨 自定义

### 修改GPIO列表

编辑`index.html`中的`defaultGPIOs`数组：

```javascript
const defaultGPIOs = [
    { pin: 2, name: 'LED灯' },
    { pin: 13, name: '继电器1' },
    { pin: 14, name: '继电器2' },
    // 添加更多GPIO...
];
```

### 修改MQTT Broker

编辑`index.html`中的默认值：

```javascript
<input type="text" id="brokerUrl" value="你的Broker地址">
```

### 修改主题颜色

编辑CSS中的`:root`变量：

```css
:root {
    --primary-color: #667eea;  /* 主色调 */
    --success-color: #10b981;  /* 成功色 */
    --danger-color: #ef4444;   /* 危险色 */
}
```

## 📱 添加到手机桌面

### iOS (iPhone/iPad)

1. 用Safari打开Web控制台
2. 点击底部"分享"按钮
3. 选择"添加到主屏幕"
4. 设置名称和图标
5. 完成！

### Android

1. 用Chrome打开Web控制台
2. 点击右上角"..."菜单
3. 选择"添加到主屏幕"
4. 设置名称
5. 完成！

## 🔒 安全建议

### 生产环境

1. **使用TLS加密**
   ```javascript
   // 修改连接代码
   client = mqtt.connect(`wss://你的Broker:8084/mqtt`, {
       // ... 其他配置
   });
   ```

2. **添加密码认证**
   ```javascript
   client = mqtt.connect(`wss://你的Broker:8084/mqtt`, {
       username: '你的用户名',
       password: '你的密码',
       // ... 其他配置
   });
   ```

3. **限制Topic权限**
   - 只允许订阅自己设备的Topic
   - 使用ACL控制访问权限

## 🐛 故障排除

### 无法连接

1. 检查设备ID是否正确
2. 检查ESP32是否在线
3. 检查MQTT Broker地址
4. 查看浏览器控制台错误

### GPIO控制无响应

1. 检查MQTT连接状态
2. 检查ESP32是否收到命令（查看串口日志）
3. 检查GPIO配置是否正确

### 页面显示异常

1. 清除浏览器缓存
2. 尝试其他浏览器
3. 检查网络连接

## 📚 技术栈

- HTML5
- CSS3 (Flexbox, Grid, Animations)
- JavaScript (ES6+)
- MQTT.js (WebSocket)

## 🎯 浏览器支持

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ 移动浏览器

## 📄 许可证

MIT License

## 🙏 致谢

- [MQTT.js](https://github.com/mqttjs/MQTT.js) - MQTT客户端库
- [EMQX Cloud](https://www.emqx.com/zh/cloud) - 免费MQTT Broker
- [Cloudflare Pages](https://pages.cloudflare.com/) - 免费托管服务

## 📞 支持

如有问题，请：
1. 查看文档
2. 检查浏览器控制台
3. 查看ESP32串口日志

---

**版本**: v1.0  
**更新日期**: 2026-02-25  
**作者**: ESP32 Team

---

*让远程控制变得简单而优雅！*
