# Hospital reputation logic

There are two reputation systems, one for hospital and one for each disease case.

Reputation is not changed directly by adding or subtracting, it changes by using positive and negative factors, the formula is the same for both systems:

**reputation = positiveFactor * 500 / negativeFactor**

They capped from both ends:

* if negativeFactor < 1 then reputation is set to 500
* if reputation < 0 then reputation is set to  0
* if reputation > 1000 then reputation is set to 1000

Reputation of a disease case influences its cost.

Factors are changing depending on the game event, in the table you can find all events and their effects.
I'm still in progress of discovering what some of them means.
Some of them just add or subtract value from the factor, but most of them depend on the current value of a factor.

Some of them change factor only for hospital or disease case, some for both at the same time.

For example, in the event `0x5` for `Hosp+` (Hospital reputation positive factor) you can see formula `(Hosp-)*5/-100`.
It means that game takes current `Hosp-` (Hospital reputation negative factor) multiplies it by `5` and divides by `100` and stores it as new `Hosp+`. Same happens for disease case, it just uses factors for this disease case.

In the event `0xD`, which happens when emergency was failed, the `count` variable is equal to amount of patients left untreated and died in the emergency.

Zero means no change.

| Event | Description | Hosp+ | Hosp- | Disease+ | Disease- |
| --- | --- | --- | --- | --- | --- |
| 0x0 | OnPatientCured | +1 | 0 | +1 | 0 |
| 0x6 | ??? (AI only?) | +1 | 0 | +1 | 0 |
| 0x15 | OnDisgnosed | +1 | 0 | +1 | 0 |
| 0x3 | OnDeath | -1 | 0 | -1 | 0 |
| 0x19 | ??? | -1| 0 | -1 | 0 |
| 0x5 | ??? | (Hosp-)*5/-100 | 0 | (Disease-)*5/100 | 0 |
| 0x9 | ??? | (Hosp-)*5/100 | 0 | (Disease-)*5/100 | 0 |
| 0xB | Explosion | (Hosp-)*10/-100 | 0 | 0 | 0 | 
| 0xC | EmergencyWin | (Hosp-)*2/100 | 0 | 0 | 0 |
| 0xD | EmergencyLost | (Hosp-) *4 *count/-100 | 0 | 0 | 0 | 
| 0xE | EpidemicDeclare | (Hosp-)*2/-100 | 0 | 0 | 0 | 
| 0xF | EpidemicLost | (Hosp-)*10/-100 | 0 | 0 | 0 | 
| 0x10 | OnVIPScore | (Hosp-)*4/100 | 0 | 0 | 0 | 
| 0x11 | OnVIPScore | (Hosp-)*2/100 | 0 | 0 | 0 | 
| 0x12 | OnVIPScore | (Hosp-)*4/-100 | 0 | 0 | 0 | 
| 0x13 | ??? | (Hosp-)*-20/100 | 0 | 0 | 0 | 
| 0x14 | ??? | -1 | 0 | ? | ? |
| 0x16 | ??? | 0 | +1 | 0 | +1 |
| 0x17 | ??? | (Hosp-)*count/100 | 0 | 0 | 0 |
| 0x18 | EndYearTrophy? | (Hosp-)*count/100 | 0 | 0 | 0 | 
| 0xA | OnPatientEndSession | 0 | 0 | 0 | 0 |
| 0x7 | InDoubt | 0 | 0 | 0 | 0 |
| 0x4 | ??? | 0 | 0 | 0 | 0 |
| 0x2 | ??? | 0 | 0 | 0 | 0 |
