# Docker管理工具Portainer忘记admin登录密码怎么办?
`docker ps -a`
`docker stop `
`docker inspect `
找到Portainer容器挂载信息

![Image](https://github.com/user-attachments/assets/76be5cce-4ed7-4aac-8209-c61f3b884b09)

`docker run --rm -v /**dockerpath**:/data portainer/helper-reset-password`

[https://www.cnblogs.com/A1999/p/15993682.html](url)