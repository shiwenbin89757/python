import requests# --->requests，urllib2(pip install xxx)
import json# ---> data = {'name': 'tom', 'age'：23}, json.dumps(data) -->'{'name':'tom','age'：23}'叫序列化, 可持久。json.loads(data) -->反序列化
import unittest# --->python专有的单元测试库，也叫单元测试框架
from APItest import data
from APItest import readExcel
from HTMLTestRunner import HTMLTestRunner# --->生成测试报告的库
token = []

class TestApi(unittest.TestCase):
    def setUp(self):
        self.us = data.user[0]
        self.pw = data.pwd[0]

    def test_login001(self):
        '''这是一个正常登录接口'''
        data = readExcel.ReadExcel().readExcel(1)
        print(data)
        data0 = eval(data[6])
        result = requests.post(url=data[4], data=data0)
        res = result.text
        result1 = json.loads(res)
        self.assertEqual(result1['success'], bool(data[7]))
        return (result1['data'])

    def tearDown(self):
        pass


class TestA(unittest.TestCase):
    def test_selectAll(self):
        '''这是一个全量查询的接口'''
        d1 = {'token': token[0], 'page': '1', 'size': '10'}
        u1 = 'http://192.168.3.20:8080/kap/kapdataall'
        result = requests.get(url=u1, params=d1)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestB(unittest.TestCase):
    def test_sc(self):
        '''这是一个删除接口'''
        d2 = {'token': token[0], 'solrid': '6b2942592a4b3eae60c969d4d3d3233b'}
        u2 = 'http://192.168.3.20:8080/kap/kapdatadeldata'
        result = requests.post(url=u2, data=d2)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'], False)
        return (result.text)

    def tearDown(self):
        pass


class TestC(unittest.TestCase):
    def test_ybcx(self):
        '''这是样本查询'''
        d3 = {'token': token[0], 'solrid': 'cd783bf307e152866d1980abb69ce8e0','page':'1','size':'10'}
        u3 = 'http://192.168.3.20:8080/kap/kapdatasamplerecomend'
        result = requests.post(url=u3, data=d3)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'],True)
        return (result.text)

    def tearDown(self):
        pass


class TestD(unittest.TestCase):
    def test_xqycx(self):
        '''这是详情页数据'''
        d4 = {'token': token[0], 'solrid': 'cd783bf307e152866d1980abb69ce8e0'}
        u4 = 'http://192.168.3.20:8080/kap/kapdatadetails'
        result = requests.post(url=u4, data=d4)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'],True)
        return (result.text)

    def tearDown(self):
        pass

class TestE(unittest.TestCase):
    def text_xcx(self):
        '''相似查询推荐文章'''
        d5 = {'token': token[0], 'level': 'theta2', 'language': 'chinese', 'page': '1', 'size': '10'}
        u5 = 'http://192.168.3.20:8080/kap/kapdatatheta'
        result = requests.post(url=u5,data=d5)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'], True)
        return (result.text)
    def test_xscstj(self):
        '''相似查询推荐文章'''
        d5 = {'token': token[0], 'level': 'theta164','language':'chinese','page':'1','size':'10'}
        u5 = 'http://192.168.3.20:8080/kap/kapdatatheta'
        result = requests.post(url=u5, data=d5)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'],True)
        return (result.text)

    def tearDown(self):
        pass

class TestF(unittest.TestCase):
    def test_ss(self):
        '''搜索'''
        d6 = {'token':token[0],'selectkey':'keyword','keyword':'演化算法 最多叶子生成树问题 近似性能 运行时间分析','page':'1','size':'10'}
        u6 = 'http://192.168.3.20:8080/kap/kapdatasearch'
        result = requests.post(url=u6,data=d6)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestG(unittest.TestCase):
    def test_tj(self):
        '''8.	根据用户使用进行推荐'''
        d7 = {'token':token[0]}
        u7 = 'http://192.168.3.20:8080/kap/kapdatarecommend'
        result = requests.post(url=u7,data=d7)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestH(unittest.TestCase):
    def test_tj(self):
        '''8.	根据用户使用进行推荐'''
        d7 = {'token':token[0]}
        u7 = 'http://192.168.3.20:8080/kap/kapdatarecommend'
        result = requests.post(url=u7,data=d7)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)
    def test_dh(self):
        '''9.	根据文章id查询文章导航信息'''
        d8 = {'token':token[0],'solrid':'cd783bf307e152866d1980abb69ce8e0'}
        u8 = 'http://192.168.3.20:8080/kap/kapdataalltopic'
        result = requests.post(url=u8,data=d8)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestI(unittest.TestCase):
    def test_gjzfc(self):
        '''10.	查询关键字分词结构'''
        d9 = {'token':token[0],'words':' [{source: "双向搜索",target: "更新策略",weight: 235}]'}
        u9 = 'http://192.168.3.20:8080/kap/kapdataforceechart'
        result = requests.post(url=u9,data=d9)
        result1 = json.loads(result.text)
        print(result1)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestJ(unittest.TestCase):
    def test_xz(self):
        '''11.	附件下载'''
        d10 = {'token':token[0],'solrid':'cd783bf307e152866d1980abb69ce8e0'}
        u10 = 'http://192.168.3.20:8080/kap/kapdatafiledownload'
        result = requests.post(url=u10,data=d10)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], False)
        return (result.text)

    def tearDown(self):
        pass

class TestK(unittest.TestCase):
    def test_tjzdyfc(self):
        '''13.	添加自定义分词'''
        d13 = {'token':token[0],'keyword':'试'}
        u13 = 'http://192.168.3.20:8080/kap/kapdatawordadd'
        result = requests.post(url=u13,data=d13)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], False)
        return (result.text)
    def test_bjzdyfc(self):
        '''15.	编辑自定义分词'''
        d13 = {'token':token[0],'wordid':'1','newword':'bone'}
        u13 = 'http://192.168.3.20:8080/kap/kapdatawordedit'
        result = requests.post(url=u13,data=d13)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], False)
        return (result.text)
    def test_cxzdyfc(self):
        '''16.	查询自定义分词'''
        d = {'token':token[0],'page':'1','size':'10'}
        u = 'http://192.168.3.20:8080/kap/kapdataword'
        result = requests.post(url=u,data=d)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

class TestL(unittest.TestCase):
    def test_cxyhxx(self):
        '''17.	用户管理,查询所有用户信息'''
        d = {'token':token[0],'page':'1','size':'10'}
        u = 'http://192.168.3.20:8080/kap/kapdataalluser'
        result = requests.post(url=u,data=d)
        result1 = json.loads(result.text)
        self.assertEqual(result1['success'], True)
        return (result.text)

    def tearDown(self):
        pass

def allTest():
    '''创建测试集'''
    suite1 = unittest.TestLoader().loadTestsFromTestCase(TestApi)
    suite2 = unittest.TestLoader().loadTestsFromTestCase(TestA)
    suite3 = unittest.TestLoader().loadTestsFromTestCase(TestB)
    suite4 = unittest.TestLoader().loadTestsFromTestCase(TestC)
    suite5 = unittest.TestLoader().loadTestsFromTestCase(TestD)
    suite6 = unittest.TestLoader().loadTestsFromTestCase(TestE)
    suite7 = unittest.TestLoader().loadTestsFromTestCase(TestF)
    suite8 = unittest.TestLoader().loadTestsFromTestCase(TestH)
    suite9 = unittest.TestLoader().loadTestsFromTestCase(TestI)
    suite10 = unittest.TestLoader().loadTestsFromTestCase(TestJ)
    suite11 = unittest.TestLoader().loadTestsFromTestCase(TestK)
    suite12 = unittest.TestLoader().loadTestsFromTestCase(TestL)
    alltests = unittest.TestSuite([suite1, suite2,suite3,suite4, suite5,suite6,suite7, suite8,suite9,suite10,suite11,suite12])
    print(suite3)
    return alltests
allTest()



if __name__ == '__main__':
    '''创建保存测试结果的文件'''
    filename = "D:\\软件学习\\result1.html"
    fp = open(filename, 'wb')
    runner = HTMLTestRunner(stream=fp, title="Test Report", description="执行的测试用例")
    runner.run(allTest())
    fp.close()
    # suite = unittest.TestSuite() #测试用例套件
    # suite.addTest(TApi('login'))
    # suite.addTest(TApi('selectAll'))
    # # 3、实例化runner类
    # runner = unittest.TextTestRunner()
    # runner.run(suite)

    # filename = "E:\\项目\\python_api\\ApaTest\\result.html"
    #
    # fp = open(filename,'wb')
    #
    # runner = HTMLTestRunner.HTMLTestRunner(stream=fp,title=u'测试报告',description=u'用例执行情况')
    # runner.run(suite)
    # import time
    # now = time.strftime("%Y-%m-%M-%H_%M_%S", time.localtime(time.time()))
    # fp = open("E:/项目/python_api/ApaTest"+"result" + now + ".html", 'wb')
    # runner = HTMLTestRunner.HTMLTestRunner(stream=fp, title='test result', description=u'result:')
    # runner.run(suite)
    # fp.close()

    # suite = unittest.TestLoader().loadTestsFromTestCase(TestApi)  # 定义一个单元测试容器
    # filename = "xxx.html"  # 定义个报告存放路径，支持相对路径
    # f = open(filename, 'wb')  # 结果写入HTML 文件
    # runner = HTMLTestRunner.HTMLTestRunner(stream=f, title='Report_title', description='Report_description',
    #                                        verbosity=2)  # 使用HTMLTestRunner配置参数，输出报告路径、报告标题、描述
    # result = runner.run(suite)
    # result.success_count  # 运行成功的数目
    # result.testsRun  # 运行测试用例的总数
    # result.failure_count  # 运行失败的数目
