# Proyecto-integrador-EMG


```
from scipy.stats import ttest_rel
import numpy as np

def evaluate_fatigue_first_last(freq_medians):
    if len(freq_medians) < 3:
        print(" No hay suficientes contracciones para aplicar la prueba t de Student.")
        return None, None, "Sin datos", (None, None)
    
    # Tomamos las primeras y las últimas 3 ventanas
    first = np.array(freq_medians[:3], dtype=np.float64)
    last = np.array(freq_medians[-3:], dtype=np.float64)
    
    # Prueba t de Student pareada
    t_stat, p_value = ttest_rel(first, last)
    test_name = "Prueba T de Student pareada"
    
    return t_stat, p_value, test_name, (first, last)
```

