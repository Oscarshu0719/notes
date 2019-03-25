# Python Note (Mainly for PyQt5)
[TOC]

## 利用Spyder中Variable Explorer查看變量屬性
``` Python
import inspect
# 初始化
local_vars = {}
# 顯示在Variable Explorer
local_vars = inspect.currentframe().f_locals
```
## 重定向
``` Python
savedStdout = sys.stdout  # 保存標準輸出流
with open('C:\\Users\\vm3y3\\Desktop\\out.txt', 'a+') as file:
    sys.stdout = file  # 重訂向到文件
    ...

    file.close() # 需先關閉文件
sys.stdout = savedStdout  # 恢復標準輸出流
```

## 文件夾遍歷
``` Python
import os
# 遞歸遍歷所有子文件夾
for i, j, k in os.walk(PATH):
    print(i, j, k)

# 僅該路徑下文件夾
print(os.listdir(PATH))
```

## IPython kernel dies for second run of PyQt5 GUI(using Spyder)
``` Python
# Replace `app = QtWidgets.QApplication(sys.argv)`
# with codes below:
from PyQt5 import QtCore, QtWidgets

app = QtCore.QCoreApplication.instance()
if app is None:
    app = QtWidgets.QApplication(sys.argv)
```

## AVX Warning of Tensorflow
```Python
import tensorflow as tf
import os

os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'
```

## Spyder Hotkey
:::info
< Ctrl + 1 > -> Comment / Cancel

< Ctrl + 4 / 5 > -> Cell Comment / Cancel

< Ctrl + D > -> Delete the line

< Ctrl + G > -> Search Definition of the function

< Ctrl + L > -> Change to the line

< Shift + Ctrl + C > -> Change Cursor to Console

< F5 > -> Run

< F12 > -> Set Breakpoint

< F11 > -> Full-Screen mode

< Ctrl + Enter > -> Run cell

< Shift + Enter > -> Run cell and shift to next cell
:::

## `__init__`
``` Python
class person():
    def __init__(self,name,gender,birth,**kw):
        self.name=name
        self.gender=gender
        self.birth=birth
        for k,w in kw.items():
            setattr(self,k,w)
    def sayhi(self):
        print ('my name is',self.name)
xiaoming = person('Xiao Ming', 'Male', '1991-1-1',job='student',tel='18089355',stdid='15010')
xiaohong = person('Xiao Hong', 'Female', '1992-2-2')
print (xiaoming.name)
print (xiaohong.birth)
print (xiaoming.job)
print (xiaoming.tel)
print (xiaoming.stdid)
print (xiaoming.sayhi())

Output: 
>>> Xiao Ming
1992-2-2
student
18089355
15010
my name is Xiao Ming
None
```

## Private
:::info
私有變量和函數用'__'開頭，例如：__name，不能在類外進行讀寫操作
:::

## Inheritance
:::info
可以多重繼承：
搜尋順序，是從子類開始，接著是同一階層父類由左至右搜尋，再至更上層同一階層父類由左至右搜尋，直到達到頂層為止
:::

``` Python
class A(B): # class A 繼承 class B
    ...
```

``` Python
class A: # 所有類就算沒寫出父類，也默認繼承class object
    ...
等於
class A(object):
    ...
```

``` Python
class CheckingAccount(Account):
    def __init__(self, id, name):
        super(CheckingAccount, self).__init__(id, name) # 呼叫父類別__init__()
```


``` Python
# __bases__：記錄著所繼承的父類，為tuple，可以通過修改此特性，變更繼承的父類

>>> C.__bases__
(<class '__main__.A'>,)
>>> C.__bases__ = (B,) # 改為繼承class B
"""
```

## `@property`
``` Python
# 不希望某變量被存取、設定或刪除，在進行操作前，得到一些通知。必須繼承class object
# property([fget[, fset[, fdel[, doc]]]])
# -> fget：存取時執行，fset：設定時執行，fdel：刪除時執行

class A(object):
    def __init__(self):
        self.a = None
    def getA(self):
        return self.a
    def setA(self, val):
        self.a = val
    def delA(self):
        del self.a
    param = property(getA, setA, delA)
等於
class A(object):
    def __init__(self):
        a = None
    @property
    def getA(self):
        return self.a
    @a.setter
    def setA(self, val):
        self.a = val
    @a.deleter
    def delA(self):
        del self.a
```

## `@classmethod`
``` Python
# 表示接下来的函数是类别方法
# 对类做的所有修改，都会影响到所有物件

# 计算该类已建立多少物件
class A():
    count = 0
    def __init__(): 
        A.count += 1
    @classmethod
    def kids(cls): # cls表类本身
        print("Count: ", cls.count) # cls.count可换成A.count

a = A()
b = A()
c = A()

print(A.kids())
```

## `@staticmethod`
``` Python
# 表示接下来的函数是类别方法
# 不会影响到类及其物件
# 没有self或cls

# 计算该类已建立多少物件
class A():
    @staticmethod
    def comment():
        print('This is a comment.')

## 系统操作
	- `os`
        - `exists()`：检查档案或目录是否存在
            - e.g. `os.path.exists('test.txt')
        - `isfile()`, sdir()`：检查是否为合法档案，检查是否为目录
            - e.g. `os.path.isfile('test.txt')
        - `isabs()`：检查是否为绝对路径
            - e.g. `os.path.isabs('test.txt')
        - `rename()`：更改名称
            - e.g. `os.rename('test.txt', 'a.txt')
        - `abspath()`：取得绝对路径名称
            - e.g. `os.path.abspath('test.txt')
        - `realpath()`：取得符号链接路径名称
            - e.g. `os.path.realpath('test.txt')
        - `remove()`：删除档案
            - e.g. `os.remove('test.txt')
        - `mkdir()`, `rmdir()`, listdir()`, `chdir()`：建立、删除、列出、变更目录
            - e.g. `os.mkdir('test_dir')
	- `glob`
		- `glob()`：列出匹配的档案（支持部分正则表达式）
			- e.g. `glob.glob('a*')` # 匹配a开头的所有档案和目录
	- `shutil`
		- `copy()`：复制
			- e.g. `shutil.copy('a.txt', 'b.txt')` # 将a.txt复制到b.txt
		- `move()`：复制并移除原本档案
			- e.g. `shutil.move('a.txt', 'b.txt')` # 将a.txt复制到b.txt，并移除a.txt

A.comment()
```

***
## PyQt5框架
### Qt Designer
 - (Omitted)
***
### 主視窗
#### QMainWindow
    - addToolBar()：增加工具列
    - centralWidget()：返回視窗中心的一個控制項
    - menuBar()：返回主視窗的功能表
    - setCentralWidget()：設定視窗中心的控制項
    - setStatusBar()：設定狀態列
    - statusBar()：取得狀態列物件
    - showMessage(message, int timeout = 0)：顯示狀態列信息
    - resize()：窗口尺寸
    - move()：移動到特定窗口位置
    - x(), y()：窗口的x, y軸
    - geometry()：取得視窗長和寬
    - setWindowTitle()：設定視窗名稱 
    - sender()：傳送信號的物件

#### QDesktopWidget
    - screenGeometry()：取得螢幕長和寬

#### QApplication
***
### 視窗控制項
#### QWidget
    - x(), y()：窗口的x, y軸
    - width(), height()：客戶區的寬和長
    - geometry()：客戶區的x(), y(), width(), height()
    - frameGeometry()：x(), y()：窗口的x, y軸；width(), height()：整個視窗的寬和長
    - resize()
    - size()：取得客戶區大小
    - setFixedWidth(int width), setFixedHeight(int heught)：分別固定寬度和高度
    - setFixedSize(QSize size), setFixedSize(int width, ing height)：長和高都固定，也不能使用滑鼠改變
    - setGeometry(int x, int y, int width, int height), setGeometry(QRect rect)：改變客戶區大小
    - move()
    - pos()：取得視窗左上角座標
    - setWindowTitle()
    - setWindowIcon()：設定視窗圖案
    - setToolTip()：設定氣泡提示
***
### 按鈕控制項
#### QPushButton - 按鈕
    - setCheckable()：設定按鈕是否已選中，若為setCheckable(True)表示已點擊
    - toggle()：在按鈕狀態之間切換
    - setIcon()：設定按鈕上的圖案
    - setEnabled()：設定按鈕是否可啟用，若為setEnabled(False)表示不可用
    - isChecked()：返回按鈕狀態
    - setDefault()：設定按鈕的預設狀態
    - setText()
    - text()

#### QRadioButton - 單選鈕控制項
    - setCheckable()：設定按鈕是否已選中，若為setCheckable(True)表示已點擊
    - isChecked()：返回按鈕狀態
    - setText()
    - text()

#### QCheckBox - 核取方塊
    - setChecked()：設定核取方塊是否已選中，若為setCheckable(True)表示已點擊
    - isChecked()：返回核取方塊狀態
    - setTriState()：設定為三態核取方塊
       - Qt.Checked：2，選中
       - Qt.PartiallyChecked：1，半選中
       - Qt.Unchecked：0，未選中
    - setText()
    - text()

#### QComboBox - 下拉式清單方塊
    - addItem()：增加一個下拉項
    - addItems()：從清單增加下拉項
    - Clear()：刪除下拉選項集合的所有選項
    - count()：返回下拉選項集合的數目
    - currentText()：返回選中項目的文字
    - itemText(i)：取得索引為i的item的選項文字
    - currentIndex()：返回選中項目的索引
    - setItemText(int index, text)：改變序號為index項的文字
    - Activated：當選中一個下拉項時發出信號
    - currentIndexChanged：當下拉項的索引改變時發出信號
    - hightlighted：當選中一個已經選中的下拉項時發出信號

#### QLabel - 標籤，作為預留位置，用以顯示不可編輯的文字和圖片
    - setAlignment()：
       - Qt.AlignLeft：水平方向靠左對齊
       - Qt.AlignRight：水平方向靠右對齊
       - Qt.AlignCenter：水平方向置中對齊
       - Qt.AlignJustify：水平方向兩端對齊
       - Qt.AlignTop：垂直方向靠上對齊
       - Qt.AlignBottom：垂直方向靠下對齊
       - Qt.AlignVCenter：垂直方向置中對齊
    - setIndent()：設定文字縮排值
    - setPixmap()：設定為一張Pixmap圖片
    - text()：取得文字內容
    - setText()：設定文字內容
    - selectedText()：返回選擇的字元
    - setBuddy()：設定快速鍵，並利用&設定助記號
    - setWordWrap()：設定是否允許換行
    - linkActivated：按一下嵌入標籤超連結
       - 若希望以新視窗打開超連結，須加上setOpenExternalLinks(true)
    - linkHovered：滑鼠游標滑過嵌入標籤超連結
***
### 計數器
#### QSPinBox
    - (Omitted)
***
### 滑動條
#### QSlider
    - (Omitted)

***
### 文字方塊控制項
#### QLineEdit - 單列文字方塊控制項
    - setAlignment()：
       - Qt.AlignLeft：水平方向靠左對齊
       - Qt.AlignRight：水平方向靠右對齊
       - Qt.AlignCenter：水平方向置中對齊
       - Qt.AlignJustify：水平方向兩端對齊
       - Qt.AlignTop：垂直方向靠上對齊
       - Qt.AlignBottom：垂直方向靠下對齊
       - Qt.AlignVCenter：垂直方向置中對齊
    - clear()：清除文字方塊內容
    - setEchoMode()：
       - QLineEdit.Normal：正常輸入字元，為預設值
       - QLineEdit.NoEcho：不顯示任何輸入字元
       - QLineEdit.Password：顯示與平台相關的密碼遮罩字元
       - QLineEdit.PasswordEchoOnEdit：在編輯時顯示字元，負責顯示密碼類型的字元
    - setPlaceholderText()：設定文字方塊浮顯文字
    - setMaxLength()
    - setReadOnly()
    - setText()
    - Text()
    - setDragEnabled()：設定文字方塊是否接受拖曳
    - selectAll()
    - setFocus()：取得焦點
    - setInputMask()：設定遮罩
    - setValidator()：
       - QIntValidator：限制輸入整數
       - QDoubleValidator：限制輸入浮點數
    - QRegexpValidator：檢查輸入是否符合規則運算式
    - selectionChanged：改變時發出信號
    - textChanged：修改文字時發出信號
    - editingFinished：當編輯文字結束時發出信號

#### QTextEdit - 多列文字方塊控制項
    - setPlainText()：設定多列文字方塊內容
    - toPlainText()：返回多列文字方塊內容
    - setHtml()：設定多列文字方塊內容為HTML檔案
    - toHtml()：返回多列文字方塊內容的HTML檔案
    - clear()：清除多列文字方塊內容

#### QToolTip
    - setFont：設定氣泡提示字體的字型和大小
***
### 對話方塊控制項
#### QDialog
    - setWindowTitle()
    - setWindowModality()
       - Qt.NonModal：非模態，可以和程式的其他視窗互動
       - Qt.WindowModal：視窗型模態，程式在未處理完目前的對話方塊前，將阻止和父視窗進行互動
       - Qt.ApplicationModal：應用程式型模態，阻止和任何其他視窗進行互動

#### QMessageBox - 彈出式對話方塊
    - information(QWidget parent, title, text, buttons, defaultButton)
    - question(QWidget parent, title, text, buttons, defaultButton)
    - warning(QWidget parent, title, text, buttons, defaultButton)
    - ctitical(QWidget parent, title, text, buttons, defaultButton)
    - about(QWidget parent, title, text)
    - setTitle()
    - setText()
    - setIcon()
    - 標準按鈕
       - QMessage.Ok：同意操作
       - QMessage.Cancel：取消操作
       - QMessage.Yes：同意操作
       - QMessage.No：取消操作
       - QMessage.Abort：終止操作
       - QMessage.Retry：重試操作
       - QMessage.Ignore：忽略操作

#### QInputDialog - 標準對話方塊
    - getInt()：從控制項取得標準整數輸入
    - getDouble()：從控制項取得標準浮點數輸入
    - getText()：從控制項取得標字串數輸入
    - getItem()：從控制項取得清單選項輸入

#### QFontDialog - 字體選擇對話方塊
    - (Omitted)

#### QFileDialog - 開啟和儲存檔案的標準對話方塊
    - getOpenFileName()：返回挑選的檔案名稱，並開啟該檔案
    - getSaveFileName()：使用選擇的檔案名稱並儲存
    - setFileMode()：可以選擇的檔案類型
       - QFileDialog.AnyFile：任何檔案
       - QFileDialog.ExistingFile：已存在的檔案
       - QFileDialog.Directory：目錄
       - QFileDialog.ExistingFiles：已經存在的多個檔案
    - setFilter()：設定篩選程式，只顯示過濾後的檔案類型
***
### 視窗繪圖控制項
#### QPainter
    - (Omitted)

#### QPen - 鋼筆
    - (Omitted)

#### QBrush - 筆刷
    - (Omitted)

#### QPixmap - 顯示繪圖設備的圖形
    - (Omitted)
***
### 拖曳與剪貼簿
#### QDrag - 拖曳
    - DropEnterEvent()：當拖曳一個控制項，並且滑鼠游標進入該控制項時，便觸發此事件，事件中可以取得操作的視窗控制項，還能夠有條件地接受或拒絕該拖曳操作
    - DragMoveEvent()：拖曳進行時會觸發此事件
    - DragLeaveEvent()：拖曳一個控制項，並且滑鼠離開該控制項時，便觸發此事件
    - DropEvent()：在目標控制項釋放拖曳操作時，便觸發此事件
    - 許多QWidget物件都支援拖曳動作，須設定QWidget.setDragEnabled(True)
    - QMimeData類函數：
|判斷函數|設定函數|取得函數|MIME類型|
|:---:|:---:|:---:|:---:|
|hasText()|text()|setText()|text/plain|
|hasHtml()|html()|setHtml()|text/html|
|hasUrls()|urls()|setUrls()|text/url-list|
|hasImage()|imageData()|setimageData()|image/*|
|hasColor()|colorData()|setcolorData()|application/x-color|

#### QClipboard - 剪貼簿
    - clear()：清除剪貼簿內容
    - setImage()：將QImage物件複製到剪貼簿
    - setMimeData()：將MIME資料複製到剪貼簿
    - setPixmap()：將Pixmap物件複製到剪貼簿
    - setText()：將文字複製到剪貼簿
    - text()：從剪貼簿取得文字
    - dataChanged：當剪貼簿內容發生變化時發出信號
***
### 日曆與時間
#### QCalender - 日曆
    - (Omitted)

#### QDateTimeEdit - 時間
    - (Omitted)
***
### 功能表、工具列與狀態列
#### QMenuBar - 功能表
    - menuBar()：返回主視窗的QMenuBar物件
    - addMenu()：在功能表增加一個新的QMenu物件
    - addAction()：對QMenu控制項增加一個操作按鈕
    - setEnabled()：在操作按鈕狀態設為啟用或禁用
    - addSeperator()：在功能表中加上一條分隔線
    - clear()：刪除功能表或功能列的內容
    - setShortcut()：將快速鍵關聯到操作按鈕
    - setText()：設定功能表項目的文字
    - setTitle()：設定QMenu控制項的標題
    - text()：返回與QAction物件關聯的文字
    - title()：返回QMenu控制項的標題
    - 每按一下QAction按鈕後，QMenu物件都會發出triggered信號

#### QToolBar - 可移動面板
    - addAction()：增加具有文字或圖示的工具按鈕
    - addSeperator()：分組顯示工具按鈕
    - addWidget()：增加按鈕以外的控制項到工具列
    - addToolBar()：使用QMainWindow類的方法增加一個新的工具列
    - setMovable()：工具列變得可移動
    - setOrientation()：工具列的方向可以設為Qt.Horizontal或Qt.Vertical
    - 每按一下工具列按鈕後，QMenu物件都會發出actionTriggered信號，同時也會傳送關聯的QAction物件操照給連接的槽函數

#### QStatusBar - 狀態列
    - addWidget()：在狀態列增加給定的視窗小控制項物件
    - addPermanentWidget()：在狀態列永久加上給定的視窗小控制項物件
    - showMessage()：在狀態列顯示一筆臨時信息，並指定時間間隔
    - clearMessage()：刪除正在顯示的臨時信息
    - removeMessage()：從狀態列刪除指定的小控制項
***
### 表格與樹
#### QTableView - 以自訂的資料模型顯示內容
    - 模型：
       - QStringListModel：儲存一組字串
       - QStandardItemModel：儲存任意層級結構的資料
       - QDirModel：封裝檔案資料
       - QSqlQueryModel：封裝SQL的查詢結果集
       - QSqlTableModel：封裝SQL的資料表
       - QSqlRelationalTableModel：封裝帶有foreign key的SQL資料表
       - QSortFilterProxyModel：排序或過濾模型中的資料

#### QListView - 展示資料
    - setModel()：設定和View關聯的Model，可使用list類型作為資料來源
    - selectedItem()：選中Model的項目
    - isSelected()：判斷Model中是否選取某項目
    - clicked：按一下項目時發出信號
    - doubleClicked：按兩下項目時發出信號

#### QListWidget - 列表增加和刪除項目
    - addItem()：在列表中增加QListWidgetItem物件或字串
    - addItems()：增加列表的每個項目
    - insertItem()：在指定的索引處插入項目
    - clear()：刪除列表內容
    - setCurrentItem()：設定目前所選的項目
    - sortItems()：按升冪重新排序項目
    - currentItemChanged：當列表項目發生改變時發出信號
    - itemClicked：當點擊列表的項目時發出信號

#### QTableWidget - 顯示資料表格
    - setRowCount(int row)：設定QTableWidget表格控制項的列數
    - setColumnCount(int col)：設定QTableWidget表格控制項的行數
    - setHorizontalHeaderLabels()：設定QTableWidget表格控制項的水平標籤
    - setVerticalHeaderLabels()：設定QTableWidget表格控制項的垂直標籤
    - setItem(int, int, QTableWidgetItem)：在QTableWidget表格控制項每個項目的單元空間裡，增加新的控制項
    - horizontalHeader()：取得QTableWidget表格控制項的表頭，以便隱藏
    - rowCount()：取得QTableWidget表格控制項的列數
    - columnCount()：取得QTableWidget表格控制項的行數
    - setEditTriggers(EditTriggers triggers)：設定表格是否可編輯，並填入編輯規則的列舉項
    - setSelectionBehavior：設定表格的選擇行為
    - setTextAlignment()：設定儲存格的對齊方式
    - setSpan(int row, int column, int rowSpanCount, int columnSpanCount)：合併儲存格，若想改變第row列第column行，則要合併rowSpanCount列數和columnSpanCount行數
    - setShowGrid()：表格預設為True，帶有格線；False，則否
    - setColumnWidth(int column, int width)：設定儲存格的行寬
    - setRowHeight(int row, int height)：設定儲存格的列高
    - 編輯規則的列舉值：
|選項|值|描述|
|:---:|:---:|:---:|
|QAbstractItemView.NoEditTriggers0No|0|不能修改表格內容|
|QAvstractItemView.CurrentChanged1Editing|1|任何時候都能修改儲存格|
|QAvstractItemView.DoubleClicked2Editing|2|按兩下儲存格|
|QAvstractItemView.SelectedClicked4Editing|4|按一下已選中的內容|
|QAvstractItemView.EditKeyPressed8Editing|8|按修改鍵時編輯儲存格|
|QAvstractItemView.AnyKeyPressed16Editing|16|按任意鍵修改儲存格|
|QAvstractItemView.AllEditTriggers31Editing|31|包括以上所有條件|
    - 表格的選擇行為：
|選項|值|描述|
|:---:|:---:|:---:|
|QAbstractItemView.SelectItems0Selecting|0|選中單個儲存格|
|QAbstractItemView.SelectRows1Selecting|1|選中一列|
|QAbstractItemView.SelectColumns2Selecting|2|選中一行|
    - 儲存格的水平對齊方式：
       - Qt.AlignLeft：將內容沿儲存格靠左對齊
       - Qt.AlignRight：將內容沿儲存格靠右對齊
       - Qt.AlignHCenter：在可用空間，居中顯示於水平方向
       - Qt.AlignJustify：將文字在可用空間中對齊，預設是從左到右
    - 儲存格的水平對齊方式：
       - Qt.AlignTop：與頂部對齊
       - Qt.AlignBottom：與底部對齊
       - Qt.AlignVCenter：在可用空間，居中顯示於垂直方向
       - Qt.AlignBaseline：與基線對齊

#### QTreeView - 樹狀結構
    - QTreeWidget
       - setColumnWidth(int column, int width)：將指定行的寬度設為給定值
       - insertTopLevelItems()：在視圖的頂層索引插入項目
       - expandAll()：展開所有樹狀節點
       - invisibleRootItem()：返回樹狀控制項中不可見的根項目
       - selectedItems()：返回所有選定的非隱藏項目
    - QTressWidgetItem
       - addChild()：將子項目加到子列表中
       - setText()：設定顯示的節點文字
       - Text()：返回顯示的節點文字
       - setCheckState(column, state)：設定指定行的選中狀態；
          - Qt.Checked：選中節點
          - Qt.Unckecked：未選中節點
       - setIcon(column, row)：在指定行顯示圖示
***
### 更多控制項
#### QTabWidget - 提供一個標籤頁和一個頁面區域
    - addTab()：將一個控制項加到Tab控制項中
    - insertTab()：將一個Tab控制項插入到指定位置
    - removeTab()：根據指定Tab控制項插入指定位置
    - setCurrentIndex()：設定目前可見的標籤頁所在的索引
    - setCurrentWidget()：設定目前可見的頁面
    - setTabBar()：設定標籤頁的列控制項
    - setTabPosition()：設定標籤頁的位置
       - QTabWidget.North：顯示在頁面的上面
       - QTabWidget.South：顯示在頁面的下面
       - QTabWidget.West：顯示在頁面的左側
       - QTabWidget.East：顯示在頁面的右側
    - setTabText()：定義Tab標籤頁的顯示值
    - currentChanged：切換到目前頁面時發出信號

#### QStackedWidget - 一個堆疊視窗

#### QDockWidget - QMainWindow內浮動狀態的視窗控制項
    - setWidget()：在Dock視窗區域設定QWidget
    - setFloating()：設定Dock視窗是否可以浮動，若為True，表示可以浮動
    - setAllowedAreas()：設定視窗可以停靠的區域
       - LeftDockWidgetArea：停靠左邊區域
       - RightDockWidgetArea：停靠右邊區域
       - TopDockWidgetArea：停靠頂部區域
       - BottomDockWidgetArea：停靠底部區域
       - NoDockWidgetArea：不顯示Widget
    - setFeatures()：設定停靠視窗的功能屬性
       - DockWidgetClosable：可關閉
       - DockWidgetMovable：可移動
       - DockWidgetFloatable：可浮動
       - DockWidgetVerticalTitleBar：在左邊顯示垂直的標籤欄
       - AllDockWidgetFeatures：具有前三種屬性的所有功能
       - NoDockWidgetFeatures：無法關閉，不能移動，無法浮動

#### QMdiArea, QMdiSubWindow - 多文字介面
    - addSubWindow()：將一個小控制項加入MDI區域，作為一個新的子視窗
    - removeSubWindow()：刪除子視窗的一個小控制項
    - setActiveSubWindow()：啟動一個子視窗
    - cascadeSubWindows()：安排子視窗在MDI區域階梯式並排顯示
    - tileSubWindows()：安排子視窗在MDI區域磚塊式並排顯示
    - closeActiveSubWindow()：關閉作用中的子視窗
    - subWindowList()：返回MDI區域的子視窗清單
    - setWidget()：設定一個小控制項，作為QMdiSubwindow實例物件的內部控制項

#### QScrollBar - 捲軸
    - valueChanged：當滑動條的值改變時發出信號
    - sliderMoved：當使用者拖動滑塊時發出信號
***
### 多執行緒
#### QTimer - 計時器
    - (Omitted)

#### QThread - Qt執行緒核心的底層類別
    - (Omitted)

#### QApplication.processEvents() - 事件處理
    - (Omitted)

#### QWebEngineView - 網頁互動
    - (Omitted)
***
### 佈局管理
#### QBoxLayout - 框佈局
    - QHBoxLayout - 水平佈局
       - addLayout(self, QLayout, stretch = 0)：在視窗的右邊加入佈局，並已stretch進行伸縮，伸縮預設為0
       - addWidget(self, QWidget, stretch, QT.Alignment alignment)：在佈局中加入控制項
       - addSpacing(self, int)：設定各控制項的上下間距，可增加額外的空間
       - 對齊方式參數：
          - Qt.AlignLeft：水平方向靠左對齊
          - Qt.AlignRight：水平方向靠右對齊
          - Qt.AlignCenter：水平方向置中對齊
          - Qt.AlignJustify：水平方向左右對齊
          - Qt.AlignTop：垂直方向靠上對齊
          - Qt.AlignBottom：垂直方向靠下對齊
          - Qt.AlignCenter：垂直方向置中對齊
    - QVBoxLayout - 垂直佈局
    - QBoxLayout.addStretch(int stretch = 0)：增加一個可伸縮的控制項，並將stretch作為伸縮量加到佈局末尾，0為最小值

#### QGridLayout - 格子佈局
    - addWidget(QWidget widget, int row, int col, int alignment = 0)：在佈局中加入控制項，設定傳入的行和列
    - addWidget(QWidget widget, int fromRow, int fromColumn, int rowSpan, int columnSpan, Qt.Alignment alignment = 0)：在佈局中加入控制項，當跨越多行或多列時使用
    - setSpacing(int spacing)：設定控制項在水平和垂直方向的間隔

#### QFormLayout - 表格佈局

#### 巢狀佈局

#### QSplitter - 動態佈局管理器
    - addWidget()：將小控制項加到QSplitter管理器的佈局中
    - indexOf()：返回小控制項在QSplitter管理器的索引
    - insertWidget()：根據指定的索引，插入一個控制項到QSplitter管理器
    - setOrientation()：設定佈局方向；Qt.Horizontal：水平方向；Qt.Vertical：垂直方向
    - setSizes()：設定控制項的初始化大小
    - count()：返回小控制項在QSplitter管理器的數量
