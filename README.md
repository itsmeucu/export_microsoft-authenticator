# microsoft-authenticator-dump

导出TOTP

1. Microsoft Authenticator 中的2FA密钥数据存储路径为 /data/data/com.azure.authenticator/databases/PhoneFactor
2. PhoneFactor 文件本身是Sqlite数据库文件，所以复制文件时候需要复制PhoneFactor PhoneFactor-shm PhoneFactor-wal 这三个文件（如果有），可以通过Sqlite数据库操作软件来查看具体的数据信息。想要的数据就在 accounts 表中。
3. 使用dump.py提取
4. account_type为1的是微软本身的账户，为0的是手动添加的第三方账户。
5. 拿到数据以后我们可以导入到自己想要使用的任意软件了，可以手动输入secret_key，也可以直接将上面otpauth://开头的url直接生成二维码进行扫码导入。
6、默认会生成二维码，按回车显示下一个二维码，此时可以使用验证器扫码即可