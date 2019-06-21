---


---

<h1 id="welcome-to-rule-generator">Welcome to Rule Generator</h1>
<p>Hi! I am going to walk you through he CBXC Backoffice <strong>Rule Generator</strong> component.</p>
<h1 id="about">About</h1>
<p>This is a front end component created using HTML, CSS and Javascript. Created for easy rule creation and manipulation.</p>
<h2 id="creating-a-rule"><strong>Creating a Rule</strong></h2>
<p>User will select a count role condition from input from provided.<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/RuleGen_Inputs.PNG" alt=""><br>
The above combination will result the below<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/RuleGen_Inputs_Output.PNG" alt="enter image description here"></p>
<h2 id="restrictions--possibilities">Restrictions / Possibilities</h2>
<p><strong>PARALLEL rule creation</strong><br>
Parallel condition should contain individual Role on it’s left and right.<br>
<em>Note : Once the parallel condition formed it can be grouped.</em></p>
<blockquote>
<p><em>R [parallel] R</em><br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Parallel%20Allowed.PNG" alt="enter image description here"></p>
</blockquote>
<p><strong>PARALLEL Rule grouping</strong><br>
A parallel condition can be grouped only with other parallel group</p>
<blockquote>
<p>[R-Parallel-R-Parallel-R-Parallel-R]  <img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Parallel_Grouping_Allowed.PNG" alt="enter image descriptionhere"></p>
</blockquote>
<h2 id="role---ui">Role - UI</h2>
<p>User Interface for a role will contains number of persons and their role and a dropdown indicator to change the role names using a dropdown.<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_UI.PNG" alt="Role Normal State"></p>
<p>Detailed actions will be enabled once the user mouse over on a role.<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Expanded_UI.PNG" alt="Role Detailed Action State"></p>
<p>Changing the roles<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Dropdown_UI.PNG" alt="Changing the roles dropdown"></p>
<h2 id="condition---ui">Condition - UI</h2>
<p>Conditions will be placed between two roles and defines how the two roles should act. Users can change the condition on the fly. “group” &amp; “ungroup” used for grouping.<br>
<img src="https://github.com/krish4u/RuleBuilder/blob/master/Condition_UI.PNG?raw=true" alt="Condition UI"></p>


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDMxODY5NTddfQ==
-->