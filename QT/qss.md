# QT使用笔记
* [首页](../README.md)    
* [Back](./README.md)
## QT中插入QSS

在main.cpp文件加入以下代码：

	QString getQssContent()  
	{  
	    QFile styleSheet(":/qss/abc.qss");  
	    if (!styleSheet.open(QIODevice::ReadOnly))
	    {
	        qWarning("Can't open the style sheet file.");
	        return "";
	    }
	    return styleSheet.readAll();
	}


main函数中调用  

	int main(int argc, char *argv[])
	{
	    QApplication a(argc, argv);
	    Widget w;
	    w.show();
	    a.setStyleSheet(getQssContent());
	    return a.exec();
	}

PS:在使用QT Creator 4.2 版本时存在无法打开qss文件得情况。度娘说是软件bug，可以更新QT Creator4.6.0    ([点击下载最新版本](http://download.qt.io/development_releases/qtcreator/)) 解决此问题。