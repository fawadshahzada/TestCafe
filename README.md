<p align="center">
  <a href="https://testcafe.io/403442/resources/blog/2021-10-7-dashboard-alpha-invitation-announce?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-banner">
    <img src="https://raw.github.com/DevExpress/testcafe/master/media/tda-banner.png" alt="Join TestCafe Dashboard “Alpha Test” Program" />
  </a>
</p>

<p align="center">
    <a href="https://testcafe.io">
        <img src="https://raw.githubusercontent.com/DevExpress/testcafe/master/media/testcafe-logo.svg?sanitize=true" alt="testcafe" />
    </a>
</p>

<p align="center">
<a href="https://github.com/DevExpress/testcafe/commits/master"><img alt="Tests" src="https://img.shields.io/github/checks-status/DevExpress/testcafe/master?label=Tests"></a>
<a href="https://github.com/DevExpress/testcafe/actions/workflows/test-dependencies.yml"><img alt="Test Dependencies" src="https://github.com/DevExpress/testcafe/actions/workflows/test-dependencies.yml/badge.svg" /></a>
<a href="https://www.npmjs.com/package/testcafe"><img alt="NPM Version" src="https://img.shields.io/npm/v/testcafe.svg" data-canonical-src="https://img.shields.io/npm/v/testcafe.svg" style="max-width:100%;"></a>
</p>

<p align="center">
<i>A Node.js tool to automate end-to-end web testing.<br/>Write tests in JS or TypeScript, run them and view results.</i>
</p>

<p align="center">
  <a href="https://testcafe.io">Homepage</a> &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://testcafe.io/documentation/402635/getting-started">Documentation</a> &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://testcafe.io/402636/faq">FAQ</a> &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://testcafe.io/support">Support</a>
</p>

* **Works on all popular environments**: TestCafe runs on Windows, MacOS, and Linux. It supports desktop, mobile, remote and cloud [browsers](https://testcafe.io/documentation/402828/guides/concepts/browsers#browser-support) (UI or headless).
* **1 minute to set up**: You [do not need WebDriver](https://testcafe.io/402636/faq#i-have-heard-that-testcafe-does-not-use-selenium-how-does-it-operate) or any other testing software. Install TestCafe with one command, and you are ready to test: `npm install -g testcafe`
* **Free and open source**: TestCafe is free to use under the [MIT license](https://github.com/DevExpress/testcafe/blob/master/LICENSE). [Plugins](#plugins) provide custom reports, integration with other tools, launching tests from IDE, etc. You can use the plugins made by the GitHub community or make your own.

![Install TestCafe and Run a Test](https://raw.githubusercontent.com/DevExpress/testcafe/master/media/install-and-run-test.gif)

<p align="center">
<i>Running a sample test in Safari</i>
</p>

## Table of contents

* [Features](#features)
* [TestCafe Studio: IDE for End-to-End Web Testing](#testcafe-studio-ide-for-end-to-end-web-testing)
* [Getting Started](#getting-started)
* [Documentation](#documentation)
* [Get Help](#get-help)
* [Issue Tracker](#issue-tracker)
* [Stay in Touch](#stay-in-touch)
* [Contributing](#contributing)
* [Plugins](#plugins)
* [Different Versions of TestCafe](#different-versions-of-testcafe)
* [Badge](#badge)
* [License](#license)
* [Creators](#creators)

## Features

**Stable tests and no manual timeouts**<br/>
TestCafe automatically waits for page loads and XHRs before the test starts and after each action.
It also features smart test actions and assertions that wait for page elements to appear.
You can change the maximum wait time.
If elements load faster, tests skip the timeout and continue.

**Rapid test development tool**<br/>
Changes in test code immediately restart the test, and you see the results instantly.<br/>
See how it works in the [TestCafe Live repository](https://github.com/DevExpress/testcafe-live).

**Latest JS and TypeScript support**<br/>
TestCafe supports the latest JavaScript features, including ES2017 (for example, async/await).
You can also [use TypeScript](https://testcafe.io/documentation/402824/guides/concepts/typescript-and-coffeescript#typescript-support)
if you prefer a strongly typed language.

**Detects JS errors in your code**<br/>
TestCafe reports JS errors that it finds on the webpage.
Tests automatically fail because of that.
However, you can disable this.

**Concurrent test launch**<br/>
TestCafe can open multiple instances of the same browser to run parallel
tests which decreases test execution time.

**PageObject pattern support**<br/>
The TestCafe's [Test API](https://testcafe.io/documentation/402632/reference)
includes a high-level selector library, assertions, etc.
You can combine them to implement readable tests with the [PageObject pattern](https://testcafe.io/documentation/402826/guides/concepts/page-model).

```js
const macOSInput = Selector('.column').find('label').withText('MacOS').child('input');
```

**Easy to include in a continuous integration system**<br/>
You can run TestCafe from a console, and its reports can be viewed in a CI system's interface
(TeamCity, Jenkins, Travis & etc.)

## TestCafe Studio: IDE for End-to-End Web Testing

TestCafe works great for JavaScript developers, but at some point you will need to delegate testing tasks to your Q&A department. If that's the case and you are looking for a codeless way to record and maintain tests compatible with your existing infrastructure, check out [TestCafe Studio](https://www.devexpress.com/products/testcafestudio/?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-ide) - a testing IDE built on top of the open-source TestCafe.

Read the following article to learn how TestCafe Studio could fit into your workflow: [What's Better than TestCafe? TestCafe Studio](https://www.devexpress.com/products/testcafestudio/qa-end-to-end-web-testing.xml).

![Get Started with TestCafe Studio](https://raw.githubusercontent.com/DevExpress/testcafe/master/media/testcafe-studio-get-started.gif)

<p align="center">
<i>Record and Run a Test in TestCafe Studio</i>
</p>

## Getting Started

### Installation

Ensure that [Node.js](https://nodejs.org/) ([Current or Active LTS](https://github.com/nodejs/Release#release-phases) is recommended, version 12 at minimum) and [npm](https://www.npmjs.com/) are installed on your computer before running it:

```sh
npm install -g testcafe
```

### Creating the Test

As an example, we are going to test the [https://devexpress.github.io/testcafe/example](https://devexpress.github.io/testcafe/example) page.

Create a `.js` or `.ts` file on your computer.
Note that it needs to have a specific structure: tests must be organized into fixtures.
You can paste the following code to see the test in action:

```js
import { Selector } from 'testcafe'; // first import testcafe selectors

fixture `Getting Started`// declare the fixture
    .page `https://devexpress.github.io/testcafe/example`;  // specify the start page


//then create a test and place your code there
test('My first test', async t => {
    await t
        .typeText('#developer-name', 'John Smith')
        .click('#submit-button')

        // Use the assertion to check if the actual header text is equal to the expected one
        .expect(Selector('#article-header').innerText).eql('Thank you, John Smith!');
});
```

### Running the Test

Call the following command in a command shell.
Specify the [target browser](https://testcafe.io/documentation/402639/reference/command-line-interface#browser-list)
and [file path](https://testcafe.io/documentation/402639/reference/command-line-interface#file-pathglob-pattern).

```sh
testcafe chrome test1.js
```

TestCafe opens the browser and starts executing the test.

> Important! Make sure the browser tab that runs tests stays active.
> Do not minimize the browser window. Inactive tabs and minimized browser windows switch
> to a lower resource consumption mode where tests are not guaranteed to execute correctly.

### Viewing the Results

TestCafe outputs the results into a command shell by default. See [Reporters](https://testcafe.io/documentation/402825/guides/concepts/reporters)
for more information. You can also use [plugins](#plugins) to customize the reports.

![Test Report](https://testcafe.io/images/report.png)

Read the [Getting Started](https://testcafe.io/documentation/402635/getting-started) page for a more detailed guide.

## Documentation

Go to our website for full [documentation](https://testcafe.io/documentation/402635/getting-started) on TestCafe.

## Get Help

Join the TestCafe community on Stack Overflow to get help. Ask and answer [questions with the TestCafe tag](https://stackoverflow.com/questions/tagged/testcafe).

## Issue Tracker

Use our GitHub issues page to [report bugs](https://github.com/DevExpress/testcafe/issues/new?template=bug-report.md) and [suggest improvements](https://github.com/DevExpress/testcafe/issues/new?template=feature_request.md).

## Stay in Touch

Follow us on [Twitter](https://twitter.com/DXTestCafe). We post TestCafe news and updates, several times a week.

## Contributing

Read our [Contributing Guide](https://github.com/DevExpress/testcafe/blob/master/CONTRIBUTING.md) to learn how to contribute to the project.

To create your own plugin for TestCafe, you can use these plugin generators:

* [Build a browser provider](https://testcafe.io/documentation/402812/guides/extend-testcafe/browser-provider-plugin)
  to set up tests on your on-premises server farm, to use a cloud testing platform, or to start your local browsers in a special way. Use this [Yeoman generator](https://www.npmjs.com/package/generator-testcafe-browser-provider) to write only a few lines of code.
* To [build a custom reporter](https://testcafe.io/documentation/402810/guides/extend-testcafe/reporter-plugin)
  with your formatting and style, check out this [generator](https://www.npmjs.com/package/generator-testcafe-reporter).

If you want your plugin to be listed below, [send us a note in a Github issue](https://github.com/DevExpress/testcafe/issues/new).

Thank you to all the people who already contributed to TestCafe!

[<img alt="aha-oretama" src="https://avatars.githubusercontent.com/u/7259161?v=4&s=117" width="117">](https://github.com/aha-oretama) |[<img alt="ai" src="https://avatars.githubusercontent.com/u/19343?v=4&s=117" width="117">](https://github.com/ai) |[<img alt="aleks-pro" src="https://avatars.githubusercontent.com/u/14822473?v=4&s=117" width="117">](https://github.com/aleks-pro) |[<img alt="Aleksey28" src="https://avatars.githubusercontent.com/u/32869530?v=4&s=117" width="117">](https://github.com/Aleksey28) |[<img alt="AlexanderMoiseev" src="https://avatars.githubusercontent.com/u/1498953?v=4&s=117" width="117">](https://github.com/AlexanderMoiseev) |[<img alt="AlexanderMoskovkin" src="https://avatars.githubusercontent.com/u/12047804?v=4&s=117" width="117">](https://github.com/AlexanderMoskovkin) |
:---: |:---: |:---: |:---: |:---: |:---: |
[aha-oretama](https://github.com/aha-oretama) |[ai](https://github.com/ai) |[aleks-pro](https://github.com/aleks-pro) |[Aleksey28](https://github.com/Aleksey28) |[AlexanderMoiseev](https://github.com/AlexanderMoiseev) |[AlexanderMoskovkin](https://github.com/AlexanderMoskovkin) |

[<img alt="alexey-lin" src="https://avatars.githubusercontent.com/u/13483856?v=4&s=117" width="117">](https://github.com/alexey-lin) |[<img alt="AlexKamaev" src="https://avatars.githubusercontent.com/u/1678902?v=4&s=117" width="117">](https://github.com/AlexKamaev) |[<img alt="AlexSkorkin" src="https://avatars.githubusercontent.com/u/995726?v=4&s=117" width="117">](https://github.com/AlexSkorkin) |[<img alt="alexwybraniec" src="https://avatars.githubusercontent.com/u/521536?v=4&s=117" width="117">](https://github.com/alexwybraniec) |[<img alt="andrewbranch" src="https://avatars.githubusercontent.com/u/3277153?v=4&s=117" width="117">](https://github.com/andrewbranch) |[<img alt="AndreyBelym" src="https://avatars.githubusercontent.com/u/4479386?v=4&s=117" width="117">](https://github.com/AndreyBelym) |
:---: |:---: |:---: |:---: |:---: |:---: |
[alexey-lin](https://github.com/alexey-lin) |[AlexKamaev](https://github.com/AlexKamaev) |[AlexSkorkin](https://github.com/AlexSkorkin) |[alexwybraniec](https://github.com/alexwybraniec) |[andrewbranch](https://github.com/andrewbranch) |[AndreyBelym](https://github.com/AndreyBelym) |

[<img alt="AndyWendt" src="https://avatars.githubusercontent.com/u/6130713?v=4&s=117" width="117">](https://github.com/AndyWendt) |[<img alt="AnnaKondratova" src="https://avatars.githubusercontent.com/u/27012218?v=4&s=117" width="117">](https://github.com/AnnaKondratova) |[<img alt="anthophobiac" src="https://avatars.githubusercontent.com/u/16448031?v=4&s=117" width="117">](https://github.com/anthophobiac) |[<img alt="arubtsov" src="https://avatars.githubusercontent.com/u/10169557?v=4&s=117" width="117">](https://github.com/arubtsov) |[<img alt="augustomezencio-hotmart" src="https://avatars.githubusercontent.com/u/25016353?v=4&s=117" width="117">](https://github.com/augustomezencio-hotmart) |[<img alt="bdwain" src="https://avatars.githubusercontent.com/u/3982094?v=4&s=117" width="117">](https://github.com/bdwain) |
:---: |:---: |:---: |:---: |:---: |:---: |
[AndyWendt](https://github.com/AndyWendt) |[AnnaKondratova](https://github.com/AnnaKondratova) |[anthophobiac](https://github.com/anthophobiac) |[arubtsov](https://github.com/arubtsov) |[augustomezencio-hotmart](https://github.com/augustomezencio-hotmart) |[bdwain](https://github.com/bdwain) |

[<img alt="benmonro" src="https://avatars.githubusercontent.com/u/399236?v=4&s=117" width="117">](https://github.com/benmonro) |[<img alt="beyondcompute" src="https://avatars.githubusercontent.com/u/248055?v=4&s=117" width="117">](https://github.com/beyondcompute) |[<img alt="bill-looby-i" src="https://avatars.githubusercontent.com/u/51128939?v=4&s=117" width="117">](https://github.com/bill-looby-i) |[<img alt="bsmithb2" src="https://avatars.githubusercontent.com/u/1773789?v=4&s=117" width="117">](https://github.com/bsmithb2) |[<img alt="caseyWebb" src="https://avatars.githubusercontent.com/u/5419074?v=4&s=117" width="117">](https://github.com/caseyWebb) |[<img alt="cdrini" src="https://avatars.githubusercontent.com/u/6251786?v=4&s=117" width="117">](https://github.com/cdrini) |
:---: |:---: |:---: |:---: |:---: |:---: |
[benmonro](https://github.com/benmonro) |[beyondcompute](https://github.com/beyondcompute) |[bill-looby-i](https://github.com/bill-looby-i) |[bsmithb2](https://github.com/bsmithb2) |[caseyWebb](https://github.com/caseyWebb) |[cdrini](https://github.com/cdrini) |

[<img alt="cgfarmer4" src="https://avatars.githubusercontent.com/u/336449?v=4&s=117" width="117">](https://github.com/cgfarmer4) |[<img alt="Chris-Greaves" src="https://avatars.githubusercontent.com/u/28542943?v=4&s=117" width="117">](https://github.com/Chris-Greaves) |[<img alt="churkin" src="https://avatars.githubusercontent.com/u/5182202?v=4&s=117" width="117">](https://github.com/churkin) |[<img alt="dej611" src="https://avatars.githubusercontent.com/u/924948?v=4&s=117" width="117">](https://github.com/dej611) |[<img alt="DIRECTcut" src="https://avatars.githubusercontent.com/u/49588154?v=4&s=117" width="117">](https://github.com/DIRECTcut) |[<img alt="Dmitry-Ostashev" src="https://avatars.githubusercontent.com/u/24777868?v=4&s=117" width="117">](https://github.com/Dmitry-Ostashev) |
:---: |:---: |:---: |:---: |:---: |:---: |
[cgfarmer4](https://github.com/cgfarmer4) |[Chris-Greaves](https://github.com/Chris-Greaves) |[churkin](https://github.com/churkin) |[dej611](https://github.com/dej611) |[DIRECTcut](https://github.com/DIRECTcut) |[Dmitry-Ostashev](https://github.com/Dmitry-Ostashev) |

[<img alt="eignatyev" src="https://avatars.githubusercontent.com/u/12494773?v=4&s=117" width="117">](https://github.com/eignatyev) |[<img alt="ericyd" src="https://avatars.githubusercontent.com/u/8379268?v=4&s=117" width="117">](https://github.com/ericyd) |[<img alt="Farfurix" src="https://avatars.githubusercontent.com/u/30019338?v=4&s=117" width="117">](https://github.com/Farfurix) |[<img alt="flora8984461" src="https://avatars.githubusercontent.com/u/39588094?v=4&s=117" width="117">](https://github.com/flora8984461) |[<img alt="GeoffreyBooth" src="https://avatars.githubusercontent.com/u/456802?v=4&s=117" width="117">](https://github.com/GeoffreyBooth) |[<img alt="helen-dikareva" src="https://avatars.githubusercontent.com/u/12034551?v=4&s=117" width="117">](https://github.com/helen-dikareva) |
:---: |:---: |:---: |:---: |:---: |:---: |
[eignatyev](https://github.com/eignatyev) |[ericyd](https://github.com/ericyd) |[Farfurix](https://github.com/Farfurix) |[flora8984461](https://github.com/flora8984461) |[GeoffreyBooth](https://github.com/GeoffreyBooth) |[helen-dikareva](https://github.com/helen-dikareva) |

[<img alt="honsq90" src="https://avatars.githubusercontent.com/u/1791439?v=4&s=117" width="117">](https://github.com/honsq90) |[<img alt="infctr" src="https://avatars.githubusercontent.com/u/15550153?v=4&s=117" width="117">](https://github.com/infctr) |[<img alt="inikulin" src="https://avatars.githubusercontent.com/u/453071?v=4&s=117" width="117">](https://github.com/inikulin) |[<img alt="Ivan-Katovich" src="https://avatars.githubusercontent.com/u/7858279?v=4&s=117" width="117">](https://github.com/Ivan-Katovich) |[<img alt="jamesgeorge007" src="https://avatars.githubusercontent.com/u/25279263?v=4&s=117" width="117">](https://github.com/jamesgeorge007) |[<img alt="jaypea" src="https://avatars.githubusercontent.com/u/367199?v=4&s=117" width="117">](https://github.com/jaypea) |
:---: |:---: |:---: |:---: |:---: |:---: |
[honsq90](https://github.com/honsq90) |[infctr](https://github.com/infctr) |[inikulin](https://github.com/inikulin) |[Ivan-Katovich](https://github.com/Ivan-Katovich) |[jamesgeorge007](https://github.com/jamesgeorge007) |[jaypea](https://github.com/jaypea) |

[<img alt="kanhaiya15" src="https://avatars.githubusercontent.com/u/38152453?v=4&s=117" width="117">](https://github.com/kanhaiya15) |[<img alt="kirovboris" src="https://avatars.githubusercontent.com/u/3633477?v=4&s=117" width="117">](https://github.com/kirovboris) |[<img alt="kisrefod" src="https://avatars.githubusercontent.com/u/27427579?v=4&s=117" width="117">](https://github.com/kisrefod) |[<img alt="kubejm" src="https://avatars.githubusercontent.com/u/8680565?v=4&s=117" width="117">](https://github.com/kubejm) |[<img alt="LavrovArtem" src="https://avatars.githubusercontent.com/u/5373460?v=4&s=117" width="117">](https://github.com/LavrovArtem) |[<img alt="link89" src="https://avatars.githubusercontent.com/u/3314130?v=4&s=117" width="117">](https://github.com/link89) |
:---: |:---: |:---: |:---: |:---: |:---: |
[kanhaiya15](https://github.com/kanhaiya15) |[kirovboris](https://github.com/kirovboris) |[kisrefod](https://github.com/kisrefod) |[kubejm](https://github.com/kubejm) |[LavrovArtem](https://github.com/LavrovArtem) |[link89](https://github.com/link89) |

[<img alt="lzxb" src="https://avatars.githubusercontent.com/u/8424643?v=4&s=117" width="117">](https://github.com/lzxb) |[<img alt="macdonaldr93" src="https://avatars.githubusercontent.com/u/5184848?v=4&s=117" width="117">](https://github.com/macdonaldr93) |[<img alt="MargaritaLoseva" src="https://avatars.githubusercontent.com/u/12034505?v=4&s=117" width="117">](https://github.com/MargaritaLoseva) |[<img alt="Marketionist" src="https://avatars.githubusercontent.com/u/534603?v=4&s=117" width="117">](https://github.com/Marketionist) |[<img alt="MatthewNielsen27" src="https://avatars.githubusercontent.com/u/35040439?v=4&s=117" width="117">](https://github.com/MatthewNielsen27) |[<img alt="mattmanske" src="https://avatars.githubusercontent.com/u/2078566?v=4&s=117" width="117">](https://github.com/mattmanske) |
:---: |:---: |:---: |:---: |:---: |:---: |
[lzxb](https://github.com/lzxb) |[macdonaldr93](https://github.com/macdonaldr93) |[MargaritaLoseva](https://github.com/MargaritaLoseva) |[Marketionist](https://github.com/Marketionist) |[MatthewNielsen27](https://github.com/MatthewNielsen27) |[mattmanske](https://github.com/mattmanske) |

[<img alt="mcjim" src="https://avatars.githubusercontent.com/u/485440?v=4&s=117" width="117">](https://github.com/mcjim) |[<img alt="miherlosev" src="https://avatars.githubusercontent.com/u/4133518?v=4&s=117" width="117">](https://github.com/miherlosev) |[<img alt="morfey13" src="https://avatars.githubusercontent.com/u/2048346?v=4&s=117" width="117">](https://github.com/morfey13) |[<img alt="mostlyfabulous" src="https://avatars.githubusercontent.com/u/15062048?v=4&s=117" width="117">](https://github.com/mostlyfabulous) |[<img alt="murajun1978" src="https://avatars.githubusercontent.com/u/911903?v=4&s=117" width="117">](https://github.com/murajun1978) |[<img alt="NickCis" src="https://avatars.githubusercontent.com/u/174561?v=4&s=117" width="117">](https://github.com/NickCis) |
:---: |:---: |:---: |:---: |:---: |:---: |
[mcjim](https://github.com/mcjim) |[miherlosev](https://github.com/miherlosev) |[morfey13](https://github.com/morfey13) |[mostlyfabulous](https://github.com/mostlyfabulous) |[murajun1978](https://github.com/murajun1978) |[NickCis](https://github.com/NickCis) |

[<img alt="Nuarat" src="https://avatars.githubusercontent.com/u/11683678?v=4&s=117" width="117">](https://github.com/Nuarat) |[<img alt="Ogurecher" src="https://avatars.githubusercontent.com/u/28919867?v=4&s=117" width="117">](https://github.com/Ogurecher) |[<img alt="pietrovich" src="https://avatars.githubusercontent.com/u/1728613?v=4&s=117" width="117">](https://github.com/pietrovich) |[<img alt="radarhere" src="https://avatars.githubusercontent.com/u/3112309?v=4&s=117" width="117">](https://github.com/radarhere) |[<img alt="raspo" src="https://avatars.githubusercontent.com/u/927264?v=4&s=117" width="117">](https://github.com/raspo) |[<img alt="rbardini" src="https://avatars.githubusercontent.com/u/874370?v=4&s=117" width="117">](https://github.com/rbardini) |
:---: |:---: |:---: |:---: |:---: |:---: |
[Nuarat](https://github.com/Nuarat) |[Ogurecher](https://github.com/Ogurecher) |[pietrovich](https://github.com/pietrovich) |[radarhere](https://github.com/radarhere) |[raspo](https://github.com/raspo) |[rbardini](https://github.com/rbardini) |

[<img alt="renancouto" src="https://avatars.githubusercontent.com/u/230893?v=4&s=117" width="117">](https://github.com/renancouto) |[<img alt="rob4629" src="https://avatars.githubusercontent.com/u/37812673?v=4&s=117" width="117">](https://github.com/rob4629) |[<img alt="rueyaa332266" src="https://avatars.githubusercontent.com/u/8298718?v=4&s=117" width="117">](https://github.com/rueyaa332266) |[<img alt="sgrillon14" src="https://avatars.githubusercontent.com/u/5530550?v=4&s=117" width="117">](https://github.com/sgrillon14) |[<img alt="smockle" src="https://avatars.githubusercontent.com/u/3104489?v=4&s=117" width="117">](https://github.com/smockle) |[<img alt="stefanschenk" src="https://avatars.githubusercontent.com/u/12391671?v=4&s=117" width="117">](https://github.com/stefanschenk) |
:---: |:---: |:---: |:---: |:---: |:---: |
[renancouto](https://github.com/renancouto) |[rob4629](https://github.com/rob4629) |[rueyaa332266](https://github.com/rueyaa332266) |[sgrillon14](https://github.com/sgrillon14) |[smockle](https://github.com/smockle) |[stefanschenk](https://github.com/stefanschenk) |

[<img alt="superroma" src="https://avatars.githubusercontent.com/u/8553464?v=4&s=117" width="117">](https://github.com/superroma) |[<img alt="sylbru" src="https://avatars.githubusercontent.com/u/3757523?v=4&s=117" width="117">](https://github.com/sylbru) |[<img alt="taiki-fw" src="https://avatars.githubusercontent.com/u/43266182?v=4&s=117" width="117">](https://github.com/taiki-fw) |[<img alt="theghostbel" src="https://avatars.githubusercontent.com/u/482899?v=4&s=117" width="117">](https://github.com/theghostbel) |[<img alt="titerman" src="https://avatars.githubusercontent.com/u/43554315?v=4&s=117" width="117">](https://github.com/titerman) |[<img alt="tobiasbueschel" src="https://avatars.githubusercontent.com/u/13087421?v=4&s=117" width="117">](https://github.com/tobiasbueschel) |
:---: |:---: |:---: |:---: |:---: |:---: |
[superroma](https://github.com/superroma) |[sylbru](https://github.com/sylbru) |[taiki-fw](https://github.com/taiki-fw) |[theghostbel](https://github.com/theghostbel) |[titerman](https://github.com/titerman) |[tobiasbueschel](https://github.com/tobiasbueschel) |

[<img alt="intermike" src="https://avatars0.githubusercontent.com/u/10540148?v=4&s=117" width="117">](https://github.com/intermike) |[<img alt="DevSide" src="https://avatars2.githubusercontent.com/u/6873926?v=4&s=117" width="117">](https://github.com/DevSide) |[<img alt="b12031106" src="https://avatars1.githubusercontent.com/u/2063566?v=4&s=117" width="117">](https://github.com/b12031106) |[<img alt="tomashanacek" src="https://avatars2.githubusercontent.com/u/1244486?v=4&s=117" width="117">](https://github.com/tomashanacek) |[<img alt="danielroe" src="https://avatars1.githubusercontent.com/u/28706372?v=4&s=117" width="117">](https://github.com/danielroe) |[<img alt="michaelficarra" src="https://avatars.githubusercontent.com/u/218840?v=4&s=117" width="117">](https://github.com/michaelficarra)
:---: |:---: |:---: |:---: |:---: |:---: |
[intermike](https://github.com/intermike) |[DevSide](https://github.com/DevSide) |[b12031106](https://github.com/b12031106) |[tomashanacek](https://github.com/tomashanacek) |[danielroe](https://github.com/danielroe) |[michaelficarra](https://github.com/michaelficarra)

[<img alt="varunkumar" src="https://avatars.githubusercontent.com/u/509433?v=4&s=117" width="117">](https://github.com/varunkumar) |[<img alt="VasilyStrelyaev" src="https://avatars.githubusercontent.com/u/11459924?v=4&s=117" width="117">](https://github.com/VasilyStrelyaev) |[<img alt="vitalics" src="https://avatars.githubusercontent.com/u/8816260?v=4&s=117" width="117">](https://github.com/vitalics) |[<img alt="Vla8islav" src="https://avatars.githubusercontent.com/u/1637557?v=4&s=117" width="117">](https://github.com/Vla8islav) |[<img alt="wentwrong" src="https://avatars.githubusercontent.com/u/26363017?v=4&s=117" width="117">](https://github.com/wentwrong) |
:---: |:---: |:---: |:---: |:---: |
[varunkumar](https://github.com/varunkumar) |[VasilyStrelyaev](https://github.com/VasilyStrelyaev) |[vitalics](https://github.com/vitalics) |[Vla8islav](https://github.com/Vla8islav) |[wentwrong](https://github.com/wentwrong) |

## Plugins

TestCafe developers and community members made these plugins:

* **Browser Providers**<br/>
  Use TestCafe with cloud browser providers and emulators.
  * [SauceLabs provider](https://github.com/DevExpress/testcafe-browser-provider-saucelabs) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [BrowserStack provider](https://github.com/DevExpress/testcafe-browser-provider-browserstack) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [CrossBrowserTesting provider](https://github.com/sijosyn/testcafe-browser-provider-crossbrowsertesting) (by [@sijosyn](https://github.com/sijosyn))
  * [LambdaTest provider](https://github.com/LambdaTest/testcafe-browser-provider-lambdatest) (by [@kanhaiya15](https://github.com/kanhaiya15))
  * [Nightmare headless provider](https://github.com/ryx/testcafe-browser-provider-nightmare) (by [@ryx](https://github.com/ryx))
  * [Testingbot provider](https://github.com/testingbot/testcafe-browser-provider-testingbot) (by [@testingbot](https://github.com/testingbot))
  * [fbsimctl iOS emulator](https://github.com/Ents24/testcafe-browser-provider-fbsimctl) (by [@ents24](https://github.com/Ents24))
  * [Electron](https://github.com/DevExpress/testcafe-browser-provider-electron) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [Puppeteer](https://github.com/jdobosz/testcafe-browser-provider-puppeteer) (by [@jdobosz](https://github.com/jdobosz))
  * [Puppeteer Chromium](https://github.com/stefanschenk/testcafe-browser-provider-puppeteer-chromium) (by [@stefanschenk](https://github.com/stefanschenk))

* **Framework-Specific Selectors**<br/>
  Work with page elements in a way that is native to your framework.
  * [React](https://github.com/DevExpress/testcafe-react-selectors) (by [@kirovboris](https://github.com/kirovboris))
  * [Angular](https://github.com/DevExpress/testcafe-angular-selectors) (by [@miherlosev](https://github.com/miherlosev))
  * [Vue](https://github.com/devexpress/testcafe-vue-selectors) (by [@miherlosev](https://github.com/miherlosev))
  * [Aurelia](https://github.com/miherlosev/testcafe-aurelia-selectors) (by [@miherlosev](https://github.com/miherlosev))

* **Plugins for Task Runners**<br/>
  Integrate TestCafe into your project's workflow.
  * [Grunt](https://github.com/crudo/grunt-testcafe) (by [@crudo](https://github.com/crudo))
  * [Gulp](https://github.com/DevExpress/gulp-testcafe) (by [@inikulin](https://github.com/inikulin))

* **Custom Reporters**<br/>
  View test results in different formats.
  * [TeamCity](https://github.com/Soluto/testcafe-reporter-teamcity) (by [@nirsky](https://github.com/nirsky))
  * [Slack](https://github.com/Shafied/testcafe-reporter-slack) (by [@Shafied](https://github.com/Shafied))
  * [NUnit](https://github.com/AndreyBelym/testcafe-reporter-nunit) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [TimeCafe](https://github.com/jimthedev/timecafe) (by [@jimthedev](https://github.com/jimthedev))

* **GitHub Action**<br/>
  Run TestCafe tests in GitHub Actions workflows.
  * [Run TestCafe](https://github.com/DevExpress/testcafe-action/)

* **Test Accessibility**<br/>
  Find accessibility issues in your web app.
  * [axe-testcafe](https://github.com/helen-dikareva/axe-testcafe) (by [@helen-dikareva](https://github.com/helen-dikareva))

* **IDE Plugins**<br/>
  Run tests and view results from your favorite IDE.
  * [TestCafe Test Runner](https://github.com/romanresh/vscode-testcafe) for Visual Studio Code (by [@romanresh](https://github.com/romanresh))
  * [TestLatte](https://github.com/Selminha/testlatte) for Visual Studio Code (by [@Selminha](https://github.com/Selminha))
  * [TestCafe runner for Webstorm](https://github.com/lilbaek/webstorm-testcafe) (by [@lilbaek](https://github.com/lilbaek))
  * [Code snippets for TestCafe](https://github.com/hdorgeval/testcafe-snippets) (by [@hdorgeval](https://github.com/hdorgeval))
  * [SublimeText](https://github.com/churkin/testcafe-sublimetext) (by [@churkin](https://github.com/churkin))

* **ESLint**<br/>
  Use ESLint when writing and editing TestCafe tests.
  * [ESLint plugin](https://github.com/miherlosev/eslint-plugin-testcafe) (by [@miherlosev](https://github.com/miherlosev))

* **Cucumber Support**<br/>
  Create and run tests that use the Cucumber syntax.
  * [gherkin-testcafe](https://github.com/kiwigrid/gherkin-testcafe) (by [@kiwigrid](https://github.com/kiwigrid)) - run your Cucumber tests with TestCafe as a backend. Requires [CucumberJS](https://github.com/cucumber/cucumber-js).
  * [testcafe-cucumber-steps](https://github.com/Marketionist/testcafe-cucumber-steps) (by [@Marketionist](https://github.com/Marketionist)) - provides predefined Cucumber steps for [gherkin-testcafe](https://github.com/kiwigrid/gherkin-testcafe).

## Different Versions of TestCafe

| &nbsp; | [TestCafe](https://testcafe.io) | [TestCafe Studio](https://www.devexpress.com/products/testcafestudio/?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff)  |
| ------ |:-------------------------------------------------:|:-----------------------------------------------------------------------:|
| No need for WebDriver, browser plugins or other tools | &#10003; | &#10003; |
| Cross-platform and cross-browser out of the box | &#10003; | &#10003; |
| Write tests in the latest JavaScript or TypeScript | &#10003; | &#10003; |
| Clear and flexible [API](https://testcafe.io/documentation/402632/reference) supports ES6 and [PageModel pattern](https://testcafe.io/documentation/402826/guides/concepts/page-model) | &#10003; | &#10003; |
| Stable tests due to the [Smart Assertion Query Mechanism](https://testcafe.io/documentation/402837/guides/basic-guides/assert#smart-assertion-query-mechanism) | &#10003; | &#10003; |
| Tests run fast due to intelligent [Automatic Waiting Mechanism](https://testcafe.io/documentation/402827/guides/concepts/built-in-wait-mechanisms) and [Concurrent Test Execution](https://testcafe.io/documentation/402830/guides/basic-guides/run-tests#run-tests-concurrently) | &#10003; | &#10003; |
| Custom reporter plugins | &#10003; | &#10003; |
| Use third-party Node.js modules in test scripts | &#10003; | &#10003; |
| Integration with popular CI systems | &#10003; | &nbsp;&#10003;\* |
| Free and open-source | &#10003; | &nbsp; |
| [Visual Test Recorder](https://docs.devexpress.com/TestCafeStudio/400165/guides/record-tests?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff) | &nbsp; | &#10003; |
| [Interactive Test Editor](https://docs.devexpress.com/TestCafeStudio/400190/user-interface/test-editor?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff) | &nbsp; | &#10003; |
| [Automatic Selector Generation](https://docs.devexpress.com/TestCafeStudio/400407/guides/record-tests/element-selectors#auto-generated-element-selectors?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff) | &nbsp; | &#10003; |
| [Run Configuration Manager](https://docs.devexpress.com/TestCafeStudio/400189/user-interface/run-configurations-dialog?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff) | &nbsp; | &#10003; |
| [IDE-like GUI](https://docs.devexpress.com/TestCafeStudio/400181/user-interface/code-editor?utm_source=github.com&utm_medium=referral&utm_campaign=tc-gh-diff) | &nbsp; | &#10003; |

\* You can use open-source TestCafe to run TestCafe Studio tests in CI systems.

## Badge

Show everyone you are using TestCafe: ![Tested with TestCafe](https://img.shields.io/badge/tested%20with-TestCafe-2fa4cf.svg)

To display this badge, add the following code to your repository readme:

```html
<a href="https://github.com/DevExpress/testcafe">
    <img alt="Tested with TestCafe" src="https://img.shields.io/badge/tested%20with-TestCafe-2fa4cf.svg">
</a>
```

## Thanks to BrowserStack

We are grateful to BrowserStack for providing the infrastructure that we use to test code in this repository.

<a href="https://www.browserstack.com/"><img alt="BrowserStack Logo" src="https://raw.github.com/DevExpress/testcafe/master/media/BrowserStack.png"/></a>

## License

Code released under the [MIT license](LICENSE).

## Creators

Developer Express Inc. ([https://devexpress.com](https://devexpress.com))
