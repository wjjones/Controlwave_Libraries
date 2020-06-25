<h1>BC_Sequencer4</h1>
<h2>SYNOPSIS</h2>
Alternation Increment count when all pumps off
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
|  | BOOL |
|  | REAL |
|  | INT |


<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
|  | REAL |
|  | REAL |
|  | REAL |
|  | REAL |

<h2>NOTES</h2>
<h4>Version:</h4> 1.0.0 - 25/05/2020 </br>
<h4>Author:</h4> Jeff Jones
<h4>Blog:</h4> 

<h2>LINK</h2> 
<h2>License Info</h2>
Distributed under the MIT License (http://opensource.org/licenses/MIT)

<h2>EXAMPLE</h2>

<h2>Code</h2>

```
(* Alternation Increment count when all pumps off  *)
CTU_1(
 CU:=ibAllOffFlag,
 RESET:=AltCntRst,
 PV := iiAvailableCount);
 AltCntRst:=CTU_1.Q;
 AltSeq:=CTU_1.CV;

	LeadIn:=LIMIT(1.0,iorLead,4.0);
	If  (NOT ibUnavalable1) and ibUnavalable2 and  ibUnavalable3 and  ibUnavalable4 then
		LeadIn := 1.0;
	End_If;
	If    ibUnavalable1 and (NOT ibUnavalable2)  and ibUnavalable3 and  ibUnavalable4 then
		LeadIn := 2.0;
	End_If;
	If   ibUnavalable1 and  ibUnavalable2 and  (NOT ibUnavalable3) and ibUnavalable4 then
		LeadIn := 3.0;
	End_If;
	If  ibUnavalable1 and ibUnavalable2 and ibUnavalable3 and (NOT ibUnavalable4) then
		LeadIn := 4.0;
	End_If;

	IF (LeadIn <> OldLeadSelect) Then
			IF ibUnavalable1 Then
				IF LeadIn = 1.0 Then
			    	iorLead := OldLeadSelect;
				End_If;
			ElsIf ibUnavalable2 Then
				IF LeadIn = 2.0 Then
		    		iorLead := OldLeadSelect;
				End_If;
			ElsIf ibUnavalable3 Then
				IF LeadIn = 3.0 Then
	    			iorLead := OldLeadSelect;
				End_If;
			ElsIf ibUnavalable4 Then
				IF LeadIn = 4.0 Then
    				iorLead := OldLeadSelect;
				End_If;							
			End_If;
			OldLeadSelect := iorLead;
	End_if;

  	IF (iorLead <> 0.0) THEN
		IF (iorLead = 1.0) THEN
			AltSeq := 0;
		END_IF;
		IF (iorLead = 2.0) THEN
			AltSeq := 1;
		END_IF;
		IF (iorLead = 3.0) THEN
			AltSeq := 2;
		END_IF;
		IF (iorLead = 4.0) THEN
			AltSeq := 3;
		END_IF;
	END_IF;
	  	CASE AltSeq OF
			0:
				orRank1:=1.0;
    			orRank2:=2.0;
 				orRank3:=3.0;
				orRank4:=4.0;
		    1:
 	   			orRank1:=4.0;
    			orRank2:=1.0;
 				orRank3:=2.0;
				orRank4:=3.0;
			2:
				orRank1:=3.0;
    			orRank2:=4.0;
 				orRank3:=1.0;
				orRank4:=2.0;
			3:
				orRank1:=2.0;
    			orRank2:=3.0;
 				orRank3:=4.0;
				orRank4:=1.0;
	END_CASE;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CTU_1 | CTU | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| AltCntRst | BOOL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| AltSeq | INT | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| OldLeadSelect | REAL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| LeadIn | REAL | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iiAvailableCount | INT | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibAllOffFlag | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavalable1 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavalable2 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavalable3 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavalable4 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRank1 | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRank2 | REAL | VAR_OUTPUT |  |  | 0 |0 | 0 | 0 | 0 |  | 0 |
| orRank3 | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| orRank4 | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iorLead | REAL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |


orRank1	REAL	VAR_OUTPUT				0	0	0	0	0	0		
orRank2	REAL	VAR_OUTPUT				0	0	0	0	0	0		
orRank3	REAL	VAR_OUTPUT				0	0	0	0	0	0		
orRank4	REAL	VAR_OUTPUT				0	0	0	0	0	0		
	REAL	VAR_IN_OUT				0	0	0	0	0	0		
