
# -*- coding:utf-8 -*-
__author__ = 'chengshaohua'

import os


path = "./" # 文件夹目录
outPath = "resultKVC.txt" # 输出结果文件
keyChar = "valueForKey:@\"_"
keyValue = "forKey:@\"_"
keyPath = "forKeyPath:@\"_"
datas = []  # 全局变量，存放找到的目标文件


def eachFile(filepath):
    if not os.path.exists(filepath): return
    
    fileNames = os.listdir(filepath)  # 获取当前路径下的文件名，返回List
    file_count = len(fileNames)
    if file_count == 0: return
    
    for index, file in enumerate(fileNames, 0):
        newDir = filepath + '/' + file # 将文件命加入到当前文件路径后面
        #        if newDir.startswith(('.//Pods')): continue
        
        if os.path.isfile(newDir):  # 如果是文件
            lastName = os.path.splitext(newDir)[1]
            if lastName == ".h" or lastName == ".m":  # 判断是否是oc文件
                f = open(newDir)
                count = 0
                for line in f.readlines():
                    count += 1
                    if len(line.strip()) < 1: continue
                    if line.find(keyChar) != -1 or line.find(keyValue) != -1 or line.find(keyPath) != -1:
                        content = '\n第'+str(count)+'行     ' + file + line  # 读文件
                        datas.append(content)
                else:
                    f.close()
        # if os.path.isdir(newDir): # 如果是文件夹
        else:
            eachFile(newDir)    #如果不是文件，递归这个文件夹的路径

def outFiles():
    file = open(outPath,'w')
    file.write("".join(datas));
    file.close()


if __name__ == "__main__":
    eachFile(path)
    outFiles()

