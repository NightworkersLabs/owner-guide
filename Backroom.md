# Backroom
Allows LOLLY holders "Yield Aggregator"-like features to exclusively gain native Ether.
Based on owner pre-defined round periods and rewards.
## scheduleRound
Schedule a new round. Can replace a to-be-started round : if it happens, any ETH bound to the replaced round will be skimed back to the owner of the contract.
| Parameter | Expected Type | Description | Requirements |
|--|--|--|--|
| *distributionRate_* | `wei`  | How much rewards (in ETH) will be proportionnally distributed between stakers per second. Combined with *value*, defines when the round ends. |
| *startsInSecs_* | `seconds`  | How many seconds after the acknowledgment of this round by the blockchain will this round considered started.|
| *gracePeriodDurationInSecs_* | `seconds`  | After the end of this round, allows *gracePeriodDurationInSecs_* seconds for stakers to claim their rewards. Once this period is over, rewards are lost for stakers and clamable by the owner.  | 1 > days < 30 
| *value* | `wei`  | Maximum amount of ETH that will be shared amongst stakers for this round. | > 1  ether |
## cancelRound
Cancels scheduled rounds. Rounds that already started cannot be cancelled.
| Parameter | Expected Type | Description|
|--|--|--|
| *roundIdToCancel_* | `number`  | Which scheduled round to cancel. |
| *noAutoSkim_* | `0 or 1`  | Defines if we want cancelled round associated rewards to be skimmed in the same transaction.|
## skimUnclaimedRewards
Skims any ETH rewards associated with cancelled rounds, or unclaimed rewards of past rounds.

| Parameter | Expected Type | Description|
|--|--|--|
|None|