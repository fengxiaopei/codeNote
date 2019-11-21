## python连接本地的数据库

#导入pymysql模块
import pymysql
import pandas as pd
#连接database
conn = pymysql.connect(host="localhost", user="root", password="666666", database="logstat", charset="utf8")
#得到一个可以执行sql语句的光标对象
cursor = conn.cursor()
sql = """
select stuno,title from new_log_stulearns where oper=76 and courseid=5 and tlen>0;
"""
cursor.execute(sql) # 执行sql语句
#ret = cursor.fetchone() # 获取单条查询数据
#ret = cursor.fetchmany(10) # 获取多条条查询数据
ret = cursor.fetchall() # 获取多条查询数据
cursor.close() #关闭光标
conn.close() #关闭数据库
#print(ret) #打印下查询结果，为tuple（元祖）
df = pd.DataFrame(list(ret), columns=['stuno', 'core'])
