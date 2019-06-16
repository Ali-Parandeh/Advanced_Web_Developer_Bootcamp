<p>I&nbsp;hope my summary note helps if you cannot understand the materials presented in this section.&nbsp;All of the example codes combined can be found in my codepen here which you can play around with to help you with understanding.</p>

<p><br></p>

<p><a href="https://codepen.io/aparandeh/pen/bQmOeb?editors=0010" target="_blank" rel="noopener noreferrer">JASMINE ALL EXAMPLES - CODEPEN</a></p>

<p><br></p>

<p>For Jasmine unit testing it's better to try the <a href="https://eu.udacity.com/course/javascript-testing--ud549" target="_blank" rel="noopener noreferrer">Udacity Javascript testing course</a>. Also reading their <a href="https://jasmine.github.io/tutorials/your_first_suite.html" target="_blank" rel="noopener noreferrer">official Jasmine docs</a>.</p>

<p><br></p>

<p>Watching this video can also help.</p>

<p><a href="https://www.youtube.com/watch?v=h2eWfvcAOTI" target="_blank" rel="noopener noreferrer">Unit Testing in JavaScript and Jasmine | TLDR Jasmine Unit Test Tutorial By: Dylan Israel</a></p>

<p><br></p>

<p>Here are my notes for this section:</p>

<p><br></p>

<p><strong>JASMINE SYNTAX &amp; MATCHER</strong></p>

<p><strong>Jasmine</strong>&nbsp;is a&nbsp;<em>behavior-driven development framework</em>&nbsp;for testing JavaScript code. It does not depend on any other JavaScript frameworks. It does not require a DOM. And it has a clean, obvious syntax so that you can easily write tests.</p>

<p><strong>Specs</strong>&nbsp;are defined by calling the global Jasmine function&nbsp;<code>it</code>, which, like&nbsp;<code>describe</code>&nbsp;takes a string and a function. The string is the title of the spec and the function is the spec, or test. A spec contains one or more expectations that test the state of the code. An&nbsp;<strong>expectation</strong>&nbsp;in Jasmine is an assertion that is either&nbsp;<code>true</code>&nbsp;or&nbsp;<code>false</code>. A spec with all&nbsp;<code>true</code>&nbsp;expectations is a passing spec. A spec with one or more&nbsp;<code>false</code>&nbsp;expectations is a failing spec.</p>

<p>describe()&nbsp;,&nbsp;<code>it()</code>&nbsp;and&nbsp;<code>.tobe()</code>&nbsp;are given to us by&nbsp;<strong>Jasmine</strong>.</p>

<p>.tobe()&nbsp;is a matcher that tests your code for specifications defined in&nbsp;<code>it()</code>.</p>

<p><strong>Specs</strong>&nbsp;are the&nbsp;<code>it()</code>s.</p>

<p>You often write all your specs in a separate specifications file.</p>

<p>The way you write Jasmine code is like this:&nbsp;<code>describe</code>&nbsp;something that&nbsp;<code>it</code>&nbsp;is going to be&nbsp;<strong>x</strong>&nbsp;and&nbsp;<strong>y</strong>.&nbsp;<code>Expect</code>&nbsp;that something&nbsp;<code>to be</code>&nbsp;<strong>x</strong>and&nbsp;<strong>y</strong>.</p>

<p>If 2 objects have different references in the memory then the&nbsp;<code>===</code>test will always be&nbsp;<code>false</code>.</p>

<p>tobe()&nbsp;works the same way as&nbsp;<code>===</code>&nbsp;and both values and references of the objects or arrays need to be the same. If we want to compare the values inside the arrays or objects that have different references, we use&nbsp;<code>toEqual()</code>.</p>

<p>jasmine.any()&nbsp;helps with checking the types of arrays, objects or items created by a specific function.&nbsp;<code>typeOf</code>&nbsp;itself cannot check the types of arrays as arrays are type of object themselves.</p>

<p>The 2nd parameter in&nbsp;<code>toBeCloseTo(3.141,3)</code>&nbsp;is the precision value which in this case is rounding up the number given to 3 decimal places.</p>

<p><br></p>

<p><strong>JASMINE: WRITING BETTER TESTS WITH HOOKS</strong></p>

<p>Instead of defining a new variable for each&nbsp;<code>it()</code>&nbsp;spec, we can define a variable first then assign it the shared value by&nbsp;<code>beforeEach()</code>&nbsp;which is run before each&nbsp;<code>it()</code>&nbsp;callback.</p>

<p>afterEach()&nbsp;does the same thing as&nbsp;<code>beforeEach()</code>&nbsp;but is run after each&nbsp;<code>it()</code>&nbsp;callback.</p>

<p><strong>Teardown</strong>&nbsp;is a code where your defined variable changes to something before each&nbsp;<code>it()</code>&nbsp;and changes back to what was before previously after each&nbsp;<code>it()</code>. You will very commonly see teardown code when testing databases to ensure that you start and end the test with the same sample data. </p>

<p>You can use&nbsp;<code>beforeAll()</code>&nbsp;and&nbsp;<code>afterAll()</code>&nbsp;when you want to define your variable and assign it a value only once and share it amongst&nbsp;<code>it()</code>&nbsp;specs. , These are functions that always run before or after each test.</p>

<p><strong>Nesting&nbsp;</strong><code><strong>describe</strong></code>: You can test&nbsp;<code>describe</code>s nested within each other if the test you are performing is complex and made out of multiple components. For example when testing an array, you want to test several functionalities of each array methods in separate&nbsp;<code>describe</code>s for each method.</p>

<p><strong>Pending Tests</strong>: Another thing we can do in writing tests is mark them as pending when we don't yet know the answer to the spec but we want the spec to be defined tor testing in the future. This is commonly done when we don't know exactly what we'll be testing or if we do not want to run a specific test. We can market test as pending or either emitting a callback function to the&nbsp;<code>it()</code>&nbsp;spec by adding the pending function&nbsp;<code>pending()</code>&nbsp;inside or simply placing an&nbsp;<code>x</code>&nbsp;before the&nbsp;<code>it()</code>&nbsp;spec.</p>

<p><strong># of&nbsp;</strong><code><strong>expect()</strong></code><strong>s per&nbsp;</strong><code><strong>it()</strong></code><strong>&nbsp;test</strong>: It is best practice to separate out number of expects in separate specs when undertaking unit testing with Jasmine. Mixing up multiple tests that test several different functions of the code cannot confidently give you good test results.&nbsp;<em>Only group expects together that are related to one functional unit.</em></p>

<p><strong>Quality of the tests</strong>: Vary the structure of your tests so that you don't accidentally miss a bug which is only happening when 2 specific function are executed one after another. Best practice is to use several data samples and separate out tests into units than mixing them together. Unless you're looking at a specific usecase which then you need to test for several things happening one after another or at the same time. You sometimes need to use same data-set to keep your testing variables to minimum so that you only have on variable changing not many. Otherwise, results you get cannot be interpreted or are meaningless.</p>

<p><br></p>

<p><strong>JASMINE: SPIES</strong></p>

<p>When&nbsp;<strong>Unit Testing</strong>&nbsp;we strive to isolate specific functionality and how each functionality behaves under variety of circumstances. With unit testing, we want to test small units of our code so we should not be invoking lots of functions that depend on other ones as they could take long to return. We should strive to use&nbsp;<strong>dummy data</strong>&nbsp;wherever possible to speed up our tests.</p>

<p><strong>Mocking</strong>: Many functions or objects may depend on other parts of our application. These can include other functions and data sources and even previously executed functions. This is where mocking helps. A&nbsp;<strong>mock</strong>&nbsp;is a fake object that poses as function without having to go through the overhead of creating the real object.</p>

<p>Mocks can be used to retrieve certain values like how many times the mock function was called, what value the function returned and how many parameters the function was called with.</p>

<p><strong>Spies</strong>&nbsp;in jasmine mocks are referred to as&nbsp;<strong>spies</strong>.</p>

<p>Spies often save us quite a bit of trouble when working with large code bases or testing libraries and help reduce the time it takes to run our tests.</p>

<p>Spies only exist in the&nbsp;<code>describe</code>&nbsp;or&nbsp;<code>it</code>&nbsp;block in which they are defined and are removed after each spec.</p>

<p>There are two ways to create a spy in jasmine: The&nbsp;<code>spyOn()</code>function which is used when the method exists on an object. The other way is&nbsp;<code>jasmine.createspy()</code>&nbsp;function which returns a brand new function.</p>

<p>When you are spying on an existing function make sure to use&nbsp;<code>spyon()</code>.</p>

<p><strong>Testing Input Parameters</strong>: We can use two spy matchers called&nbsp;<code>.toHaveBeenCalled()</code>&nbsp;and&nbsp;<code>toHaveBeenCalledWith()</code>.</p>

<p><strong>Testing Returned Value</strong>: We can test the returned value by invoking the spy function with dummy data then storing the returned value in a variable and testing that with&nbsp;<code>.toEqual()</code>&nbsp;matcher.</p>

<p><strong>Testing Frequency</strong>: We can test how many times a function has been called using the&nbsp;<code>.calls.any()</code>&nbsp;or&nbsp;<code>calls.count()</code>methods on a spy function.</p>

<p><br></p>

<p><strong>JASMINE: CLOCKS</strong></p>

<p><strong>Clock</strong>: Jasmine Clock is available for testing time dependent code.</p>

<p>It is installed by invoking&nbsp;<code>jasmine.clock().install()</code>&nbsp;but needs to be uninstalled after you are done to restore the original functions and to ensure no unintended side effects are present. You can install a clock inside a&nbsp;<code>beforeEach()</code>&nbsp;function and uninstall it inside&nbsp;<code>afterEach()</code>.</p>

<p>You can check how many times a function has been called on spies using&nbsp;<code>.calls.count()</code>&nbsp;or check if they have been called or not using&nbsp;<code>.calls.any()</code>. You can also check if they have not been called using&nbsp;<code>.not.toHaveBeenCalled()</code>.</p>

<p>With jasmine you can also test async code like AJAX, SetInterval or SetTimeout. All you need to do is to pass an optional single argument&nbsp;<code>"done"</code>&nbsp;to methods&nbsp;<code>beforeAll()</code>,&nbsp;<code>afterAll()</code>,&nbsp;<code>beforeEach()</code>,&nbsp;<code>afterEach()</code>&nbsp;or to callbacks of&nbsp;<code>it()</code>s and the test will not complete until the&nbsp;<code>done</code>&nbsp;function is invoked.</p>

<p>Jasmine has an internal timer that runs before the test fails to make sure that the test is not waiting too long. However, you can change the maximum value of this timer in jasmine settings.</p>

<p><br></p>

<p><strong>JASMINE: TDD &amp; BDD</strong></p>

<p><strong>Test Driven Development (TDD)</strong>&nbsp;is a software development approach where you write test specs, then strive to pass each test as you implement the application functionalities and as you implement each unit function, you refactor your code. Then you repeat the process for the next part of the application in larger projects. This is called the&nbsp;<strong>Red, Green, Refactor</strong>&nbsp;approach.</p>

<p><strong>Behaviour Driven Development (BDD)</strong>: Jasmine describes itself as BDD framework. BDD is a subset of TDD but not mutually exclusive with TDD. Instead of testing the outputs only we describe the behaviour of functional units so that we can test the design of the software.</p>

<p>There are some problems while preforming&nbsp;<strong>TDD</strong>: Where to start, how much need to test, understand why test fails. Solution for above problems is BDD. TDD describe how system works. BDD describe how end user use the system.</p>

<p><br></p>

<p><strong>JASMINE: OTHER KINDS OF TESTS</strong></p>

<p><strong>Integration Testing</strong>: Is meant to the the integration of our units and larger parts of our application. Here we test more than one unit and how they function together. This kind of testing builds on top of unit testing.</p>

<p><strong>Acceptance Testing</strong>: Involves performing tests on the full system which can include testing the application on the browser or a mobile device to understand if the software is fully passing the requirements of application. We're simply trying to see if something is acceptable or not. Entire system test, not how one unit functions or multiple units are integrated together.</p>

<p><strong>Stress Testing</strong>: Determines how effective our application can be under unfavorable conditions. These conditions include systems going down, high traffic or other scenarios that may not be common but can happen to an application.</p>

<p>User Acceptance Test is a&nbsp;<strong>phase</strong>&nbsp;in a typical software development process. From the other side, End-To-End test is one of the&nbsp;<strong>approaches</strong>&nbsp;to testing the complex applications which involves all layers of the application to interact with each other during test execution. It means that you can execute End-to-End test in User Acceptance Test phase, and you can't consider those two terms as one, that has the same meaning.</p>