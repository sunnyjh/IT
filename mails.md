# python send emails

## 1.利用qq邮箱发送邮件
  
    #!/usr/bin/python3

    import smtplib
    from email.mime.text import MIMEText
    from email.header import Header

    # 第三方 SMTP 服务
    mail_host="smtp.qq.com"  #设置服务器
    mail_user="530631297"    #用户名
    mail_pass="icvzljazjrubcbaj"   #口令 

    sender = '530631297@qq.com'
    receivers = ['jiangdezhichen@163.com','530631297@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱

    mail_msg = """
    <p>Python 邮件发送测试...</p>
    <p><a href="http://www.runoob.com">这是一个链接</a></p>
    """
    message = MIMEText(mail_msg, 'html', 'utf-8')
    message['From'] = Header("菜鸟教程", 'utf-8')
    message['To'] =  Header("111", 'utf-8')

    subject = 'Python SMTP 邮件测试'
    message['Subject'] = Header(subject, 'utf-8')

    try:
        smtpObj = smtplib.SMTP_SSL("smtp.qq.com",465)
        smtpObj.login(sender,mail_pass)
        smtpObj.sendmail(sender,receivers,message.as_string())
        print ("邮件发送成功")
    except smtplib.SMTPException as err:
        print (err)
        print ("Error: 无法发送邮件")

## 2.利用mail.berryoncology.com发送邮件

        #!/usr/bin/python3
        
        import smtplib
        from email.mime.text import MIMEText
        from email.header import Header
        
        # 第三方 SMTP 服务
        mail_host="mail.berryoncology.com"  #设置服务器
        mail_user="jiangdzh3403"    #用户名
        mail_pass="jiangdzh_2013"   #口令 
        
        sender = 'jiangdzh3403@berryoncology.com'
        receivers = ['jiangdzh3403@berryoncology.com','530631297@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
        
        mail_msg = """<p>Python 邮件发送测试...</p>
        <p><a href="http://www.runoob.com">这是一个链接111</a></p>
        """
        message = MIMEText(mail_msg, 'html', 'utf-8')
        message['From'] = Header("菜鸟教程", 'utf-8')
        message['To'] =  Header("测试", 'utf-8')
        
        subject = 'Python SMTP 邮件测试'
        message['Subject'] = Header(subject, 'utf-8')
        
        
        try:
            smtpObj = smtplib.SMTP()
            smtpObj.connect(mail_host, 25)    # 25 为 SMTP 端口号
            smtpObj.login(mail_user,mail_pass)
            smtpObj.sendmail(sender, receivers, message.as_string())
            print ("邮件发送成功")
        except smtplib.SMTPException as err:
            print (err)
            print ("Error: 无法发送邮件")


## 3.利用163邮箱发送邮件（代码好像有点问题，发送不出去）

        #!/usr/bin/python3
        
        import smtplib
        from email.mime.text import MIMEText
        from email.header import Header
        
        # 第三方 SMTP 服务
        mail_host="smtp.163.com"  #设置服务器
        mail_user="jiangdezhichen"    #用户名
        mail_pass="20150501jdzh"   #口令 
        
        sender = 'jiangdezhichen@163.com'
        receivers = ['530631297@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱
        
        mail_msg = """
        <p>Python 邮件发送...</p>
        <p><a href="http://www.runoob.com">这是一个链接</a></p>
        """
        message = MIMEText(mail_msg, 'html', 'utf-8')
        message['From'] = Header("我是谁", 'utf-8')
        message['To'] =  Header("小猪佩奇", 'utf-8')
        
        subject = 'Python'
        message['Subject'] = Header(subject, 'utf-8')
        
        
        try:
            smtpObj = smtplib.SMTP_SSL(mail_host,465)
            smtpObj.login(sender,mail_pass)
            smtpObj.sendmail(sender,receivers,message.as_string())
            print ("邮件发送成功")
        except smtplib.SMTPException as err:
            print (err)
            print ("Error: 无法发送邮件")
