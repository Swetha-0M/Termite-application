# Termite-application
from PyQt6 import QtCore, QtGui, QtWidgets
import sys
from PyQt6.QtGui import QIcon
from PyQt6.QtWidgets import *
from page22 import Ui_second_obj


class Ui_MainWindow(object):
    def openWindow(self):
        self.window = QtWidgets.QMainWindow()
        self.ui = Ui_second_obj()
        self.ui.setupUi(self.window)
        self.window.show()

    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(780, 500)
        MainWindow.setWindowFlags(QtCore.Qt.WindowType.CustomizeWindowHint | QtCore.Qt.WindowType.WindowCloseButtonHint
                                  | QtCore.Qt.WindowType.WindowMinimizeButtonHint)
        MainWindow.setWindowIcon(QIcon('termite_img.png'))
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        self.outputWindow = QtWidgets.QTextEdit(self.centralwidget)
        self.outputWindow.setGeometry(QtCore.QRect(10, 50, 491, 241))
        self.outputWindow.setObjectName("outputWindow")
        self.sendInputLine = QtWidgets.QLineEdit(self.centralwidget)
        self.sendInputLine.setGeometry(QtCore.QRect(10, 300, 441, 21))
        self.sendInputLine.setObjectName("sendInputLine")
        self.layoutWidget = QtWidgets.QWidget(self.centralwidget)
        self.layoutWidget.setGeometry(QtCore.QRect(10, 20, 493, 26))
        self.layoutWidget.setObjectName("layoutWidget")
        self.horizontalLayout = QtWidgets.QHBoxLayout(self.layoutWidget)
        self.horizontalLayout.setContentsMargins(0, 0, 0, 0)
        self.horizontalLayout.setObjectName("horizontalLayout")
        self.connectButton = QtWidgets.QPushButton(self.layoutWidget)
        self.connectButton.setObjectName("connectButton")
        self.horizontalLayout.addWidget(self.connectButton)
        # self.settingsButton = QtWidgets.QPushButton(self.layoutWidget)
        self.settingsButton = QtWidgets.QPushButton(self.layoutWidget, clicked = lambda: self.openWindow())
        self.settingsButton.setObjectName("settingsButton")

        self.horizontalLayout.addWidget(self.settingsButton)
        self.clearButton = QtWidgets.QPushButton(self.layoutWidget)
        self.clearButton.setObjectName("clearButton")
        # connect buttons 'CLEAR' to function
        self.clearButton.clicked.connect(self.outputWindow.clear)
        self.horizontalLayout.addWidget(self.clearButton)
        # self.aboutButton = QtWidgets.QPushButton(self.layoutWidget)
        # self.aboutButton = QtWidgets.QPushButton(self.layoutWidget, clicked = lambda: self.show_popup())
        self.aboutButton = QtWidgets.QPushButton(self.layoutWidget)
        # self.aboutButton.clicked.connect(self.show_popup)
        self.aboutButton.setObjectName("aboutButton")
        self.horizontalLayout.addWidget(self.aboutButton)
        self.closeButton = QtWidgets.QPushButton(self.layoutWidget)
        self.closeButton.clicked.connect(QtCore.QCoreApplication.instance().quit)
        # self.closeButton.clicked.connect(self.closeIt)
        self.closeButton.setObjectName("closeButton")
        self.horizontalLayout.addWidget(self.closeButton)
        self.enterButton = QtWidgets.QPushButton(self.centralwidget)
        # self.enterButton.clicked.connect()
        self.enterButton.setGeometry(QtCore.QRect(460, 300, 41, 24))
        self.enterButton.setText("")
        icon = QtGui.QIcon()
        icon.addPixmap(QtGui.QPixmap("e1.png"), QtGui.QIcon.Mode.Normal, QtGui.QIcon.State.Off)
        self.enterButton.setIcon(icon)
        self.enterButton.setIconSize(QtCore.QSize(60, 60))
        self.enterButton.setObjectName("enterButton")
        MainWindow.setCentralWidget(self.centralwidget)

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    # def closeIt(self):
    #     self.close()


    def show_popup(self):
        msg = QMessageBox()
        msg.setWindowTitle('About Termite 3.4')
        msg.setText('Termite is simple RS232 communication tool')
        msg.setIcon('termite_img.png')  # QIcon
        x = msg.exec_()

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "Termite 3.4 (by CompuPhase)"))
        self.connectButton.setText(_translate("MainWindow", "Disconnected-click to connect"))
        self.settingsButton.setText(_translate("MainWindow", "Settings"))
        self.clearButton.setText(_translate("MainWindow", "Clear"))
        self.aboutButton.setText(_translate("MainWindow", "About"))
        self.closeButton.setText(_translate("MainWindow", "Close"))


if __name__ == "__main__":
    app = QtWidgets.QApplication(sys.argv)
    FirstWindow = QtWidgets.QMainWindow()
    ui = Ui_MainWindow()
    ui.setupUi(FirstWindow)
    FirstWindow.show()
    sys.exit(app.exec())
