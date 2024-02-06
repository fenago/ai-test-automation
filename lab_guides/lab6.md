
How to Use ChatGPT for Automation 
----------------------------------

The code-writing capabilities of ChatGPT are well-documented, with
countless examples of everything from simple plugins to entire websites
built by the chatbot. But, while ChatGPT still requires hand-holding
when writing code, it\'s exceptional at building test cases, writing
test scripts, and helping developers embrace testing best practices. 

### Creating Test Cases 

Suppose that you\'re responsible for creating a test plan. With a simple
prompt and a few bullet points, ChatGPT can create an in-depth test plan
consisting of setup instructions and multiple test cases. You can even
instruct ChatGPT to prepare a test case table to enter into Jira
tickets, which results in a copy-and-pastable table!

### Writing Test Scripts 

Suppose you want to write a unit test for an existing code. By copying
the code snippet into ChatGPT, you can ask for a unit test for the code,
and it will create a test based on the inferred context. You can insert
these tests into a test automation process (e.g., your CI/CD processes)
and prevent future regressions. 

### Explaining Test Results 

If you run the test script generated in the previous section and receive
an error, you can copy and paste it into ChatGPT, and it will create an
explanation. Additionally, the conversational format of ChatGPT means
you can also ask follow-up questions. These same capabilities can help
developers fix bugs. 

### Creating Test Summaries 

Suppose you have a list of test results and want to summarize the
results for a team lead or stakeholder. You can ask ChatGPT to summarize
the results in a narrative format for a particular audience (e.g.,
technical or non-technical). Or, you can request that ChatGPT put the
results into a table that may form part of a more extensive report. 



Examples in Action 
-------------------

Let\'s start by generating a BDD scenario using Cucumber and a
domain-specific language (DSL) called Gherkin. These specifications are
machine and human-readable to improve communication between testers,
developers, and non-technical business people. 

We can start with the prompt: \"Generate a test case using Cucumber for
Google Search.\" 

Note: You could replace \"Google Search\" with a description of your
feature or functionality. 

        
        Feature: Google Search Engine 

        Scenario: User performs a successful search 

        As a user who wants to find information quickly 

        I want to search using Google's search engine 

        So that I can find relevant results easily 

        Given I am on the Google homepage 

        When I enter a "cucumber testing" query into the search bar 

        And I click the "Search" button 

        Then I should see search results related to "cucumber testing" 

        And the first result should have a title containing "Cucumber" 

        And the first result should have a URL containing "cucumber.io"
        

Next, we can generate specific test steps using the prompt: \"Implement
these steps using Cucumber\'s step definitions.\" 

Note: These step definitions are written in Ruby using the Capybara
library, but you can specify any language or framework you want. 


```
    
require 'capybara/cucumber' 

Given("I am on the Google homepage") do 

    visit("https://www.google.com") 

end 

When("I enter a {string} query into the search bar") do |search_term| 

    fill_in("q", with: search_term) 

end 

And("I click the {string} button") do |button_name| 

    click_button(button_name) 

end 

Then("I should see search results related to {string}") do |search_term| 

    expect(page).to have_content(search_term) 

end 

And("the first result should have a title containing {string}") do |title_substring| 

    first_result_title = find(".g:first-child .LC20lb.DKV0Md").text 

expect(first_result_title).to include(title_substring) 

end 

And("the first result should have a URL containing {string}") do |url_substring| 

    first_result_url = find(".g:first-child .yuRUbf a")[:href] 

    expect(first_result_url).to include(url_substring) 

end 
    
```



Python




And voila, you have an executable BDD specification that you can use to
ensure an application performs as expected.

You can also use ChatGPT to create unit tests. For example, if you
wanted to test a mobile calculator app\'s addition and subtraction
functions using Appium, specify the prompt: \"Write an Appium test for a
mobile calculator app with an addition and subtraction button.\" 


```
        
import unittest 

from appium import webdriver 

from appium.webdriver.common.mobileby import MobileBy 

class CalculatorAppTest(unittest.TestCase): 

    def setUp(self): 

        desired_capabilities = { 

            "platformName": "Android", 

            "deviceName": "Android Emulator", 

            "app": "/path/to/your/calculator.apk", 

            "automationName": "UiAutomator2" 

        } 

        self.driver = webdriver.Remote("http://127.0.0.1:4723/wd/hub", desired_capabilities) 

    def tearDown(self): 

        self.driver.quit() 

    def test_addition(self): 

        number1 = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "number1") 

        number2 = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "number2") 

        number1.send_keys("5") 

        number2.send_keys("3") 

        add_button = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "addButton") 

        add_button.click() 

        result = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "result") 

        self.assertEqual(result.text, "8") 

    def test_subtraction(self): 

        number1 = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "number1") 

        number2 = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "number2") 

        number1.send_keys("7") 

        number2.send_keys("4") 

        subtract_button = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "subtractButton") 

        subtract_button.click() 

        result = self.driver.find_element(MobileBy.ACCESSIBILITY_ID, "result") 

        self.assertEqual(result.text, "3") 

if __name__ == "__main__": 

    unittest.main() 
         
```



Python




These tests are relatively accurate and ready to execute virtually
as-is. While you may need to engineer prompts to get the best results or
modify the results to suit your project better, ChatGPT is sufficient to
get your tests 90% of the way there. As a result, senior engineers can
save time, and junior engineers can simplify their job.
