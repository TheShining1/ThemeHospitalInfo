For both, hospital and disease case.

reputation = positiveFactor * 500 / negativeFactor

if negativeFactor < 1 then reputation = 500

if reputation < 0 then reputation = 0
if reputation > 1000 then reputation = 1000


| Event | Desc | Hosp+ | Hosp- | Disease+ | Disease- |
| --- | --- | --- | --- | --- | --- |
| 0x0 | OnPatientCured | 1 | 0 | 1 | 0 |
| 0x6 | ??? (AI only?) | 1 | 0 | 1 | 0 |
| 0x15 | OnDisgnosed | 1 | 0 | 1 | 0 |
| 0x3 | OnDeath | -1 | 0 | -1 | 0 |
| 0x19 | ??? | -1| 0 | (-1) | 0 |
| 0x5 | ??? | (Hosp-)*5/-100 | 0 | (Disease-)*5/100 | 0 |
| 0x9 | ??? | (Hosp-)*5/100 | 0 | (Disease-)*5/100 | 0 |
| 0xB | Explosion | (Hosp-)*10/-100 | 0 | 0 | 0 | 
| 0xC | EmergencyWin | (Hosp-)*2/100 | 0 | 0 | 0 |
| 0xD | EmergencyLost | (Hosp-)*4*count/-100 | 0 | 0 | 0 | 
| 0xE | EpidemicDeclare | (Hosp-)*2/-100 | 0 | 0 | 0 | 
| 0xF | EpidemicLost | (Hosp-)*10/-100 | 0 | 0 | 0 | 
| 0x10 | OnVIPScore | (Hosp-)*4/100 | 0 | 0 | 0 | 
| 0x11 | OnVIPScore | (Hosp-)*2/100 | 0 | 0 | 0 | 
| 0x12 | OnVIPScore | (Hosp-)*4/-100 | 0 | 0 | 0 | 
| 0x13 | ??? | (Hosp-)*-20/100 | 0 | 0 | 0 | 
| 0x14 | ??? | -1 | 0 |||
| 0x16 | ??? | 0 | 1 | 0 | 1|
| 0x17 | ??? | (Hosp-)*count/100 | 0 | 0 | 0 |
| 0x18 | EndYearTrophy? | (Hosp-)*count/100 | 0 | 0 | 0 | 
| 0xA | OnPatientEndSession | 0 | 0 | 0 | 0 |
| 0x7 | InDoubt | 0 | 0 | 0 | 0 |
| 0x4 | ??? | 0 | 0 | 0 | 0 |
| 0x2 | ??? | 0 | 0 | 0 | 0 |
