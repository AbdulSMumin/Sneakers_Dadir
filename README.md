# Sneakers_Dadir
# Nike US Bot

import time
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.action_chains import ActionChains

# Go to page
driver = webdriver.Chrome()  # Optional argument, if not specified will search path.
driver.get('https://www.nike.com/gb/launch/t/air-max-95-dna-aurora-green');
driver.maximize_window()
time.sleep(0.2) # Let the user actually see something!

# Dismiss Cookie
dismiss_cookie = WebDriverWait(driver, 20).until(EC.element_to_be_clickable((By.XPATH, "//*[@id='root']/div/div/div[1]/div/div[2]/div/div/div/div[2]/button"))).click()
time.sleep(0.2)

# Select Size and add to bag
select_size = driver.find_element_by_xpath("//button[text()='UK 7.5']")
driver.execute_script("arguments[0].scrollIntoView()", select_size)
time.sleep(0.5)
select_size.click()

# Buy
buy = driver.find_element_by_xpath("//button[text()='Buy ']")
ActionChains(driver).send_keys(Keys.PAGE_DOWN).perform()
driver.execute_script("arguments[0].scrollIntoView()", buy)
time.sleep(0.5)
buy.click()

# Sign In
email_nike = driver.find_element_by_xpath("//form[@id='nike-unite-loginForm']//input[@name='emailAddress']")
email_nike.send_keys('a.s.mumin@hotmail.co.uk')
pass_nike = driver.find_element_by_xpath("//form[@id='nike-unite-loginForm']//input[@name='password']")
pass_nike.send_keys('Allahuakbar10')
nike_next = WebDriverWait(driver, 20).until(EC.element_to_be_clickable((By.XPATH, "//form[@id='nike-unite-loginForm']//input[@value='SIGN IN']"))).click()
time.sleep(0.2)

# Payment
payment = driver.find_element_by_xpath("//input[@id='cvNumber']")
payment.send_keys('471')
time.sleep(0.1)
save_and_continue = WebDriverWait(driver, 20).until(EC.element_to_be_clickable((By.XPATH, "//div[@id='checkout-sections']/div[2]/div/span/span[1]/div/button[@type='button']")))
save_and_continue.click()
submit_order = WebDriverWait(driver, 20).until(EC.element_to_be_clickable((By.XPATH, "//button[text()='Submit Order']")))
#submit_order.click()

