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
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_UI.PNG" alt="Role Normal State">
Detailed actions will be enabled once the user mouse over on a role.    
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Expanded_UI.PNG" alt="Role Detailed Action State">
####  Changing the roles    
<img src="https://raw.githubusercontent.com/krish4u/RuleBuilder/master/Role_Dropdown_UI.PNG" alt="Changing the roles dropdown">

## Condition - UI
Conditions will be placed between two roles and defines how the two roles should act. Users can change the condition on the fly. “group” &amp; “ungroup” used for grouping.
<img src="https://github.com/krish4u/RuleBuilder/blob/master/Condition_UI.PNG?raw=true" alt="Condition UI">

# cbx_rulegen_core.js
Rule generator runs on javascript. A function oriented programming apporach.  The functions listed below are handling the major working of rule generator.

### function handleBreak(getId,scope)
This function hleps the rule builder to break properly into a second line where the constructed rules reaches the screen width.

*Parameters:*
>__getId__ - To identifiy the section supposed to brought to next line is grouped or ungrouped   
>__scope__ - Actual element that triggres the ``handleBreak`` function.


### function handleParallel(v,y)    
When a condition is set to *``parallel``* it's left and right conditions will be validated as per below
*Scenario:*
* Left and right should be independnet Roles.   
* If it supposed to be grouped with other groups the conditions present in the group should be ``parallel``.    

*Parameters:*   
__v__ - Current value selected on dropdown   
__y__ - Scope when clicked

### function closeme(getter)
This function removes a role if user clicks the *``x``* close icon. It takes a single parameter of current scope and traverse to its parent then removes the role.

##### Independent Role Scenario:
If a role alone present it will removed along with any leaf condition present next to the deleted role.  
##### Grouped Role Scenario:
* Item to be deleted present at end of the group then the role alone will be deleted.
* Item to be deleted present at beginning or middle of the group then the role and condition next to it will be deleted.

*Parameters:*   
__getter__ - current element when clicked.

### function validateParing(valBefore, valnext);
This is a validation function makes sure the grouping done properly and added required identifiers for further processing.

*Parameters:*   
__valBefore__ - current element when clicked.
__valnext__ - current element when clicked.

### function handleSpinner(getter)
On click of ``+`` and ``-`` increase / decrease the roles count. The max and min value will be validated by a function named ``handleOverflow()``.

*Parameters:*   
__getter__ - ``+`` or ``-`` button which is clicked.

### function handleOverflow(getVal,scope)
Developers can limit the number of users for a role via HTML5 ``max`` &amp; ``min`` attributes.

*Parameters:*   
__getVal__ - Current incremented / decremented value in spinner
__scope__ - Actual spinner value field 

### function buildCounter(b)
This funcion generates template for role counter. Based on the user input the counter value ``b`` set and append to the role template.

*Parameters:*   
__b__ - Number of Role value.

### function buildDropdown(selectedRole, roleList)
This function builds the dropdown template and append to the role template. The roles will be fetched from backend and passed to this function.

*Parameters:*   
__selectedRole__ - User input for the role name from dropdown.
__roleList__ - List of roles from Database.

### function buildCondition(b)
Builds the condition template with user selected input.
*__Note : As of now the template is hardcoded and satic. It should be change as dynamic.__*

*Parameters:*   
__b__ - User input from condition dropdown.

### function parallelCheck(g)
Validating ``parallel`` condition by taking all possible allowed / not allowed conditions.
This check will happen when user tries to group / ungroup.

*Parameters:*   
__g__ - Current groping value ( Group /  Ungroup)

### function subRuleCreation (roleList)
*Suspended function - Not in use*


# Generating rule from existing set ( Reversh Push )
Editing an already existing rule will be handled by the below functions.

### function pushRoleProcess(x,z,nextvalue)
This is the function initially called when a rule is trying to get build.  It will have a ``pushcounter`` to get track of rule build process.

From this function there will a call to ``frameRoleTemplate()`` function.

### function frameRoleTemplate(userCount, roleLvl)
This function will build user template and append it to the role template.
*Parameters:*   
__userCount__ - Number of users count
__roleLvl__ - role value


### function decideLogic(nextvalue)
This function is responsible for generate roles grouped or ungrouped
*Parameters:*   
__nextvalue__ - Gives the next values coming up in role.


### function pusherClosegrp()
Find ending of a group and closes the group.

### function pushCondProcess(x,z)
Prepares condition template and append to the rule.
*Parameters:*   
__x,z__ - Determine the condition is grouping or not.

### function pushMaster(roleLevel,count)
Routes to the appropriate ``pushCondProcess``.
*Parameters:*
__roleLevel__ : current role
__count__ : role count

### function getActionType (rowCount)
Determine the action ADD or MODIFY
*Parameter*:
__rowCount__ : number of rows.
