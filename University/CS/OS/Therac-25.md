# Therac-25
#cs 


The therac-25 was a computer controlled radiation machine. 

It had 2 therapeutic modes, Electron mode and Photon mode.

The hazard of dual-mode machines is that when the turntable is in the wrong position, the flattener is misaligned causing high output dose rates.



### Causes

- Decided to not duplicate hardware safety mechanisms and interlocks in favour of software versions
- Implemented outdated code and design features from a previous model
- Lack of software documentation
- Safety analysis assumed the software was fine
- The software allowed concurrent access to shared memory leading to a race condition
- Often malfunctions would lead to an underdose rather than an overdose
- Cryptic message failures

### Incidents 

AECL was aware of potential issues but deemed it impossible to occur and took no action.

First incident was not reported to FDA.

The device regularly malfunctioned without affecting the patient which masked the accident

Machine inspections found nothing wrong so the issue was misdiagnosed.

AECL did not comply with suggested/directed orders. (malfunction behavior & potentiometer)




### Summary 

- Belief that the cause of the accident had been determined

- Assumption that fixing one error would prevent further accidents

- Management inadequacies and lack of procedures for following through on accidents

- Overconfidence in software and removal of hardware locks

- Terrible software-engineering practices

- Unrealistic risk assessments
