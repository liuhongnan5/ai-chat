# ===========================================
# 阿里云部署配置
# ===========================================

# 1. 阿里云 Serverless (Next.js)
# -----------------------------------
# 环境变量（需要在阿里云函数计算控制台配置）：
# - NEXT_PUBLIC_API_URL: 扣子编程API地址
# - API_KEY: API密钥（如有）

# 阿里云函数计算FC部署示例：
# 使用 Serverless Devs: https://help.aliyun.com/document_detail/195297.html
# s.yaml 配置示例（需要补充以下内容）:

# s.yaml:
#   edition: 1.0.0
#   name: ai-chat-app
#   access: default  # 需配置阿里云密钥
#   
#   services:
#     web:
#       component: fc
#       props:
#         region: cn-hangzhou  # 需修改为实际区域
#         service:
#           name: ai-chat-service
#           internetAccess: true
#         function:
#           name: ai-chat-function
#           runtime: nodejs20
#           codeDir: ./
#           command: npm run build && npm run start
#           memorySize: 1024
#           timeout: 60
#         triggers:
#           - type: http
#             name: http-trigger
#             config:
#               authType: anonymous
#               methods:
#                 - GET
#                 - POST
#         customDomains:
#           - domainName: auto
#             protocol: https

# 2. 阿里云 ECS/CVM 部署
# -----------------------------------
# 部署命令（需要补充以下内容）:
# 1. 安装 Node.js 20+
# 2. 安装 Nginx
# 3. 配置 Nginx 反向代理
# 4. 使用 PM2 管理进程: pm2 start npm --name "ai-chat" -- run start

# ===========================================
# 腾讯云部署配置
# ===========================================

# 1. 腾讯云 Serverless (Next.js)
# -----------------------------------
# 环境变量（需要在腾讯云云函数控制台配置）：
# - NEXT_PUBLIC_API_URL: 扣子编程API地址
# - API_KEY: API密钥（如有）

# 腾讯云 Serverless Framework 部署示例：
# serverless.yml 配置示例（需要补充以下内容）:

# serverless.yml:
#   component: scf
#   name: ai-chat-app
#   inputs:
#     name: ai-chat-function
#     region: ap-guangzhou  # 需修改为实际区域
#     runtime: Nodejs20
#     timeout: 60
#     memorySize: 1024
#     codeUri: ./
#     handler: index.main
#     environment:
#       variables:
#         NEXT_PUBLIC_API_URL: ""  # 需补充
#         API_KEY: ""  # 需补充

# 2. 腾讯云 CVM 部署
# -----------------------------------
# 部署命令（需要补充以下内容）:
# 1. 安装 Node.js 20+
# 2. 安装 Nginx
# 3. 配置 Nginx 反向代理到 3000 端口
# 4. 使用 PM2: pm2 start npm --name "ai-chat" -- run start

# ===========================================
# 通用部署检查清单
# ===========================================
# [ ] 确认 NEXT_PUBLIC_API_URL 已配置
# [ ] 确认 API_KEY 已配置（如需要）
# [ ] 确认服务器开放 80/443 端口
# [ ] 确认域名已备案（国内云）
# [ ] 配置 SSL 证书
# [ ] 配置防火墙规则

# ===========================================
# 注意事项
# ===========================================
# 1. 扣子编程API无鉴权，代理层可一定程度保护
# 2. 建议生产环境添加访问频率限制
# 3. 国内云部署需完成ICP备案
# 4. 建议使用PM2保持服务持续运行
