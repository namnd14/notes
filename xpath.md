// -> relative xpath, search for all children element
/ -> absolute xpath, search for direct child element only
* Stands for all element
//*[@class=‘abc’]
//*[@id=‘xyz’]
//*[@data-testid=‘abc’]
//*[text()=‘text’]
//*[contains(@class, ‘class-name’)]
combine example
//*[@class='myclass' and contains(text(),'qwerty')]