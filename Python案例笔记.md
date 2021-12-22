# Python案例笔记

- ### 学生管理系统

  1. #### 内置模块

  ```python
  import re			#正则表达式，检索需要的东西
  import os			#系统接口模块
  
  re.sub(pattern, repl, string, count)
  第一个参数就是 正则表达式，要替换的东西
  第二个参数就是 要替换成什么的参数
  第三个参数就是 要替换的整个字符串
  第四个参数就是 要替换的个数或者次数
  text='Hello,monkey!'
  re.sub(r'\s+', '-', text) 
  把 <text> 中的 ‘空格’ 替换成‘-’
  
  os.path.exists(filename) #判断系统中是否有存在此文件
  
  ```

  2. #### 主函数

  ```python
  def main():
    函数名（）			#执行一个功能的函数
    函数名（）			#执行第二个功能函数
  if __name__=='__main__':		#函数都会有一个属性
    main()										#执行主函数
  ```

  3. #### try...except...

  ```python
  try:										#处理异常的一个函数
    pass
  except N as n:					#会指定一个错误		
    pass
  ```

  4. #### 写文件

  ```python
  with open('文件名',’写入方式‘) as f:
    f.write()
  #写入方式
  w:写入
  r:只读
  a:追加
  
  
  例：
  
  studentList=[]
  
  studen={
      'id':1,
      'name':'monkey'
  }
  
  studentList.append(studen)
  
  with open('1.txt','w') as f:
      f.write(str(studentList))			#直接写入就是列表模式
      for info in studentList:
        f.write(str(info))					#挨个写入就是字典模式，字典要比列表好取数据。
  ```

  5. #### 文件存储

  ```python
  .save('文件夹名'+‘/’+'文件名'+'后缀’)  #后缀是文件要保存的形式
  Mac 文件路径是：‘/’
  Windows 文件路径是：‘\\’ #必须要带转义字符
  ```

  6. ###### 

