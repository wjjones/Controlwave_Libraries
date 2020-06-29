<h1>BC_Real_To_Time</h1>
<h2>SYNOPSIS</h2>
Function Block to convert a real number to a Time
<h2>DESCRIPTION</h2>
To use this Program in Controlwave Designer. 
Create a new Function Block Program and Select LD as Type, Right Click Logical POUs>>Insert>>Function Block Diagram, </br> 
-   Select Language " LD ".
</br>

<h2>INPUTS</h2>

| Name | Type | Default Value |
| --- | --- | --- |
| irIN | REAL |

<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
|  | Time |


<h2>NOTES</h2>
<h4>Version:</h4> 1.0.0 - 25/05/2020 </br>
<h4>Author:</h4> Brett Courier
<h4>Reviewer:</h4> Jeff Jones
<h4>Blog:</h4> 

<h2>LINK</h2> 
<h2>License Info</h2>
Distributed under the MIT License (http://opensource.org/licenses/MIT)

<h2>EXAMPLE</h2>

<h2>Code</h2>

```
LD		irIN
MUL		REAL#1.0E3
REAL_TO_DINT	
DINT_TO_TIME
ST Real_To_Time
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| irIN | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |