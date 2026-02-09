# Solution: Celsius to Fahrenheit

## Complete Runnable Code

```rust
fn celsius_to_fahrenheit(celsius: f64) -> f64 {
    (celsius * 9.0 / 5.0) + 32.0
}

fn fahrenheit_to_celsius(fahrenheit: f64) -> f64 {
    (fahrenheit - 32.0) * 5.0 / 9.0
}

fn main() {
    // Common temperature conversions
    println!("Temperature Conversion Table");
    println!("{:>10} °C | {:>10} °F", "Celsius", "Fahrenheit");
    println!("{}", "-".repeat(26));
    
    let celsius_values = [-40.0, -20.0, 0.0, 10.0, 20.0, 25.0, 30.0, 37.0, 100.0];
    
    for c in celsius_values {
        let f = celsius_to_fahrenheit(c);
        println!("{:>10.1} °C | {:>10.1} °F", c, f);
    }
    
    // Verify the reverse conversion
    println!("\n--- Verification ---");
    let original = 25.0;
    let converted = celsius_to_fahrenheit(original);
    let back = fahrenheit_to_celsius(converted);
    println!("{} °C → {} °F → {} °C", original, converted, back);
    
    // Famous temperatures
    println!("\n--- Notable Temperatures ---");
    println!("Water freezes: {} °C = {} °F", 0.0, celsius_to_fahrenheit(0.0));
    println!("Water boils: {} °C = {} °F", 100.0, celsius_to_fahrenheit(100.0));
    println!("Body temp: {} °C = {} °F", 37.0, celsius_to_fahrenheit(37.0));
    println!("Same value: {} °C = {} °F", -40.0, celsius_to_fahrenheit(-40.0));
}
```

## How It Works

### The Formula

```
°F = (°C × 9/5) + 32

or equivalently:

°F = (°C × 1.8) + 32
```

### Step-by-Step Calculation

```
Convert 25°C to Fahrenheit:

Step 1: Multiply by 9/5 (or 1.8)
        25 × 1.8 = 45

Step 2: Add 32
        45 + 32 = 77

Result: 25°C = 77°F ✓
```

### Why This Formula?

The scales have different:
- **Zero points**: 0°C = freezing water, 0°F = salt/ice mixture
- **Scale sizes**: 100°C span = 180°F span (so 1°C = 1.8°F)

```
Celsius:    0 °C -------- 100 °C
            |              |
            |  (180 units) |
            |              |
Fahrenheit: 32 °F -------- 212 °F
```

### Visual Relationship

```
        °C     °F
        ───    ───
       100 ── 212  (boiling)
        37 ── 98.6 (body temp)
        25 ── 77   (room temp)
        20 ── 68
        10 ── 50
         0 ── 32   (freezing)
       -18 ── 0
       -40 ── -40  (same value!)
```

### The Magic Number: -40

At -40°, both scales are equal!
```
(-40 × 9/5) + 32 = -72 + 32 = -40 ✓
```

### Precision in Rust

Using `f64` (64-bit float) gives us plenty of precision:

```rust
// f64 has ~15-16 decimal digits of precision
let precise = celsius_to_fahrenheit(37.0);
println!("{}", precise);  // 98.60000000000001

// For display, round appropriately
println!("{:.1}", precise);  // 98.6
```

## Complexity Analysis

- **Time Complexity**: O(1) - Just arithmetic operations
- **Space Complexity**: O(1) - No extra space needed
