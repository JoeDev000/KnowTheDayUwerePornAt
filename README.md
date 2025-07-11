# Day U Were Born At Calculator Tool 📅

A simple C++ console tool that determines what day of the week you were born on using **Zeller's Congruence** algorithm.

## Sample Output 📊

```
--------------------------------
Konw The Day You Were Porn At :3
--------------------------------
Entre Your date of birth
Entre your birth Year: 2005

Entre your birth Month: 8

Entre your birth Day: 10

You were porn at Wednesday, Welcome To Life :)
```

## Algorithm Details 🔬

This program uses **Zeller's Congruence**, a mathematical algorithm developed by Christian Zeller in 1882 to calculate the day of the week for any given date.

### Zeller's Congruence Formula

The algorithm is implemented in the `caclulate_ordre()` function:

```cpp
short caclulate_ordre(short year, short month, short day) {
    int a, m, y;
    a = (14 - month) / 12;
    y = year - a;
    m = month + 12*a - 2;
    return (day + y + (y / 4) - (y / 100) + (y / 400) + ((31 * m) / 12)) % 7;
}
```

### Formula Breakdown

The mathematical formula used is:
```
h = (q + ⌊13(m+1)/5⌋ + K + ⌊K/4⌋ + ⌊J/4⌋ - 2J) mod 7
```

Where:
- **h** = day of week (0 = Saturday, 1 = Sunday, 2 = Monday, ..., 6 = Friday)
- **q** = day of month
- **m** = month (3 = March, 4 = April, ..., 14 = February)
- **K** = year of century (year mod 100)
- **J** = zero-based century (⌊year/100⌋)

### Implementation Translation

In our code:
- `a = (14 - month) / 12` → Adjusts for January and February being counted as months 13 and 14 of the previous year
- `y = year - a` → Adjusts the year if month is January or February
- `m = month + 12*a - 2` → Converts month to Zeller's month system
- The main formula: `(day + y + (y / 4) - (y / 100) + (y / 400) + ((31 * m) / 12)) % 7`

### Why This Algorithm Works

1. **Leap Year Handling**: The terms `(y / 4) - (y / 100) + (y / 400)` account for leap years in the Gregorian calendar
2. **Month Adjustment**: January and February are treated as months 13 and 14 of the previous year to simplify leap year calculations
3. **Century Correction**: The algorithm accounts for the peculiarities of the Gregorian calendar system
4. **Modular Arithmetic**: Using `% 7` gives us the day of the week (0-6)

### Day Mapping

The result is mapped to days as follows:
```cpp
string days[] {"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"};
```

Note: The algorithm returns 0-6, where 0 corresponds to Sunday in this implementation.

## Technical Details 🔧

### Core Functions

- **Input Validation**: `readYear()`, `readMonth()`, `readDay()` ensure valid date inputs
- **Zeller's Algorithm**: `caclulate_ordre()` implements the mathematical formula
- **Day Conversion**: `getDayUwerePornAt()` converts the numeric result to day name

### Data Flow

1. User inputs birth date (year, month, day)
2. Date is validated for basic ranges
3. Zeller's Congruence algorithm calculates day of week
4. Numeric result is converted to day name
5. Result is displayed to user

## Requirements 📋

- **C++ Compiler**: GCC, Clang, or Visual Studio
- **C++ Standard**: C++11 or later
- **Operating System**: Windows only (uses Windows-specific system commands)

## Compilation Instructions 🔨

### Windows Only
```bash
# Using MinGW
g++ -o day_calculator.exe day_calculator.cpp
```
or click at the '.exe' file in the exe\ folder

## Algorithm Accuracy 📊

Zeller's Congruence is mathematically proven and works for:
- **Gregorian Calendar**: Years 1583 onwards (when Gregorian calendar was adopted)
- **Julian Calendar**: Earlier dates with modification
- **All Valid Dates**: No date range limitations within the calendar system

## Known Limitations ⚠️

1. **Windows Only**: Uses Windows-specific system commands (`system("cls")` and `system("pause>0")`)
2. **No Cross-Platform Support**: Will not run on Linux or macOS without code modifications
3. **Input Validation**: Basic range checking only (doesn't validate impossible dates like Feb 30)
4. **Language**: Contains spelling errors in output text
5. **Day Names**: Contains typos in day names array ("Tusday", "Thurthday")

## Mathematical Background 📚

**Zeller's Congruence** is based on the mathematical properties of the Gregorian calendar:
- Accounts for the 400-year cycle of the Gregorian calendar
- Handles leap years correctly
- Compensates for the irregular month lengths
- Uses modular arithmetic to determine the day of the week

The algorithm is widely used in computer science and mathematics for date calculations due to its accuracy and efficiency.

## Author 👨‍💻

**Joe Ali**  
Software Developer & Open Source Programmer

## License 📄

This project is open source. Feel free to use, modify, and distribute as needed.

---

*Thanks for using this program! 😊*