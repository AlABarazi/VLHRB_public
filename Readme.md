# High-Rise Building (HRB) Vertical Transportation Simulation

This project simulates vertical transportation in a high-rise building using an agent-based model. It focuses on elevator usage, worker movements, and construction logistics.

## Overview

The simulation models the following key components:

- Elevators
- Workers
- Construction wagons
- Break rooms, restrooms, and material storage areas
- Building floors and layout

The model aims to analyze elevator efficiency, worker productivity, and overall construction logistics in high-rise building projects.

## Key Features

- Time-based simulation with customizable parameters
- Multiple elevator types (passenger, material)
- Worker behavior modeling (arrivals, breaks, material transport)
- Construction wagon progression
- Data collection and analysis of system performance

## Requirements

- Python 3.7+
- Mesa (agent-based modeling framework)
- pandas
- numpy
- openpyxl (for Excel file handling)

## Setup

1. Install required packages:
   ```
   pip install mesa pandas numpy openpyxl
   ```

2. Place input Excel files in the `ABM/resources/` directory:
   - Takt plan file (e.g., "Skanska_Hyperion.xlsx")
   - Layout file (e.g., "work-map-profile.xlsx")
   - Sampling data file (e.g., "sampling.xlsx")
   - Elevator data file (e.g., "elevator_data.xlsx")

## Usage

1. Import the `HRB` class from the module.
2. Create an instance of the `HRB` model with desired parameters.
3. Run the simulation using the `run_model()` method or step through it manually.
4. Analyze the results using the data collector.

Example:

```python
from hrb_model import HRB

model = HRB(
    taktplan="Skanska_Hyperion.xlsx",
    layoutfile="work-map-profile.xlsx",
    scenario_sheet=5,
    sampling_filename="sampling.xlsx",
    elevators_data_filename="elevator_data.xlsx",
    simulation_startdate=datetime(2022, 5, 16, 6, 0, 0, 0),
    simulation_days=5
)

model.run_model(step_count=10000)

# Analyze results
results = model.datacollector.get_model_vars_dataframe()
print(results)
```

## Customization

The simulation offers many parameters for customization, including:

- Project start and simulation dates
- Work hours and break times
- Elevator configurations
- Worker behaviors
- Construction logistics factors

Refer to the `HRB` class initialization parameters for all available options.

## Data Collection

The simulation collects various metrics, including:

- System latency (overall, up/down, by floor level)
- Elevator utilization
- Worker productivity
- Trip data and destinations

Access this data through the `datacollector` attribute of the model instance.

## Notes

- The simulation uses real-world data from Excel files for takt planning, building layout, and elevator usage patterns.
- Adjust the `simulation_speed_microsec` parameter to control the time scale of the simulation.
- The model includes options for "dummy calls" to simulate additional elevator traffic based on historical data.

## Future Improvements

- Implement visualization of the simulation
- Add more detailed reporting and analysis tools
- Enhance worker decision-making logic
- Optimize performance for larger simulations

## License

This program is dual-licensed:

1. Open Source License: GNU General Public License v3.0
   - See the [GNU GPL v3](https://www.gnu.org/licenses/gpl-3.0.en.html) for details.

2. Commercial License: Available for purchase
   - Allows use in proprietary software without GPL obligations
   - Includes additional features and support

For commercial licensing options or any questions regarding usage and distribution, please contact:

Alaa Barazi
Email: alaabarazi@gmail.com

## Contact

For more information, support, or commercial inquiries, please contact:

Alaa Barazi
Email: alaabarazi@gmail.com

---

This README now includes your contact information and a brief explanation of the dual licensing approach. It informs users about the open-source option under GPL v3 and the availability of a commercial license. Users are directed to contact you for any licensing questions or commercial inquiries.