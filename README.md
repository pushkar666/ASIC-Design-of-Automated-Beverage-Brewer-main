# Coffee Making Machine Module

This project implements a coffee-making machine using Verilog HDL. The module allows the selection of different coffee options (Espresso, Milk, or Cappuccino) with or without sugar, processes the chosen option, and provides outputs indicating the preparation stages.

## Project Details

- **Module Name**: `coffee_making`
- **Language**: Verilog HDL
- **Target Devices**: Compatible with FPGA development boards.
- **Tool Versions**: Designed for use with industry-standard synthesis tools such as Genus Synthesis Solution.

## Features

The coffee-making machine supports:
1. **Espresso** (with or without sugar)
2. **Milk-based coffee** (with or without sugar)
3. **Cappuccino** (with or without sugar)

Each process includes:
- Dispensing a cup
- Adding water/milk/coffee/sugar based on the selection
- Stirring the ingredients
- Indicating when the preparation is complete

## Inputs and Outputs

### Inputs:
| Signal                  | Description                        |
|-------------------------|------------------------------------|
| `clk`                   | Clock signal for timing control.  |
| `btn_start`             | Start button selection (3 bits).  |
| `Espresso_without_sugar`| Selection for espresso (no sugar).|
| `Espresso_with_sugar`   | Selection for espresso (with sugar).|
| `Milk_without_sugar`    | Selection for milk (no sugar).    |
| `Milk_with_sugar`       | Selection for milk (with sugar).  |
| `Cappuccino_without_sugar` | Selection for cappuccino (no sugar).|
| `Cappuccino_with_sugar` | Selection for cappuccino (with sugar).|
| `rst`                   | Reset signal.                    |

### Outputs:
| Signal      | Description                            |
|-------------|----------------------------------------|
| `cup`       | Dispenses a cup.                      |
| `water`     | Dispenses water.                      |
| `milk`      | Dispenses milk.                       |
| `coffee`    | Dispenses coffee.                     |
| `sugar`     | Dispenses sugar.                      |
| `stirrer`   | Activates the stirrer.                |
| `finish`    | Indicates that coffee preparation is complete.|

## States and Functionality

The module uses a finite state machine (FSM) with the following states:
- **State 0**: Dispenses the cup.
- **State 1**: Adds the main ingredient (coffee or milk).
- **State 2**: Adds sugar (if selected).
- **State 3**: Stirs the ingredients.
- **State 4**: Marks the preparation as finished.

Each state operates on a timer (`timer`) to simulate delays for realistic preparation times.

## Setup Constraints

### Clock and Timing
- Clock frequency: Ensure timing constraints meet the setup requirements for `clk`.
- Example timing violation: Setup check with pin `timer_reg[9]/CK->D` shows a slack of `-524 ps`. Adjust clocking or synthesis constraints as needed to resolve.

### Input Delay
- Input delay constraints: `700 ps`.

### Area and Wireload
- Area mode: Timing library.
- Wireload mode: Enclosed.

## Revision History

- **Revision 0.01**: Initial implementation of the module with basic functionality.

## How to Use

1. **Load the Module**: Integrate the `coffee_making` module into your Verilog project.
2. **Set Inputs**: Use the `btn_start` and corresponding input signals to select a coffee type.
3. **Observe Outputs**: Monitor output signals (`cup`, `water`, etc.) to track the preparation stages.

## License

This project is open for educational and personal use. For commercial applications, please contact the author.

## Additional Comments

- This module was generated and synthesized using Genus Synthesis Solution. Further optimizations may be required for specific hardware.
- For detailed constraints and synthesis adjustments, refer to the generated `constraints.sdc` file.

---

*Created on: 14th February 2024*
