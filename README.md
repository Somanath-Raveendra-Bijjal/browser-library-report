# browser-library-report
*** Settings ***
Library    Browser

*** Test Cases ***
Verify Playwright Homepage
    New Page    https://playwright.dev/
    Get Title    contains    Playwright

Click Get Started
    New Page    https://playwright.dev/
    ${element}=    Get Element By Role    link    name=Get started
    Click    ${element}
    ${heading}=    Get Element By Role    heading    name=Installation
    Get Element States    ${heading}    contains    visible

Alternative Click Get Started
    New Page    https://playwright.dev/
    Click    text="Get started"
    Get Element States    h1 >> text="Installation"    contains    visible

Playwright Test Example
    New Page    https://playwright.dev/
    Get Title    matches    Playwright
    ${getStarted}=    Get Element By Text    Get started
    Get Attribute    ${getStarted}    href    ==    /docs/intro
    Click    ${getStarted}
    Get Url    matches    .*intro