<h1>BC_Rank2</h1>
<h2>SYNOPSIS</h2>
Alternation Increment count when all pumps off for 2 pumps
<h2>DESCRIPTION</h2>
To use this Program in Controlwave Designer. 
Create a new Structure Text Program, Right Click Logical POUs>>Insert>>Program, </br> 
-   Select Language " SFC ".
</br>
-   Copy "Code" Block
</br> 
-   Create Signals from the "Signals" block
<h2>INPUTS</h2>

| Name | Type | Default Value |
| --- | --- | --- |
| ibAllOffFlag | BOOL |
| irLeadSelect | REAL |
| iiAvailableCount | INT |

<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
| orRank1 | REAL |
| orRank2 | REAL |

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
 CTU_1(
 CU:=ibAllOffFlag,
 RESET:=AltCntRst,
 PV := iiAvailableCount);
 AltCntRst:=CTU_1.Q;
 AltSeq:=CTU_1.CV;
  
(* [LEAD_SELECT] = 1.0 FOR LCSP1A, 2.0 FOR LCSP1B ETC *)

  	IF (irLeadSelect <> 0.0) THEN
		IF (irLeadSelect = 1.0) THEN
			AltSeq := 0;
		END_IF;
		IF (irLeadSelect = 2.0) THEN
			AltSeq := 1;
		END_IF;

	END_IF;

	  	CASE AltSeq OF
			0:
				orRank1:=1.0;
				orRank2:=2.0;
			1:
				orRank1:=2.0;
				orRank2:=1.0;
		END_CASE;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ibAllOffFlag | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 | 
| CTU_1 | CTU | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| AltCntRst | BOOL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| AltSeq | INT | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irLeadSelect |  REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iiAvailableCount | INT | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRank1 | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRank2 | REAL | VAR_OUTPUT |  |  | 0 |0 | 0 | 0 | 0 |  | 0 |