更新时间:2023/12/10

easyUse个人版源代码
=
链接
-
[返回首页](szy2077.github.io)[返回至easyUse]
(szy2077.github.io/easyUse/index.html)
[产品](szy2077.github.io\things.html)

源代码
-
```py

#import
import os
import tkinter
import tkinter.filedialog
import tkinter.ttk
from os import system as command
from time import sleep
from tkinter import messagebox as msgbox
from tkinter.filedialog import askdirectory
import random
import sys

import ttkbootstrap
import ttkbootstrap.constants

from win10toast import ToastNotifier

import psutil

#check
try:open("c:\\easy\\easykey.txt")
except:msgbox.showwarning("警告","应用未激活")
else:
    #class
    class function():
        global coin

        def finishSetup(self=0):
            a = combobox2311.get()

            setWindow.destroy()

            with open("setting.txt", "w") as f:
                f.write(a+"\n")
                f.write(str(coin))

            toaster = ToastNotifier()
            toaster.show_toast(
                title="EasyUse专业版",
                msg="设置完成,请重启软件应用设置",
                icon_path="icon.ico",
                duration=10,
                threaded=True,
            )


        def clean_disk(self=0):
            if msgbox.askyesno("提示","确清理c盘?"):
                window2 = ttkbootstrap.Toplevel()
                window2.geometry("400x200")
                window2.title("easyUse v1.0")
                window2.iconbitmap("icon.ico")

                progressbar11 = tkinter.ttk.Progressbar(window2,length=300)
                tkinter.Label(window2, text="删除中...", font=("微软雅黑", 30)).pack()
                progressbar11.pack()
                progressbar11["maximum"] = 300
                progressbar11["value"] = 0

                for i in ["del /f /s /q %temp%","del /f /s /q %systemdrive%\*.log","del /f /s /q %systemdrive%\*.old","del /f /s /q %systemdrive%\*.tmp","del /f /s /q %systemdrive%\*.gid","taskkill /f /im explorer.exe&start explorer.exe"]:
                    command(i)
                    progressbar11['value'] += 50
                    window2.update()

                sleep(1)
                window2.destroy()

        def fix_windows(self=0):
            if msgbox.askyesno("提示","确定恢复Windows？"):
                command("start plugins\\fixWindows.lnk")

        def windows_key(self=0):
            if msgbox.askyesno("提示","确定激活windows？"):
                command("start plugins\\激活windows.lnk")

        def save_windows(self=0):
            if msgbox.askyesno("提示","确定开始简单杀毒?\n此工具不能代替任何杀毒软件，请勿当作杀毒软件使用！"):
                window3 = ttkbootstrap.Toplevel()
                window3.geometry("500x350")
                window3.title("easyUse v1.0")
                window3.iconbitmap("icon.ico")

                # void
                def del_all():
                    for i in warnList:
                        os.remove(path=path + "//" + i)

                progressbar21 = tkinter.ttk.Progressbar(window3, length=300)
                listbox21 = tkinter.Listbox(window3, width=30, height=8)
                tkinter.Label(window3, text="杀毒", font=("微软雅黑", 30)).pack()
                progressbar21.pack()
                listbox21.pack()
                ttkbootstrap.Button(window3,text="删除所有风险项目",bootstyle=(ttkbootstrap.constants.OUTLINE,ttkbootstrap.constants.LIGHT),command=del_all).pack()


                progressbar21["maximum"] = 300
                progressbar21["value"] = 0

                #things to do.
                virusList = ["Sasser.exe","wannacry.exe","滑稽病毒.exe","MEZE.exe"]
                warnTypeList = ["reg","bat","cmd","vbs","ps1"]
                warnList = []

                allFile1 = []
                allFile2 = []
                path = askdirectory(title="请选择要杀毒的目录")
                for i in range(150):
                    sleep(0.004)
                    progressbar21["value"] +=1
                    window3.update()

                listbox21.insert("end","可能带有危险：")

                for i in os.listdir(path=path):
                    allFile1.append(path+"//"+i)
                    allFile2.append(i)

                #cheack1
                for i in allFile2:
                    if i.split(".")[1] in warnTypeList:
                        listbox21.insert("end",i)
                        warnList.append(i)

                for i in range(75):
                    sleep(0.004)
                    progressbar21["value"] +=1
                    window3.update()

                sleep(0.5)
                #check2
                listbox21.insert("end", "已经删除：")

                for i in allFile2:
                    if i in virusList:
                        listbox21.insert("end",i)

                        idx = allFile2.index(i)
                        virusPath = allFile1[idx]

                        os.remove(virusPath)

                for i in range(75):
                    sleep(0.004)
                    progressbar21["value"] +=1
                    window3.update()

        def toast(self,caption,text):
            toaster = ToastNotifier()
            toaster.show_toast(
                title=caption,
                msg=text,
                icon_path="icon.ico",
                duration=10,
                threaded=True,
            )

    #set
    set = []

    with open("setting.txt") as f:
        a = f.readlines()
        for i in range(len(a)-1):
            set.append(a[i].split("\n")[0])
        set.append(a[len(a)-1])

    coin = float(set[1])
    coin += 0.5

    f = open("setting.txt", "w")
    f.write(set[0] + "\n")
    f.write(str(coin))

    f.close()

    #init
    window = ttkbootstrap.Window(themename=set[0],resizable=None)
    window.geometry("900x650")
    window.title("easyUse企业版 v1.2")
    window.iconbitmap("icon.ico")

    window.overrideredirect(1)

    #load v
    English_title = tkinter.Label(window, text="None", bg="grey", fg="white", font=("微软雅黑",20))

    button211_pic = tkinter.PhotoImage(file="pic\\button211_pic.png")
    button212_pic = tkinter.PhotoImage(file="pic\\button212_pic.png")
    button213_pic = tkinter.PhotoImage(file="pic\\button213_pic.png")
    button214_pic = tkinter.PhotoImage(file="pic\\button214_pic.png")
    button1_pic = tkinter.PhotoImage(file="pic\\button1.png")
    button2_pic = tkinter.PhotoImage(file="pic\\button2.png")
    button3_pic = tkinter.PhotoImage(file="pic\\button3.png")
    button4_pic = tkinter.PhotoImage(file="pic\\button4.png")

    label241 = ttkbootstrap.Label(window, text="这是一个由easyWorld公司写的程序，主要为国人使用。\n作者花了很大心思,\n如果想留言或反馈改进话请9练习作者163\n邮箱：18116231008@163.coj",bootstyle="DARK",font=("微软雅黑",15))

    button211 = tkinter.Button(window, text="", bg="black", fg="white", image=button211_pic, font=("微软雅黑", 40), command=function.clean_disk, bd=0)
    button212 = tkinter.Button(window, text="", bg="black", fg="white", image=button212_pic, font=("微软雅黑", 40), command=function.fix_windows, bd=0)
    button213 = tkinter.Button(window, text="", bg="black", fg="white", image=button213_pic, font=("微软雅黑", 40), command=function.windows_key, bd=0)
    button214 = tkinter.Button(window, text="", bg="black", fg="white", image=button214_pic, font=("微软雅黑", 40), command=function.save_windows, bd=0)

    isAboutRun = 0
    isSetupRun = 0
    isSeniorRun = 0
    isCommonRun = 0

    topicList = ['solar',"darkly","superhero","vapor","cyborg"]

    #set
    English_title.pack()

    English_title.place(x=400,y=90)

    #def
    def change_window(choice):
        #global
        global label241
        global label231
        global label221
        global button211
        global button212
        global button213
        global button214

        global isAboutRun
        global isSetupRun
        global isSeniorRun
        global isCommonRun

        global setWindow
        global combobox2311

        #choice
        if choice == "普通":
            English_title.config(text="common")
            #destroy
            label241.destroy()
            isAboutRun = 0

            isSetupRun = 0

            if isCommonRun == 1:
                button211.destroy()
                button212.destroy()
                button213.destroy()
                button214.destroy()
                isCommonRun = 0

            button211 = tkinter.Button(window, text="", bg="black", fg="white", image=button211_pic, font=("微软雅黑", 30),command=function.clean_disk,bd=0)
            button212 = tkinter.Button(window, text="", bg="black", fg="white", image=button212_pic, font=("微软雅黑", 40),command=function.fix_windows, bd=0)
            button213 = tkinter.Button(window, text="", bg="black", fg="white", image=button213_pic, font=("微软雅黑", 40),command=function.windows_key, bd=0)
            button214 = tkinter.Button(window, text="", bg="black", fg="white", image=button214_pic, font=("微软雅黑", 40),command=function.save_windows, bd=0)

            button211.pack()
            button212.pack()
            button213.pack()
            button214.pack()

            button211.place(x=20,y=130)
            button212.place(x=170,y=130)
            button213.place(x=320,y=130)
            button214.place(x=470,y=130)

            isCommonRun = 1

        elif choice == "体检":
            English_title.config(text="computer")

            computer_window = ttkbootstrap.Toplevel()
            computer_window.geometry("900x600")
            computer_window.title("easyUse v1.0")
            computer_window.iconbitmap("icon.ico")

            mem = psutil.virtual_memory()

            zj = float(mem.total) / 1024 / 1024 / 1024
            ysy = float(mem.used) / 1024 / 1024 / 1024

            label221 = tkinter.Label(computer_window,text="检查内存占用   已完成   "+str(ysy)+"GB",bg="grey",fg="white",font=("微软雅黑",16))
            label222 = tkinter.Label(computer_window,text="清理系统垃圾   已完成",bg="grey",fg="white",font=("微软雅黑",16))
            label223 = tkinter.Label(computer_window,text="刷新桌面图标   已完成",bg="grey",fg="white",font=("微软雅黑",16))

            if zj/2 >= ysy:
                amountused221 = random.randint(50,63)
            else:
                amountused221 = random.randint(64,100)

            #work
            meter221 = ttkbootstrap.Meter(
                computer_window,
                metersize=180,
                padding=5,
                amountused=amountused221,
                metertype="semi",
                subtext="电脑体检分数",
                interactive=True,
                bootstyle=ttkbootstrap.constants.SUCCESS
            )

            tkinter.Label(computer_window,text="电脑体检",bg="grey",fg="white",font=("微软雅黑",40)).pack()
            meter221.pack()

            meter221.place(x=20,y=100)

            label221.pack()
            label221.place(x=250,y=200)
            computer_window.update()

            sleep(1)

            function.clean_disk()

            label222.pack()
            label222.place(x=250,y=250)
            computer_window.update()

            sleep(1)

            command("taskkill /f /im explorer.exe&start explorer.exe")

            label223.pack()
            label223.place(x=250,y=300)
            computer_window.update()

            sleep(1)

        elif choice == "设置":
            English_title.config(text="settings")
            #destroy
            label241.destroy()
            isAboutRun = 0

            isSeniorRun = 0

            button212.destroy()
            button213.destroy()
            button214.destroy()
            isCommonRun = 0
            button211.destroy()

            if isSetupRun == 1:
                isSetupRun = 0

            isSetupRun = 1

            setWindow = ttkbootstrap.Toplevel()
            setWindow.geometry("600x400")
            setWindow.title("setup")
            setWindow.iconbitmap("icon.ico")
            setWindow.resizable(0, 0)

            label311 = tkinter.Label(setWindow,text="主题",bg="grey",fg="white",font=("微软雅黑",20))
            combobox2311 = ttkbootstrap.Combobox(setWindow,values=topicList)
            button211 = ttkbootstrap.Button(setWindow,text="完成",bootstyle=(ttkbootstrap.constants.LIGHT,ttkbootstrap.constants.OUTLINE),command=function.finishSetup)

            tkinter.Label(setWindow,text="设置",bg="grey",fg="white",font=("微软雅黑",30)).pack()
            label311.pack()
            combobox2311.pack()
            button211.pack()

            label311.place(x=420,y=70)
            combobox2311.place(x=370,y=120)
            button211.place(x=540,y=350)

        elif choice == "关于":
            English_title.config(text="about")
            #destroy
            isSetupRun = 0
            isSeniorRun = 0

            button211.destroy()
            button212.destroy()
            button213.destroy()
            button214.destroy()
            isCommonRun = 0

            if isAboutRun == 1:
                isAboutRun = 0

            label241 = ttkbootstrap.Label(window,text="这是一个由easyWorld公司写的程序，主要为国人使用。\n作者花了很大心思,\n如果想留言或反馈改进请联系作者163\n邮箱：18116231008@163.com",font=("微软雅黑",15))
            label241.pack()

            label241.place(x=30,y=150)
            msgbox.showinfo("关于软件", "EasyUse 专业版\n版本:v1.2\n作者:史喆元\n全名:EasyUse 1.2 beta")
            isAboutRun = 1

    class change():
        def change1(self=0):
            change_window("普通")

        def change2(self=0):
            change_window("体检")

        def change3(self=0):
            change_window("设置")

        def change4(self=0):
            change_window("关于")

    #pack
    tkinter.Label(window,text="欢迎使用EasyUse专业版!",bg="black",fg="white",font=("微软雅黑",30)).pack(ipady=10)
    Label2 = ttkbootstrap.Label(window,text="积分:" + str(coin),font=("微软雅黑",10))
    button1 = tkinter.Button(window, text="", image=button1_pic,bd=0,command=change.change1)
    button2 = tkinter.Button(window, text="", image=button2_pic,bd=0,command=change.change2)
    button3 = tkinter.Button(window, text="", image=button3_pic,bd=0,command=change.change3)
    button4 = tkinter.Button(window, text="", image=button4_pic,bd=0,command=change.change4)
    quit_button = ttkbootstrap.Button(window, text="X", bootstyle=ttkbootstrap.constants.DARK,command=sys.exit)

    Label2.pack()
    button1.pack()
    button3.pack()
    button2.pack()
    button4.pack()
    quit_button.pack()
    #place
    Label2.place(x=10,y=10)
    button1.place(x=750,y=40)
    button2.place(x=750,y=190)
    button3.place(x=750,y=340)
    button4.place(x=750,y=490)
    quit_button.place(x=870,y=0)

    #window drag
    def start_dragging(event):
        window.x = event.x
        window.y = event.y


    def stop_dragging(event):
        window.x = 0
        window.y = 0


    def do_dragging(event):
        deltax = event.x - window.x
        deltay = event.y - window.y
        new_x = window.winfo_x() + deltax
        new_y = window.winfo_y() + deltay
        window.geometry(f"+{new_x}+{new_y}")


    window.bind("<ButtonPress-1>", start_dragging)
    window.bind("<ButtonRelease-1>", stop_dragging)
    window.bind("<B1-Motion>", do_dragging)

    window.x = 0
    window.y = 0


    #mainloop
    window.mainloop()
```
