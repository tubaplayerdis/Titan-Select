# Titan-Select

Titan-Select is a simple visual atuon selector that works on pros. It is has a single header file implementation and can be imported into your project with 2 small steps.

**NOTE:** Titan-Select uses **LVGL 9**. Make sure you have to latest pros version installed that supports lvgl 9 to use Titan-Select

### Adding to your project

First, download titanselect.hpp, Then, in the include directory of your pros project, create a folder called titanselect then add the titanselect.hpp file to that folder. Now, your all ready to start using Titan-Select.

### Showcase

Add pictures here.

### Features

Titan-Select is a relatively simple but has a few key features that make it great,

 - **Automatic auton saving/loading from file** - Titan-Select will automatically save/load your last used autons so you dont have to worry about an auton not running or having to reselect an auton pre-match. **(A Micro-SD has to be inserted and read/writeable for this to work)**

 - **Grid style Selector** - Titan-Selects's grid style selector makes choosing autons simple and straightforward to maximize your time writing autons instead of trying to get your auton selector to work.

### Usage

Titan-Select makes use of a macro based API to interact with the selector and register autons. The macros handle most of the work but to get started read up on the following macros:

 - **AUTON(name, routine)** - Used to register autons with the selector. Can be used in **header or source files** to define autons. 
 - **SELECTOR_INIT()** - Initializes the selector and makes it visible. Call this in your **initialize()** function!
 - **SELECTOR_RUN_SELECTED()** - Runs your selected auton. Call this in your **autonomus()** function!

**PLEASE READ** the documentation below for more info. Thanks!

---

# Titan-Select API Macros

## `AUTON(name, routine)`
**Description:**  
Defines an auton and automatically adds it to the selector. This can be used in a header or source file to declare an auton.

**Parameters:**  
- `name` — Name of the auton.  
- `routine` — Code for the auton, enclosed in curly braces `{}`.

**Example:**  
```cpp
AUTON(BlueLeft, { MoveRobot(); });
```

---

## `AUTON_RAW(name, function)`
**Description:**  
Defines an auton and automatically adds it to the selector.

**Parameters:**  
- `name` — Name of the auton.  
- `function` — C++ function matching the `void()` signature. Can be a lambda or a raw function pointer.

**Example:**  
```cpp
AUTON_RAW(BlueRight, MyAutonFunction);
```

---

## `SELECTOR_INIT()`
**Description:**  
Initializes the selector and displays it on the screen. Call this in your **initialize()** function.

**Returns:**  
 - None

---

## `SELECTOR_RUN_SELECTED()`
**Description:**  
Runs the currently selected auton. Call this in your **autonomus()** function.

**Returns:**  
 - None

---

## `SELECTOR_RUN_AUTON(auton_name)`
**Description:**  
Runs the auton with the specified name.

**Parameters:**  
- `auton_name` — Name of the auton to run as a string.

**Returns:**  
 - None
 

---

## `SELECTOR_IS_AUTON_SELECTED()`
**Description:**  
Checks if an auton is selected. Potentially call this in your **competition_initialize()** function to provide feedback on whether or not an auton is selected!

**Returns:**  
- `bool` — `true` if an auton is selected, otherwise `false`.

---

## `SELECTOR_SELECTED_AUTON_NAME()`
**Description:**  
Gets the name of the currently selected auton.

**Returns:**  
- `"No Auton"` — No auton selected.  
- *const char** — Name of the selected auton.

---

## `SELECTOR_SET_VISIBILITY(visible)`
**Description:**  
Sets the visibility of the selector. Useful for integrating with custom displays.

**Parameters:**  
- `visible` — `true` to show, `false` to hide.

**Returns:**  
 - None
 

---

## `SELECTOR_GET_SELECTOR()`
**Description:**  
Gets the active selector object.

**Returns:**  
- `selector` — Active selector object.

---

## `SELECTOR_DESTROY()`
**Description:**  
Destroys the selector object in memory. **Use with caution.**

**Returns:**  
 - None
 
---

# Titan-Select Settings

#### These settings are located inside the titanselect.hpp file and can be modified as such to modify functionality.

## `SELECTOR_ROWS`
**Description:**  
Number of rows in the auton selector.  
**Default:** `3`

## `SELECTOR_COLS`
**Description:**  
Number of columns in the auton selector.  
**Default:** `3`
