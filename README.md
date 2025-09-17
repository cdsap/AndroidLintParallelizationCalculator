# Android Lint Parallelization Calculator

A web-based calculator tool for determining optimal parallelization settings for Android Lint tasks in Gradle builds. This tool helps developers understand how the `LintParallelBuildService` class limits parallelization and calculate the maximum number of parallel lint tasks for different configurations.

## 🌐 Live Demo

**Try it now**: [https://cdsap.github.io/AndroidLintParallelizationCalculator/](https://cdsap.github.io/AndroidLintParallelizationCalculator/)

**Reference**: [LintParallelBuildService.kt](https://cs.android.com/android-studio/platform/tools/base/+/mirror-goog-studio-main:build-system/gradle-core/src/main/java/com/android/build/gradle/internal/services/LintParallelBuildService.kt;l=36)

## 🚀 Features

- **Two Calculation Modes**:
  - **In-Process Mode**: Calculates workers based on Gradle daemon heap size
  - **Out-of-Process Mode**: Calculates workers based on total physical memory
- **Real-time Calculations**: Instant updates as you modify parameters
- **Visual Feedback**: Interactive sliders, progress indicators, and memory diagrams
- **Formula Display**: Shows the exact Kotlin calculation formulas used
- **Responsive Design**: Works on desktop and mobile devices
- **Dark Theme**: Modern, developer-friendly interface

## 📖 Background

The `LintParallelBuildService` class in Android's build system limits the parallelization of Lint tasks to prevent memory issues. This calculator helps you understand and optimize these limits for your specific build environment.

## 🎯 Usage

### In-Process Mode
Calculates parallel workers based on the Gradle daemon heap size:
- **Formula**: `floor(currentGBHeap × 0.75 / lintReservedPerLint)`
- Uses 75% of the Gradle daemon heap for lint tasks
- Reserves memory per lint task as specified

### Out-of-Process Mode
Calculates parallel workers based on total physical memory:
- **Formula**: `Math.floorDiv(totalPhysicalMemory, lintHeapSize) - 2`
- Reserves space for Gradle and Kotlin daemons
- Can use either property-based or heap-based lint memory allocation

## 🛠️ Technology Stack

- **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **No Dependencies**: Self-contained, no external frameworks
- **Styling**: Custom CSS with CSS Grid, Flexbox, and custom properties
- **Architecture**: Single-page application with modular JavaScript

## 📁 Project Structure

```
lint_calculaotr/
├── index.html          # Main application file
└── README.md          # This file
```

## 🚀 Getting Started

1. **Try the live demo**: [https://cdsap.github.io/AndroidLintParallelizationCalculator/](https://cdsap.github.io/AndroidLintParallelizationCalculator/)
2. **Or clone locally**: Download/clone this repository and open `index.html` in your browser
3. **Select** your calculation mode (In-Process or Out-of-Process)
4. **Configure** the parameters for your build environment
5. **View** the calculated results and formula breakdown

## ⚙️ Configuration Parameters

### In-Process Mode
- **Current Gradle daemon heap size**: Heap size allocated to the Gradle daemon
- **Memory reserved per lint task**: Memory allocated per parallel lint task
- **Maximum workers in project**: Project-wide worker limit

### Out-of-Process Mode
- **Total Physical Memory**: Available RAM in the build environment
- **Lint Heap Size**: Memory per lint task (property or heap-based)
- **Maximum workers in project**: Project-wide worker limit

## 🎨 Features in Detail

### Interactive Controls
- **Number inputs** with unit selectors (GB, MB)
- **Visual sliders** with real-time feedback
- **Radio button groups** for configuration options
- **Toggle switches** for mode selection

### Visualizations
- **Memory diagrams** showing process layout
- **Calculation steps** with detailed formulas
- **Progress indicators** for parameter ranges
- **Warning indicators** for configuration issues

### Responsive Design
- **Mobile-friendly** layout with adaptive grids
- **Touch-friendly** controls and interactions
- **Accessible** with proper ARIA labels and keyboard navigation

## 🔧 Customization

The application uses CSS custom properties for easy theming:

```css
:root {
  --bg: #0b0f14;          /* Background color */
  --card: #121821;        /* Card background */
  --text: #e8eef5;        /* Text color */
  --accent: #7dd3fc;      /* Primary accent */
  --accent-2: #86efac;    /* Secondary accent */
  --warn: #f0abfc;        /* Warning color */
}
```

## 📱 Browser Compatibility

- **Chrome** 60+
- **Firefox** 55+
- **Safari** 12+
- **Edge** 79+

## 🤝 Contributing

This is a simple, self-contained tool. If you'd like to contribute:

1. Fork the repository
2. Make your changes
3. Test in multiple browsers
4. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🔗 Related Resources

- [Android Lint Documentation](https://developer.android.com/studio/write/lint)
- [Gradle Build Performance](https://docs.gradle.org/current/userguide/performance.html)
- [Android Build System](https://developer.android.com/studio/build)

---

**Note**: This calculator is based on the actual Android build system implementation and should provide accurate results for most build environments. However, always verify the calculations against your specific setup and requirements.
