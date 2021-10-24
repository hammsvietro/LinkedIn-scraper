from selenium import webdriver;
import bs4
from selenium.webdriver.chrome.options import Options;
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

def set_up():
     chrome_options = Options()
     chrome_options.add_argument('--headless')
     return webdriver.Chrome(chrome_options=chrome_options);

def wait_elem(browser, by, entity):
     WebDriverWait(browser, 30).until(EC.presence_of_element_located((by, entity)))

browser = set_up();

browser.get('https://www.linkedin.com/');
wait_elem(browser, By.ID, 'session_key');

browser.maximize_window()
browser.find_element_by_id('session_key').send_keys('Username Here!!!');
browser.find_element_by_id('session_password').send_keys('Password Here!!!')
browser.find_element_by_class_name('sign-in-form__submit-button').click();

browser.get('https://www.linkedin.com/jobs/collections/recommended')

wait_elem(browser, By.CLASS_NAME, 'jobs-search-results-list')

html = browser.page_source;

soup = bs4.BeautifulSoup(html, 'html.parser');

for vaga in soup.select('li'):
     vagaTitulo = vaga.select_one('a');
     print(vagaTitulo)
