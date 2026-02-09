# Solution: Leap Year

## Complete Runnable Code

```rust
fn is_leap_year(year: i32) -> bool {
    // A year is a leap year if:
    // 1. Divisible by 4 AND
    // 2. (NOT divisible by 100) OR (divisible by 400)
    
    (year % 4 == 0) && (year % 100 != 0 || year % 400 == 0)
}

// Alternative: More readable version
fn is_leap_year_verbose(year: i32) -> bool {
    if year % 400 == 0 {
        true  // Divisible by 400 → leap year
    } else if year % 100 == 0 {
        false // Divisible by 100 but not 400 → NOT leap year
    } else if year % 4 == 0 {
        true  // Divisible by 4 → leap year
    } else {
        false // Not divisible by 4 → NOT leap year
    }
}

fn main() {
    // Test various years
    let years = [1900, 2000, 2004, 2019, 2020, 2021, 2024, 2100];
    
    println!("{:>6} | {:>10}", "Year", "Leap Year?");
    println!("{}", "-".repeat(20));
    
    for year in years {
        println!("{:>6} | {:>10}", year, is_leap_year(year));
    }
    
    // Famous leap year edge cases
    println!("\n--- Notable Examples ---");
    println!("1900: {} (divisible by 100, not 400)", is_leap_year(1900));
    println!("2000: {} (divisible by 400)", is_leap_year(2000));
    println!("2024: {} (divisible by 4, not 100)", is_leap_year(2024));
    
    // Count leap years in a range
    let leap_years: Vec<i32> = (2000..=2030)
        .filter(|&y| is_leap_year(y))
        .collect();
    println!("\nLeap years 2000-2030: {:?}", leap_years);
}
```

## How It Works

### Leap Year Rules

| Condition | Result |
|-----------|--------|
| Divisible by 400 | LEAP YEAR |
| Divisible by 100 (but not 400) | NOT leap year |
| Divisible by 4 (but not 100) | LEAP YEAR |
| Not divisible by 4 | NOT leap year |

### Decision Tree

```
                    Year
                      │
              Is year % 4 == 0?
                   /        \
                 NO          YES
                 │            │
           NOT LEAP     Is year % 100 == 0?
                           /        \
                         NO          YES
                         │            │
                    LEAP YEAR    Is year % 400 == 0?
                                    /        \
                                  NO          YES
                                  │            │
                            NOT LEAP      LEAP YEAR
```

### Examples Traced

```
Year 2024:
  2024 % 4 = 0 ✓ (divisible by 4)
  2024 % 100 = 24 (not divisible by 100)
  → LEAP YEAR ✓

Year 1900:
  1900 % 4 = 0 ✓ (divisible by 4)
  1900 % 100 = 0 (divisible by 100!)
  1900 % 400 = 300 (NOT divisible by 400)
  → NOT LEAP YEAR ✓

Year 2000:
  2000 % 4 = 0 ✓
  2000 % 100 = 0 (divisible by 100)
  2000 % 400 = 0 ✓ (divisible by 400!)
  → LEAP YEAR ✓
```

### Why These Rules?

The leap year rules correct calendar drift:
- Earth takes ~365.2422 days to orbit the sun
- Without leap years, seasons would shift
- The 100/400 rule fine-tunes the correction

| Rule | Days/Year | Error/Year |
|------|-----------|------------|
| No leap years | 365 | -0.2422 days |
| Every 4 years | 365.25 | +0.0078 days |
| Skip centuries | 365.24 | -0.0022 days |
| Keep 400ths | 365.2425 | +0.0003 days |

### The Boolean Formula Explained

```rust
(year % 4 == 0) && (year % 100 != 0 || year % 400 == 0)
```

Breaking it down:
1. `year % 4 == 0` — Must be divisible by 4
2. `year % 100 != 0` — AND not a century year
3. `year % 400 == 0` — OR a 400-year

## Complexity Analysis

- **Time Complexity**: O(1) - Just three modulo operations
- **Space Complexity**: O(1) - No extra space
