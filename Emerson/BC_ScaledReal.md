<h1>BC_ScaledReal</h1>
<h2>SYNOPSIS</h2>
The Normalizing Function, with Limit Clamping
<h2>DESCRIPTION</h2>
To use this Program in Controlwave Designer. 
Create a new Function Program, Right Click Logical POUs>>Insert>>Function, </br> 
-   Select Language " ST ".
</br>
-   Copy <# Code #> Block
</br> 
-   Create Signals from the <# Signals #> block

<h2>INPUTS</h2>

| Name | Type | Default Value |
| --- | --- | --- |
| irInput |	REAL |	VAR_INPUT |		
irZero | REAL | VAR_INPUT |		
irSpan | REAL | VAR_INPUT |		
irScaledZero | REAL | VAR_INPUT |		
irScaledSpan | REAL | VAR_INPUT |		

<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
|  |  |  |

<h2>NOTES</h2>
<h4>Version:</h4> 1.0.0 - 29/06/2020 </br>
<h4>Author:</h4> Brett Courier
<h4>Reviewer:</h4> Jeff Jones
<h4>Blog:</h4> 

<h2>LINK</h2> 
<h2>License Info</h2>
Distributed under the MIT License (http://opensource.org/licenses/MIT)

<h2>EXAMPLE</h2>

<h2>Code</h2>

```
IF irInput > (irZero + irSpan) THEN
 ScaledReal := irScaledZero + irScaledSpan;
ELSIF irInput < irZero THEN
 ScaledReal := irScaledZero;
ELSE
 ScaledReal := (((irInput - irZero) / irSpan) * irScaledSpan) + irScaledZero;
END_IF;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| irInput |REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irZero | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |	
| irSpan | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irScaledZero | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irScaledSpan | REAL |VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |	