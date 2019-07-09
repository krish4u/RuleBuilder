# Welcome to Rule Generator
Hi! I am going to walk you through he CBXC Backoffice **Rule Generator** component.

# About
This is a front end component created using HTML, CSS and Javascript. Created for easy rule creation and manipulation.

# Creating a Rule
User will select a count role condition from input from provided.
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/RuleGen_Inputs.PNG" alt="">
The above combination will result the below
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/RuleGen_Inputs_Output.PNG" alt="enter image description here">
## Restrictions / Possibilities
**PARALLEL rule creation**
Parallel condition should contain individual Role on it’s left and right.
_Note : Once the parallel condition formed it can be grouped._

**R [parallel] R**
><img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Parallel%20Allowed.PNG" alt="Parallel condition">

**PARALLEL Rule grouping**

A parallel condition can be grouped only with other parallel group
>[R-Parallel-R-Parallel-R-Parallel-R]  
><img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Parallel_Grouping_Allowed.PNG" alt="enter image descriptionhere">

## Role - UI
User Interface for a role will contains number of persons and their role and a dropdown indicator to change the role names using a dropdown.
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_UI.PNG" alt="Role Normal State"></p>
<p>Detailed actions will be enabled once the user mouse over on a role.<br>
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Expanded_UI.PNG" alt="Role Detailed Action State"></p>
Changing the roles
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Dropdown_UI.PNG" alt="Changing the roles dropdown"></p>
## Condition - UI
Conditions will be placed between two roles and defines how the two roles should act. Users can change the condition on the fly. “group” &amp; “ungroup” used for grouping.
<img src="https://github.com/krish4u/RuleBuilder/blob/master/Condition_UI.PNG?raw=true" alt="Condition UI"></p>

# cbx_rulegen_core.js
Rule generator runs on javascript. A function oriented programming apporach.  The functions listed below are handling the major working of rule generator.

## function handleBreak(getId,scope)
This function hleps the rule builder to break properly into a second line where the constructed rules reaches the screen width.

*Parameters:*
>__getId__ - To identifiy the section supposed to brought to next line is grouped or ungrouped   
>__scope__ - Actual element that triggres the ``handleBreak`` function.


## function handleParallel(v,y)    
When a condition is set to *``parallel``* it's left and right conditions will be validated as per below
*Scenario:*
* Left and right should be independnet Roles.   
* If it supposed to be grouped with other groups the conditions present in the group should be ``parallel``.    

*Parameters:*   
__v__ - Current value selected on dropdown   
__y__ - Scope when clicked

## function closeme(getter)
This function removes a role if user clicks the *``x``* close icon. It takes a single parameter of current scope and traverse to its parent then removes the role.

##### Independent Role Scenario:
If a role alone present it will removed along with any leaf condition present next to the deleted role.  
##### Grouped Role Scenario:
* Item to be deleted present at end of the group then the role alone will be deleted.
* Item to be deleted present at beginning or middle of the group then the role and condition next to it will be deleted.

*Parameters:*   
__getter__ - current element when clicked.

## function validateParing(valBefore, valnext);
This is a validation function makes sure the grouping done properly and added required identifiers for further processing.

*Parameters:*   
__valBefore__ - current element when clicked.
__valnext__ - current element when clicked.

## function handleSpinner(getter)
On click of ``+`` and ``-`` increase / decrease the roles count. The max and min value will be validated by a function named ``handleOverflow()``.
*Parameters:*   
__getter__ - ``+`` or ``-`` button which is clicked.

## function handleOverflow(getVal,scope)
Developers can limit the number of users for a role via HTML5 ``max`` &amp; ``min`` attributes.
*Parameters:*   
__getVal__ - Current incremented / decremented value in spinner
__scope__ - Actual spinner value field 

## function buildCounter(b)
fill here
``function buildDropdown(selectedRole, roleList)``
``function buildCondition(b)``
``function subRuleCreation (roleList)``
``function parallelCheck(g)``

## Getting a rule from DB and process it
``function frameRoleTemplate(userCount, roleLvl)``
``function pushRoleProcess(x,z,nextvalue)``
``function decideLogic(nextvalue)``
``function pusherClosegrp()``
``function pushCondProcess(x,z)``
``function pushMaster(roleLevel,count)``
``function getActionType (rowCount) ``
