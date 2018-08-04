import random   #随机
import datetime    #日期
import time


dataCount = 1000  # 数据量
codeRange = range(ord('a'), ord('z'))   #代码的范围
alphaRange = [chr(x) for x in codeRange]
alphaMax = len(alphaRange)
daysMax = 42003           #出生日期的范围，1900-01-01往后推42003天
theDay = datetime.date(1900, 1, 1)


def genRandomName(nameLength):       #生成长度随机英文
    global alphaRange, alphaMax
    length = random.randint(1, nameLength)
    name = ''
    for i in range(length):
        name += alphaRange[random.randint(0, alphaMax - 1)]
    return name
print(genRandomName(10))

def genRandomDay():           #生成出生日期
    global daysMax, theDay
    mDays = random.randint(0, daysMax)
    mDate = theDay + datetime.timedelta(days=mDays)
    return mDate.isoformat()
print(genRandomDay())

def genRandomSex():           #随机生成几到几之间的数字
    return str(random.randint(1, 3))
print(genRandomSex())

def genRandomSex1():           #征信查询原因，01或02
    return '0'+str(random.randint(1, 2))
print(genRandomSex1())
#
# def genDataBase1(fileName, dataCount):
#     outp = open('D:\\软件学习\\gb.txt', 'w')
#     i = 0
#     while i < dataCount:
#         firstName = genRandomName(14)
#         lastName = genRandomName(14)
#         birthday = genRandomDay()
#         sex = genRandomSex()
#         mLine = "%i,%s,%s,%s,%d\n" % (i + 1, firstName, lastName, birthday, sex)  #输出数据顺序
#         outp.write(mLine)
#         i += 1
#     outp.close()
#
#
# if __name__ == "__main__":
#     random.seed()
#     start = time.time()
#     genDataBase1('db_test.txt', dataCount)
#     end = time.time()
#     print('use time:%d' % (end - start))
#     print('Ok')

# import random         #生成1~10的随机数1000个
# fp = open('D:\\软件学习\\gb.txt', 'w')
# for i in range(1, 1000):
#     a = random.randint(1,10)
#     fp.write(str(a)+"\n")
# fp.close()



def createPhone():    # 随机生成手机号码
    prelist=["130","131","132","133","134","135","136","137","138","139","147","150","151","152","153","155","156","157","158","159","186","187","188"]
    return random.choice(prelist)+"".join(random.choice("0123456789") for i in range(8))
print(createPhone())


def getdistrictcode():     # 随机生成身份证号
    with open('D:\\软件学习\\districtcode.txt') as file:
        data = file.read()
        districtlist = data.split('\n')
    for node in districtlist:
    #print node
        if node[10:11] != ' ':
            state = node[10:].strip()
        if node[10:11]==' 'and node[12:13]!=' ':
            city = node[12:].strip()
        if node[10:11] == ' 'and node[12:13]==' ':
            district = node[14:].strip()
            code = node[0:6]
            codelist.append({"state":state,"city":city,"district":district,"code":code})

def gennerator():
    global codelist
    codelist = []
    if not codelist:
        getdistrictcode()
    id = codelist[random.randint(0,len(codelist))]['code'] #地区项
    id = id + str(random.randint(1930,2013)) #年份项
    da = theDay+datetime.timedelta(days=random.randint(1,366)) #月份和日期项
    id = id + da.strftime('%m%d')
    id = id+ str(random.randint(100,300))#，顺序号简单处理

    i = 0
    count = 0
    weight = [7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2] #权重项
    checkcode ={'0':'1','1':'0','2':'X','3':'9','4':'8','5':'7','6':'6','7':'5','8':'5','9':'3','10':'2'} #校验码映射
    for i in range(0,len(id)):
        count = count +int(id[i])*weight[i]
        id = id + checkcode[str(count%11)] #算出校验码
        return id

print (gennerator())

#构造从1000个用户，用户名不相同的
x=1
f=open('D:\\软件学习\\gb.txt',"w")      #先打开txt记事本
while x <1001:         #用户数
    f.write("liushuihao"+'%d'%x+',HQ'+',小王,'+genRandomSex()+','+gennerator()+','+genRandomSex1()+','+'模型名称'+','+genRandomName(10)+','+createPhone()+',kehubianhao'+'%d'%x+'\n')     #  +‘\n’实现内容的换行
    x=x+1
f.close()    #关闭记事本
