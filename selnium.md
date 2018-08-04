from selenium import webdriver
from selenium.webdriver.common.keys import Keys

# 目前支持的driver有Firefox, Chrome, IE和Remote等
driver = webdriver.Chrome(executable_path="D:\\3\\chromedriver")
# 直到页面被加载完（onload事件被触发）才将控制权返回脚本
driver.get('https://www.baidu.com')
assert u'百度一下，你就知道' in driver.title
print (u"当前URL：", driver.current_url)

driver.find_element_by_id('kw').send_keys('水')
#selenium 元素查找find_element_by_id方法，找到元素后输入信息
driver.find_element_by_id('su').click()
#selenium 元素查找find_element_by_id方法，找到元素后进行点击
