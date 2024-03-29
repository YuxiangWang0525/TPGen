# maimai Trip Partner Stickers Generator - 舞萌DX旅行伙伴表情包生成器
使用Vue+canvas实现
使用到的主要依赖如下:  
naive-ui:2.38.1  
vue:3.4.21
## 私有化部署指引:
### 克隆仓库
```bash
git clone https://github.com/YuxiangWang0525/TPGen.git
```
### 安装依赖  
```bash
npm install 或 yarn install
```
### 启动Vite开发服务器
```bash
npm run dev 或 yarn dev
```
二次开发或确认功能
### 编译发行版
```bash
npm run build 或 yarn build
```
查看项目根目录下的dist文件夹,它应该含有assets文件夹和index.html
### 部署到平台
#### 常规Web服务器
上传所有文件即可
#### GitHub Pages
将编译后文件新建分支,将项目独立部署
#### 热铁盒网页托管(及其他静态托管服务)  
请确保网页部署的位置在当前Web配置的Web访问根目录下  
例如 https://tpgen.yuxiangwang0525.com  
不要有根路径存在  
例如 https://yuxiangwang0525.com/tpgen