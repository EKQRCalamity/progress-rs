# progress-rs
Small rust utility for creating terminal progressbars that fit the screen.

# Usage

Copy the progress.rs to the project directory where you want to use it. You will need the termsize library.

### Examples

##### Basic Usage
```rust
// Example:
mod progress;

use std::{time, thread};
use std::time::Duration;
use progress::{ProgressBar};

fn main() {
    let mut progress_bar = ProgressBar::new("[".to_string(), "]".to_string(), "#".to_string(), "~".to_string(), 0.0, 100.0);
    loop {
        match progress_bar.show() {
            Ok(boolean_finished) => {
                if boolean_finished {
                    break;
                } else {
                    progress_bar.update_progress((progress_bar.percent() as f64) + (1 as f64));
                    thread::sleep(Duration::from_millis(20));
                }
            },
            Err(_) => panic!("Error (Shouldnt happen)")
        }
    }
}
```

##### Example in project:
If you want to see it in use in an actual project take a look at my [leecher-rs](https://github.com/EKQRCalamity/leecher-rs) repository.
