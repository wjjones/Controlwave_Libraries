<h1>BC_RAMP</h1>
<h2>SYNOPSIS</h2>
This is used as a template for descriptions and program
<h2>DESCRIPTION</h2>
To use this Program in Controlwave Designer. 
Create a new Structure Text Program, Right Click Logical POUs>>Insert>>Program, </br> 
-   Select Language " SFC ".
</br>
-   Copy <# Code #> Block
</br> 
-   Create Signals from the <# Signals #> block

<h2>INPUTS</h2>

| Name | Type | Default Value |
| --- | --- | --- |
| ibStart | BOOL |
| ibStop | BOOL |
| ibHold | BOOL |
| iiStartValue | INT |
| iiEndValue | INT |


<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
| orRampOut | REAL |
| obTrack | BOOL |

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
IF NOT ibStop THEN
	IF ibStart AND NOT run THEN  
		int_value := iiStartValue;
        run:=TRUE;
	END_IF;
    IF run THEN
    	IF NOT ibHold THEN
        	int_value := (int_value+1) MOD (iiEndValue+1);
            orRampOut := INT_TO_REAL(int_value);
			IF int_value = iiEndValue THEN
				obTrack := TRUE;
			END_IF; 
		END_IF;      
	END_IF;
ELSE
	run:=FALSE;
	orRampOut:= 0.0;
    int_value:=0;
	obTrack := FALSE;
END_IF;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ibStart | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 | 
| ibStop | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibHold | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRampOut | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| run |  BOOL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| int_value | INT | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iiStartValue | INT | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iiEndValue | INT | VAR_INPUT |  |  | 0 |0 | 0 | 0 | 0 |  | 0 |
| obTrack | BOOL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |