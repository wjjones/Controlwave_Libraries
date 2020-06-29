<h1>BC_Scheduler_2</h1>
<h2>SYNOPSIS</h2>
This will schedule runtime between 2 pumps
<h2>DESCRIPTION</h2>
To use this Program in Controlwave Designer. 
Create a new Function Block, Right Click Logical POUs>>Insert>>Function Block, </br> 
-   Select Language " ST ".
</br>
-   Copy <# Code #> Block
</br> 
-   Create Signals from the <# Signals #> block

<h2>INPUTS</h2>

| Name | Type | Default Value |
| --- | --- | --- |
| iiMode | INT | VAR_INPUT |
| ibState |	BOOL | VAR_INPUT |
| ibStrobe | BOOL | VAR_INPUT |
| ibReset | BOOL | VAR_INPUT |
| irRank_1 | REAL | VAR_INPUT |
| ibUnavailable_1 |	BOOL | VAR_INPUT |
| ibFailState_1 | BOOL | VAR_INPUT |
| irRank_2 | REAL | VAR_INPUT |
| ibUnavailable_2 |	BOOL | VAR_INPUT |
| ibFailState_2 | BOOL | VAR_INPUT |

<h2>OUTPUTS</h2>

| Name | Type | Default Value |
| --- | --- | ---|
| obTrack |	BOOL | VAR_OUTPUT |
| odiStatus | DINT | VAR_OUTPUT |
| obOutput_1 | BOOL | VAR_OUTPUT |
| obOutput_2 | BOOL | VAR_OUTPUT |

<h2>NOTES</h2>
<h4>Version:</h4> 1.0.0 - 29/06/2020 </br>
<h4>Author:</h4> Brett Courier
<h4>Reviewer:</h4> Jeff Jones
<h4>Blog:</h4> 

<h2>LINK</h2> 
<h2>License Info</h2>
Distributed under the MIT License (http://opensource.org/licenses/MIT)

<h2>EXAMPLE</h2>

<h2>Data Type </h2>

```
TYPE
     Pumps      :
       STRUCT
           irRank        : REAL;
           ibUnavailable : BOOL;
           ibFail_state  : BOOL;
           obOutput      : BOOL;
           pad1        : BOOL;
       END_STRUCT;
 
     Array2Pumps    : ARRAY[1..3] OF Pumps;
END_TYPE
```

<h2>Code</h2>

```
I
SCHEDULER_1(
iiMode:=iiMode,
iaibDeviceInfo:=DeviceArray,
ibReset:=ibReset,
ibStrobe:=ibStrobe,
ibState:=ibState);
odiStatus:=SCHEDULER_1.odiStatus;
obTrack:=SCHEDULER_1.obTrack;


DeviceArray[1].irRank:= irRank_1;
DeviceArray[1].ibUnavailable := ibUnavailable_1;
DeviceArray[1].ibFail_state := ibFailState_1;
obOutput_1 := DeviceArray[1].obOutput;

DeviceArray[2].irRank:= irRank_2;
DeviceArray[2].ibUnavailable := ibUnavailable_2;
DeviceArray[2].ibFail_state := ibFailState_2;
obOutput_2 := DeviceArray[2].obOutput;
```

<h2>Signals</h2>

| Name | Type | Usage | Description | Address | Retain | PDD | TB | Hidden |   InitvalueHidden | DefaultHiddent | Redundant |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SCHEDULER_1 |	SCHEDULER | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| DeviceArray |	Array2Pumps | VAR |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| iiMode | INT | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibState |	BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibStrobe | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibReset | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irRank_1 | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavailable_1 |	BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibFailState_1 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| irRank_2 | REAL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibUnavailable_2 |	BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| ibFailState_2 | BOOL | VAR_INPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| obTrack |	BOOL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| odiStatus | DINT | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| obOutput_1 | BOOL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |
| obOutput_2 | BOOL | VAR_OUTPUT |  |  | 0 | 0 | 0 | 0 | 0 |  | 0 |