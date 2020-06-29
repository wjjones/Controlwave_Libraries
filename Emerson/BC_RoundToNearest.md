<h1>BC_RoundToNearest</h1>
<h2>SYNOPSIS</h2>
This function Rounds up or down by a specific increment
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
| ibRoundUp | BOOL | VAR_INPUT |
| irNumber | REAL |	VAR_INPUT |	
| irRoundAmount | REAL | VAR_INPUT |

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
Temp1 := irNumber / irRoundAmount;

If Temp1 = DINT_TO_REAL(Temp2) Then
 RoundToNearest
  := irNumber;
Elsif Not ibRoundUp Then
 Temp2 := REAL_TO_DINT(Temp1 - 0.5);
 Temp1 := DINT_TO_REAL(Temp2);
 Else
 Temp2 := REAL_TO_DINT(Temp1 + 0.5);
 Temp1 := DINT_TO_REAL(Temp2);
End_If;

 RoundToNearest :=  Temp1 * irRoundAmount;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Temp1 | REAL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibRoundUp | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irNumber | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irRoundAmount | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| Temp2 | VAR | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |