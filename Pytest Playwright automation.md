**1 Install**



pip install pytest playwright

playwright install



**2 Create new file as test\_ui.py**



from playwright.sync\_api import sync\_playwright





def test\_basic\_actions():

&#x20;   with sync\_playwright() as p:

&#x20;       browser = p.chromium.launch(headless=False)

&#x20;       page = browser.new\_page()



&#x20;       # Open website

&#x20;       page.goto("https://rahulshettyacademy.com/AutomationPractice/")



&#x20;       # Select Radio Button

&#x20;       page.check("input\[value='radio1']")



&#x20;       # Select Checkbox

&#x20;       page.check("#checkBoxOption1")



&#x20;       # Select Dropdown

&#x20;       page.select\_option("#dropdown-class-example", "option2")



&#x20;       # Simple validation

&#x20;       assert page.is\_checked("input\[value='radio1']")



&#x20;       browser.close()



**3 Run**



pytest -v

