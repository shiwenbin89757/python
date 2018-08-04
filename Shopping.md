# -*- coding: utf-8 -*-
dict_1 = {} #接收注册进来的用户数据{'张三':{'password':'123456','account_balance':0.00}}
dict_2 = {} #空购物车,{'手机':{'荣耀8':['￥1699','64G','魅海蓝'],'iPhone':['￥4390','32G','黑']}}
dict1 = {'手机':{'荣耀8':{'￥':'1699','内存':'64g','颜色':'魅海蓝'},'iPhone':{'￥':'4390','内存':'64g','颜色':'魅海蓝'}},'相机':{'尼康':{'￥':'1699','内存':'64g','颜色':'魅海蓝'},'罗马仕':{'￥':'4390','内存':'64g','颜色':'魅海蓝'}}}
dict2 = {'上衣':{'adidas':{'￥':'169','尺寸':'M','颜色':'魅海蓝'},'playboy':{'￥':'230','尺寸':'M','颜色':'魅海蓝'}},'裤子':{'senma':{'￥':'199','尺寸':'M','颜色':'魅海蓝'},'baleno':{'￥':'100','尺寸':'M','颜色':'魅海蓝'}}}
dict3 = {'洗衣机':{'Haier':{'￥':'1699','重量':'4t','颜色':'魅海蓝'},'LG':{'￥':'4390','重量':'4t','颜色':'魅海蓝'}},'电视':{'Midea':{'￥':'1699','尺寸':'24','颜色':'魅海蓝'},'Panasonic':{'￥':'4390','尺寸':'40','颜色':'魅海蓝'}}}
dict4 = {'小吃':{'辣条':{'￥':'5','含量':'64g','颜色':'魅海蓝'},'鸭脖':{'￥':'20','含量':'50g','颜色':'魅海蓝'}},'坚果':{'开心果':{'￥':'50','含量':'100g','颜色':'魅海蓝'},'夏威夷果':{'￥':'30','含量':'80g','颜色':'魅海蓝'}}}
dict5 = {'小说':{'盗墓笔记':{'￥':'46','页码':'200','颜色':'魅海蓝'},'鬼吹灯':{'￥':'38','页码':'150','颜色':'魅海蓝'}},'工具书':{'新华字典':{'￥':'30','页码':'500','颜色':'魅海蓝'},'英语单词本':{'￥':'10','页码':'100','颜色':'魅海蓝'}}}
f = open('D:\\软件学习\\gb.txt')
print('\033[1;32;48m') #改变字体，背景颜色
print('欢迎来到文斌商城注册登录界面'.center(100,'-'))
#print('\n')
print('1: 注册'.center(80,' '))
#print('\n')
print('2: 登录'.center(80,' '))
#print('\n')
print('0: 关闭'.center(80,' '))
num = input('请输入你选择的数字:')
if int(num) == 0:
    exit()
elif int(num) == 1:
    username1 = input('请输入用户名:')
    password1 = input('请输入密码:')
    dict_1[username1] = {'password1': password1, 'account_balance1': 0.00}  # 把输入的用户名1和密码账户余额添加到字典中
    print('注册成功，请注册第二个账号')
    username2 = input('请输入用户名:')
    password2 = input('请输入密码:')
    dict_1[username2] = {'password2': password2, 'account_balance2': 0.00}  # 把输入的用户名2和密码账户余额添加到字典中
    print(dict_1)
    if len(dict_1) == 2:
        print('注册成功')
        user1 = input('请输入登录的用户名:')                               # 第一次登陆
        if username1 == user1:
            print('用户名验证通过')
            pwd1 = input('请输入登录的密码:')
            if dict_1[user1]['password1'] == pwd1:
                print('密码验证通过')
                print('欢迎来到文斌商城注册登录界面'.center(100,'-'))
                print('1: 电子类'.center(80, ' '))
                # print('\n')
                print('2: 服装类'.center(80, ' '))
                # print('\n')
                print('3: 家具类'.center(80, ' '))
                # print('\n')
                print('4: 食品类'.center(80, ' '))
                # print('\n')
                print('5: 图书类'.center(80, ' '))
                # print('\n')
                print('0: 退出'.center(80, ' '))
                nums = input('请输入你要浏览的品类编号:')
                if int(nums) == 1:
                    print('欢迎浏览电子类产品'.center(100, '*'))
                    print('1: 手机')
                    print('荣耀8' + ':' + "['￥1699','64G','魅海蓝']")
                    print('iPhone' + ':' + "['￥4390','32G','黑']")
                    print('2: 相机')
                    print('尼康' + ':' + "['￥1699','64G','魅海蓝']")
                    print('罗马仕' + ':' + "['￥4390','32G','黑']")
                    nums_1 = input('请输入你要浏览的产品名：')
                    if nums_1 in dict1:
                        print(dict1[nums_1])
                        nums_01 = input('请添加具体商品到购物车，并购买：')
                        if nums_01 in dict1[nums_1]:
                            dict_2 = dict1.get(nums_01)  # 把商品全部信息加入购物车
                            with open('D:\\软件学习\\gb.txt', 'w') as f:
                                f.write(str(nums_01))  # 把商品加入购物车
                            print('商品已成功添加到购物车，请支付')
                            a = float(dict1[nums_1][nums_01]['￥'])     #商品价格
                            b = float(dict_1[username1]['account_balance1'])     #账户余额
                            while True:
                                print('___商品价格:%.2f'%a)
                                print('___账户余额:%.2f'%b)
                                if b >= a:  # 判断账户里是否有足够的钱
                                    b = b - a  # 支付后剩余的钱
                                    print('%s商品支付成功' % nums_01)
                                    print('商品参数：{nums_01}'.format(nums_01=dict1[nums_1][nums_01]))
                                    print('余额：%.2f'%b)
                                    exit()
                                else:
                                    print('账户余额不足，请充值')
                                    bank1 = input('请输入银行卡号：')  # 充值
                                    pwd1 = input('请输入密码：')
                                    dict_1[username1] = {'bank1': bank1, 'pwd1': pwd1}  # 把输入的银行卡1和密码添加到字典中
                                    money_1 = float(input('请输入充值金额：'))
                                    if (money_1) > 0:
                                        b = b + (money_1)  # 充值后账户里的钱
                                        print('充值%.2f成功' % money_1)
                                        print('充值后账户余额%.2f' %b)
                                    else:
                                        print('充值金额有误，请重新输入')
                        else:
                            print('你输入的商品不存在，请重新输入')
                elif int(nums) == 2:
                    print('欢迎浏览服装类产品'.center(100, '*'))
                    print('1:上衣 ')
                    print('adidas' + ':' + "['￥':'169','尺寸':'M','颜色':'魅海蓝']")
                    print('playboy' + ':' + "['￥':'230','尺寸':'M','颜色':'魅海蓝']")
                    print('2:裤子 ')
                    print('senma' + ':' + "['￥':'199','尺寸':'M','颜色':'魅海蓝']")
                    print('baleno' + ':' + "['￥':'100','尺寸':'M','颜色':'魅海蓝']")
                    nums_1 = input('请输入你要浏览的产品名')
                    if nums_1 in dict2:
                        print(dict2[nums_1])
                        nums_01 = input('请添加具体商品到购物车，并购买：')
                        if nums_01 in dict2[nums_1]:
                            dict_2 = dict2.get(nums_01)  # 把商品全部信息加入购物车
                            with open('D:\\软件学习\\gb.txt', 'w') as f:
                                f.write(str(nums_01))  # 把商品加入购物车
                            print('商品已成功添加到购物车，请支付')
                            a = float(dict2[nums_1][nums_01]['￥'])     #商品价格
                            b = float(dict_1[username1]['account_balance1'])     #账户余额
                            while True:
                                print('___商品价格:%.2f'%a)
                                print('___账户余额:%.2f'%b)
                                if b >= a:  # 判断账户里是否有足够的钱
                                    b = b - a  # 支付后剩余的钱
                                    print('%s商品支付成功' % nums_01)
                                    print('商品参数：{nums_01}'.format(nums_01=dict2[nums_1][nums_01]))
                                    print('余额：%.2f'%b)
                                    exit()
                                else:
                                    print('账户余额不足，请充值')
                                    bank1 = input('请输入银行卡号：')  # 充值
                                    pwd1 = input('请输入密码：')
                                    dict_1[username1] = {'bank1': bank1, 'pwd1': pwd1}  # 把输入的银行卡1和密码添加到字典中
                                    money_1 = float(input('请输入充值金额：'))
                                    if (money_1) > 0:
                                        b = b + (money_1)  # 充值后账户里的钱
                                        print('充值%.2f成功' % money_1)
                                        print('充值后账户余额%.2f' %b)
                                    else:
                                        print('充值金额有误，请重新输入')
                        else:
                            print('你输入的商品不存在，请重新输入')
                elif int(nums) == 3:
                    print('欢迎浏览服装类产品'.center(100, '*'))
                    print('1:洗衣机 ')
                    print('Haier' + ':' + "['￥':'1699','重量':'4t','颜色':'魅海蓝']")
                    print('LG' + ':' + "['￥':'4390','重量':'4t','颜色':'魅海蓝']")
                    print('2:电视 ')
                    print('Midea' + ':' + "['￥':'1699','尺寸':'24','颜色':'魅海蓝']")
                    print('Panasonic' + ':' + "['￥':'4390','尺寸':'40','颜色':'魅海蓝']")
                    nums_1 = input('请输入你要浏览的产品名')
                    if nums_1 in dict3:
                        print(dict3[nums_1])
                        nums_01 = input('请添加具体商品到购物车，并购买：')
                        if nums_01 in dict3[nums_1]:
                            dict_2 = dict3.get(nums_01)  # 把商品全部信息加入购物车
                            with open('D:\\软件学习\\gb.txt', 'w') as f:
                                f.write(str(nums_01))  # 把商品加入购物车
                            print('商品已成功添加到购物车，请支付')
                            a = float(dict3[nums_1][nums_01]['￥'])     #商品价格
                            b = float(dict_1[username1]['account_balance1'])     #账户余额
                            while True:
                                print('___商品价格:%.2f'%a)
                                print('___账户余额:%.2f'%b)
                                if b >= a:  # 判断账户里是否有足够的钱
                                    b = b - a  # 支付后剩余的钱
                                    print('%s商品支付成功' % nums_01)
                                    print('商品参数：{nums_01}'.format(nums_01=dict3[nums_1][nums_01]))
                                    print('余额：%.2f'%b)
                                    exit()
                                else:
                                    print('账户余额不足，请充值')
                                    bank1 = input('请输入银行卡号：')  # 充值
                                    pwd1 = input('请输入密码：')
                                    dict_1[username1] = {'bank1': bank1, 'pwd1': pwd1}  # 把输入的银行卡1和密码添加到字典中
                                    money_1 = float(input('请输入充值金额：'))
                                    if (money_1) > 0:
                                        b = b + (money_1)  # 充值后账户里的钱
                                        print('充值%.2f成功' % money_1)
                                        print('充值后账户余额%.2f' %b)
                                    else:
                                        print('充值金额有误，请重新输入')
                        else:
                            print('你输入的商品不存在，请重新输入')
                elif int(nums) == 4:
                    print('欢迎浏览服装类产品'.center(100, '*'))
                    print('1:小吃 ')
                    print('辣条' + ':' + "['￥':'5','含量':'64g','颜色':'魅海蓝']")
                    print('鸭脖' + ':' + "['￥':'20','含量':'50g','颜色':'魅海蓝']")
                    print('2:坚果 ')
                    print('开心果' + ':' + "['￥':'50','含量':'100g','颜色':'魅海蓝']")
                    print('夏威夷果' + ':' + "['￥':'30','含量':'80g','颜色':'魅海蓝']")
                    nums_1 = input('请输入你要浏览的产品名')
                    if nums_1 in dict4:
                        print(dict4[nums_1])
                        nums_01 = input('请添加具体商品到购物车，并购买：')
                        if nums_01 in dict4[nums_1]:
                            dict_2 = dict4.get(nums_01)  # 把商品全部信息加入购物车
                            with open('D:\\软件学习\\gb.txt', 'w') as f:
                                f.write(str(nums_01))  # 把商品加入购物车
                            print('商品已成功添加到购物车，请支付')
                            a = float(dict4[nums_1][nums_01]['￥'])     #商品价格
                            b = float(dict_1[username1]['account_balance1'])     #账户余额
                            while True:
                                print('___商品价格:%.2f'%a)
                                print('___账户余额:%.2f'%b)
                                if b >= a:  # 判断账户里是否有足够的钱
                                    b = b - a  # 支付后剩余的钱
                                    print('%s商品支付成功' % nums_01)
                                    print('商品参数：{nums_01}'.format(nums_01=dict4[nums_1][nums_01]))
                                    print('余额：%.2f'%b)
                                    exit()
                                else:
                                    print('账户余额不足，请充值')
                                    bank1 = input('请输入银行卡号：')  # 充值
                                    pwd1 = input('请输入密码：')
                                    dict_1[username1] = {'bank1': bank1, 'pwd1': pwd1}  # 把输入的银行卡1和密码添加到字典中
                                    money_1 = float(input('请输入充值金额：'))
                                    if (money_1) > 0:
                                        b = b + (money_1)  # 充值后账户里的钱
                                        print('充值%.2f成功' % money_1)
                                        print('充值后账户余额%.2f' %b)
                                    else:
                                        print('充值金额有误，请重新输入')
                        else:
                            print('你输入的商品不存在，请重新输入')
                elif int(nums) == 5:
                    print('欢迎浏览服装类产品'.center(100, '*'))
                    print('1:小说 ')
                    print('盗墓笔记' + ':' + "['￥':'46','页码':'200','颜色':'魅海蓝']")
                    print('鬼吹灯' + ':' + "['￥':'38','页码':'150','颜色':'魅海蓝']")
                    print('2:工具书 ')
                    print('新华字典' + ':' + "['￥':'30','页码':'500','颜色':'魅海蓝']")
                    print('英语单词本' + ':' + "['￥':'10','页码':'100','颜色':'魅海蓝']")
                    nums_1 = input('请输入你要浏览的产品名')
                    if nums_1 in dict5:
                        print(dict5[nums_1])
                        nums_01 = input('请添加具体商品到购物车，并购买：')
                        if nums_01 in dict5[nums_1]:
                            dict_2 = dict5.get(nums_01)  # 把商品全部信息加入购物车
                            with open('D:\\软件学习\\gb.txt', 'w') as f:
                                f.write(str(nums_01))  # 把商品加入购物车
                            print('商品已成功添加到购物车，请支付')
                            a = float(dict5[nums_1][nums_01]['￥'])     #商品价格
                            b = float(dict_1[username1]['account_balance1'])     #账户余额
                            while True:
                                print('___商品价格:%.2f'%a)
                                print('___账户余额:%.2f'%b)
                                if b >= a:  # 判断账户里是否有足够的钱
                                    b = b - a  # 支付后剩余的钱
                                    print('%s商品支付成功' % nums_01)
                                    print('商品参数：{nums_01}'.format(nums_01=dict5[nums_1][nums_01]))
                                    print('余额：%.2f'%b)
                                    exit()
                                else:
                                    print('账户余额不足，请充值')
                                    bank1 = input('请输入银行卡号：')  # 充值
                                    pwd1 = input('请输入密码：')
                                    dict_1[username1] = {'bank1': bank1, 'pwd1': pwd1}  # 把输入的银行卡1和密码添加到字典中
                                    money_1 = float(input('请输入充值金额：'))
                                    if (money_1) > 0:
                                        b = b + (money_1)  # 充值后账户里的钱
                                        print('充值%.2f成功' % money_1)
                                        print('充值后账户余额%.2f' %b)
                                    else:
                                        print('充值金额有误，请重新输入')
                        else:
                            print('你输入的商品不存在，请重新输入')

            else:
                print('密码错误')
        else:
            print('用户名不存在，请注册')
        # 第二次登录同上
    else:
        print('注册失败')
elif int(num) == 2:
    username = input('请输入你的用户名:')

# list=['1','2','3','4','5','0']
# dict1={'diannao':{'dell':{'price':3000,'coller':'red','number':10}},'shouji':{'lenovo':{'price':3500,'coller':'black','number':20}},'pinban':{'Thinkpad':{'price':4000,'coller':'black','number':30}},'dianshi':{'HP':{'price':2500,'coller':'black','number':30}},'zhuji':{'ASUS':{'price':3500,'coller':'black','number':25}}}
# dict2={'shangyi':{'adidas':{'price':200,'coller':'black','number':40}},'kuzhi':{'playboy':{'price':200,'coller':'black','number':200}},'weijing':{'senma':{'price':50,'coller':'black','number':80}},'waitao':{'baleno':{'price':100,'coller':'black','number':150}},'chenyi':{'mut':{'price':3000,'coller':'green','number':100}}}
# dict3={'xiyiji':{'Haier':{'price':3500,'coller':'white','number':20}},'dianshi':{'LG':{'price':3000,'coller':'black','number':40}},'kongtiao':{'Midea':{'price':4000,'coller':'black','number':40}},'binxiang':{'Panasonic':{'price':4500,'coller':'black','number':40}},'youyangji':{'WEILI':{'price':3000,'coller':'red','number':10}}}
# dict4={'qixie':{'yaling':{'price':110,'coller':'black','number':60}},'jiangshengfu':{'adidas':{'price':200,'coller':'red','number':300}},'jiangshengshuji':{'jiroutujie':{'price':20,'coller':'red','number':500}},'jiqi':{'跑步机':{'price':2000,'coller':'black','number':10}},'jiangshengsipin':{'guwumiaobao':{'price':10,'coller':'red','number':1000}}}
# dict5={'jiake':{'longxia':{'price':800,'coller':'red','number':50}},'haiyu':{'pantouyu':{'price':20,'coller':'white','number':100}},'shenghaiyu':{'manyu':{'price':30,'coller':'yellow','number':100}},'ruangu':{'bazuayu':{'price':15,'coller':'white','number':100}},'xia':{'daxia':{'price':25,'coller':'white','number':100}}}
# print('欢迎你来到文斌的网上商城'.center(50,'*'))
# print('1.电子类'.center(48,' '))
# print('2.服装类'.center(48,' '))
# print('3.家具类'.center(48,' '))
# print('4.健身类'.center(48,' '))
# print('5.海鲜类'.center(48,' '))
# print('0.退出'.center(46,' '))
# leixin = raw_input('请选择你要浏览的产品系列')
# if list[0] == leixin:
#     print dict1
# elif list[1] == leixin:
#     print dict2
# elif list[2] == leixin:
#     print dict3
# elif list[3] == leixin:
#     print dict4
# elif list[4] == leixin:
#     print dict5
# elif list[5] == leixin:
#     print('退出')
# elif leixin not in list:
#     print('返回上一层')
# list1=[]
# dict1.update(dict2)
# dict1.update(dict3)
# dict1.update(dict4)
# dict1.update(dict5)
# for k1 in dict1:
#     print(k1)             #电脑，手机等
#     list1.append(k1)          #将全部商品集合到一个list1
# print('分割线1'.center(50,'_'))
# while True:
#     carts = raw_input('请输入产品名称')
#     if carts in list1:
#         with open('C:\\Users\\asus\\Desktop\\gb.txt','w') as f:
#             f.write(str(carts))                       # 把商品加入购物车
#         m = dict1[carts]
#         dict_2.update(m)                  # 把商品全部信息加入购物车
#         print('商品已成功添加到购物车')
#         if carts not in dict_2.keys():
#             if money >= dict1[carts][price]:
#                 money = money - dict1[carts][price]  # 支付成功
#                 print('{carts}商品支付成功'.format(carts = dict1[carts]))
#             else:
#                 print('账户余额不足，请充值')
#                 bank = raw_input('请输入银行卡号：')  # 充值
#                 pwd = raw_input('请输入密码：')
#                 money_a = raw_input('请输入充值金额：')
#                 if money > 0:
#                     money = money + money_a
#                     print('充值成功')
#                 else:
#                     print('充值金额有误，请重新输入')
#         else:
#             print('购物车已添加该商品,不需重复添加')
#     else:
#         print('你输入的商品不存在，请重新输入')