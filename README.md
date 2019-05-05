# tpm-dev

### 工具
[Linux TPM2 & TSS2 Software](https://github.com/tpm2-software)


### IBM-swTPM配置过程中的问题
按说明配置后每次启动tpm_server 都必须先运行 tpmbios。  
但正常情况下无法正常运行tcsd，猜测是`sudo tcsd -e -f`使用sudo权限，而tpm_server则是普通用户权限，两者进程间无法通信。  
使用`sudo tpm_server`提示环境变量缺失，无奈直接使用root用户。   
按顺序运行tpm_server tpmbios tcsd之后基本可以正常运行，目前暂未测试，但是tcsd似乎仍有一些问题，猜测可能是先前修改了tcsd的配置文件。   
