# Portable LTspice Simulation Setup

This guide explains how to move an LTspice project from one machine to another while keeping custom libraries and symbols working correctly.

## Prerequisites

You should have:

* LTspice installed on the target machine.
* The circuit schematic file (`.asc`).
* The `Libs` folder containing all custom symbols (`.asy`) and library files (`.lib` / `.LIB`).

---

## Step 1: Copy Project Files

Copy the following items into the same project directory on the target machine:

```text
Project/
├── Circuit.asc
└── Libs/
    ├── OPAx189.LIB
    ├── OPAx192.LIB
    ├── TLE2027.LIB
    ├── lm311.lib
    └── *.asy
```

---

## Step 2: Update Symbol Files

1. Open the `Libs` folder.
2. Edit each `.asy` file using a text editor (e.g., Notepad).
3. Remove any machine-specific `SYMATTR ModelFile` entries.

Example:

```text
SYMATTR ModelFile C:\Arvind\Projects\RCU\Simulation\Complete Sim 23092025\Libs\TLE2027.LIB
```

Delete the above line and save the file.

> This path is specific to the original machine and will not work on other systems.

---

## Step 3: Verify Library Includes

Open the `.asc` schematic file and ensure it contains the required `.include` statements:

```spice
.include Libs\OPAx189.LIB
.include Libs\TLE2027.LIB
.include Libs\lm311.lib
.include Libs\OPAx192.LIB
```

Add any missing library includes as needed.

---

## Step 4: Open the Schematic

1. Launch **LTspice**.
2. Open the `.asc` file.
3. If LTspice displays messages such as:

```text
Symbol XXX.asy not found
Model XXX.LIB not found
```

don't worry—this can usually be fixed by manually placing the symbols.

---

## Step 5: Restore Missing Components

1. Open **Place Component** (`P`).
2. Navigate to the **Libs** directory.
3. Verify that the required custom components are visible.

If the components do not appear:

* Recheck **Step 2**.
* Confirm that all `.asy` files are present in the `Libs` folder.
* Verify that machine-specific paths were removed correctly.

---

## Step 6: Place Missing Symbols

For any empty or missing components in the schematic:

1. Place the correct symbol from the `Libs` folder.
2. Use the original circuit PDF, screenshot, or image as a reference.
3. Ensure all pin connections match the original design.

---

## Step 7: Configure and Run Simulation

1. Review and update simulation settings if required.
2. Save the schematic.
3. Run the simulation.

---

## Troubleshooting

### Custom Components Not Visible

* Verify `.asy` files exist in the `Libs` folder.
* Check that all `SYMATTR ModelFile` absolute paths have been removed.
* Restart LTspice after making changes.

### Library Not Found Errors

* Ensure all `.include` statements point to the correct relative path.
* Confirm that the corresponding `.LIB` files exist in the `Libs` directory.

### Missing Symbols in Schematic

* Manually place the symbols from the `Libs` folder.
* Cross-reference with the original circuit documentation.

---

## Notes

* Always use **relative paths** for portable LTspice projects.
* Keep the `.asc` file and `Libs` folder together when sharing projects.
* Avoid hardcoded machine-specific paths in `.asy` files.

## How to Import Compiled .raw to .asc 

* Make sure both the file
* Keep the `.asc` file and `.raw` files together in same directory.
* Make sure all the nets are same from .raw and .asc
* Open .asc , click on "pick visible traces icon" in the top bar, it should automatically find and open .raw
* If not manually open .raw from - File - open - .raw
* Right click and add trace - choose - net - corresponding to .asc

```
```
