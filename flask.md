#
## 1.关闭翻墙软件

## 2.在app.run中指定host和port，其中host必须指定为“0.0.0.0”，如下：
    
    from flask import Flask
    app = Flask(__name__)
 
    @app.route("/")
    def hello():
        return "Hello World!"
 
    if __name__ == "__main__":
        app.run(host="0.0.0.0",port=9090)
