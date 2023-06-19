# progress-rs
Small rust utility for creating terminal progressbars that fit the screen.

# Usage

Copy the progress.rs to the project directory where you want to use it. You will need the termsize library.

```rust
// Example:
fn main() {
    let mut progress_bar = ProgressBar::new(true, "[".to_string(), "]".to_string(), "#".to_string(), "~".to_string(), 0.0, 0.0, 100.0);
    loop {
        match progress_bar.show() {
            Ok(boolean_finished) => {
                if boolean_finished {
                    break;
                } else {
                    progress_bar.update_progress((progress_bar.percent() as f64) + (1 as f64));
                }
            },
            Err(_) => panic!("Error (Shouldnt happen)")
        }
    }
}

```