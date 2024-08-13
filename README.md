# Learning-Python2

assumption = {
    "DEATH_PROB": 0.003,
    "INTEREST_RATE": 0.005
}

import pandas as pd
from cashflower import ModelPointSet

main = ModelPointSet(data=pd.DataFrame({
    "id": [1],
    "sum_assured": [100_000],
    "remaining_term": [36],
}))

from cashflower import variable

from input import assumption, main
from settings import settings

@variable()
def survival_rate(t):
    if t == 0:
        return 1
    return survival_rate(t-1) * (1-assumption["DEATH_PROB"])
