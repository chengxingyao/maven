# maven
### 四、注册服务
```shell
#!/bin/bash
systemctl stop $CI_PROJECT_NAME.service
# 注册到服务 并启动 
mkdir -p /etc/systemd/system/
echo "[Unit]
Description=springboot service
After=syslog.target

[Service]
EnvironmentFile=/opt/${CI_PROJECT_NAME}/conf.ini
Type=simple
Restart=always
ExecStart= /opt/${CI_PROJECT_NAME}/${jarFileName}

[Install]
WantedBy=multi-user.target " > /etc/systemd/system/$CI_PROJECT_NAME.service
systemctl daemon-reload
systemctl start $CI_PROJECT_NAME.service

```
