**# Smart-Bartender
An automated bartending machine using raspberry pi 
**import sys
from PyQt5.QtCore import pyqtSlot
from PyQt5.QtWidgets import QApplication,QDialog,QPushButton
from PyQt5.uic import loadUi
import RPi.GPIO as gpio
import time


load1=17 ##VODKA
load2=27 ##BEER
load3=22 ##SOJU
load4=23 ##APPLE
load5=24 ##PINEAPPLE
load6=25 ##POMELO


gpio.setmode(gpio.BCM)
gpio.setwarnings(False)

gpio.setup(load1,gpio.OUT)
gpio.setup(load2,gpio.OUT)
gpio.setup(load3,gpio.OUT)
gpio.setup(load4,gpio.OUT)
gpio.setup(load5,gpio.OUT)
gpio.setup(load6,gpio.OUT)


class industrial(QDialog):
    def __init__(self):
        super(industrial,self).__init__()
        loadUi('design.ui',self)
        self.setWindowTitle('MENU')
        self.load_1.clicked.connect(self.load1)
        self.load_2.clicked.connect(self.load2)
        self.load_3.clicked.connect(self.load3)
        self.load_4.clicked.connect(self.load4)
        self.load_5.clicked.connect(self.load5)
        self.load_6.clicked.connect(self.load6)
        
        
        gpio.output(load1,gpio.HIGH)
        gpio.output(load2,gpio.HIGH)
        gpio.output(load3,gpio.HIGH)
        gpio.output(load4,gpio.HIGH)
        gpio.output(load5,gpio.HIGH)
        gpio.output(load6,gpio.HIGH)
       
        
    @pyqtSlot()
    
    
    
    
    
    
    
    
    
    def load1(self): ## APPLE + VODKA
        if gpio.input(load1):
            gpio.output(load4,gpio.LOW)
            time.sleep(6)
            gpio.output(load4,gpio.HIGH)
            time.sleep(1)
            gpio.output(load1,gpio.LOW)
            time.sleep(3)
            gpio.output(load1,gpio.HIGH)
  
  
   
      
    
        
        
        
        
        
        
            
    def load2(self): ##POMELO + VODKA
        if gpio.input(load1):
            gpio.output(load6,gpio.LOW)
            time.sleep(6)
            gpio.output(load6,gpio.HIGH)
            time.sleep(1)
            gpio.output(load1,gpio.LOW)
            time.sleep(3)
            gpio.output(load1,gpio.HIGH)
        
        
        
        
        
        
        
        
        
        
        
            
    def load3(self):   #APPLE + BEER
        if gpio.input(load3):
            gpio.output(load4,gpio.LOW)
            time.sleep(6)
            gpio.output(load4,gpio.HIGH)
            time.sleep(1)
            gpio.output(load2,gpio.LOW)
            time.sleep(3)
            gpio.output(load2,gpio.HIGH)
           
           
           
           
           
           
           
           
           
           
           
           
           
            
    def load4(self):        #PINEAPPLE + VODKA
        if gpio.input(load4):
            gpio.output(load5,gpio.LOW)
            time.sleep(6)
            gpio.output(load5,gpio.HIGH)
            time.sleep(1)
            gpio.output(load1,gpio.LOW)
            time.sleep(3)
            gpio.output(load1,gpio.HIGH)
            
            
            
            
            
            
            
            
            
            
            
            
            
            
    def load5(self):     #SOJU + PINEAPPLE
        if gpio.input(load5):
            gpio.output(load5,gpio.LOW)
            time.sleep(5)
            gpio.output(load5,gpio.HIGH)
            time.sleep(1)
            gpio.output(load3,gpio.LOW)
            time.sleep(3)
            gpio.output(load3,gpio.HIGH)
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
         
    def load6(self):      #BEER
        if gpio.input(load6):
            gpio.output(load2,gpio.LOW)
            time.sleep(5)
            gpio.output(load2,gpio.HIGH)   
            
    ####MIXED####    
            
            
  
            
            
            
            
            
            
            
            

app=QApplication(sys.argv)
widget=industrial()
widget.show()
sys.exit(app.exec_())
