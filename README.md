# Bin2Dec App Documentation

## Overview

The Bin2Dec app is a simple utility that converts binary numbers to decimal numbers. It is built using Vue.js with TypeScript setup and styled with Tailwind CSS.

## Features

- Accepts user input in binary format (0's and 1's).
- Validates the input to ensure it contains only valid binary digits.
- Converts the binary input to its decimal equivalent and displays the result.
- Displays error messages for invalid input.
- Includes a responsive and visually appealing user interface.

## Installation

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/ekunemmanuel/bin-dec
   ```

2. Navigate to the project directory:

   ```bash
   cd bin2dec-app
   ```

3. Install dependencies using npm:

   ```bash
   npm install
   ```

## Usage

1. Run the development server:

   ```bash
   npm run dev
   ```

2. Open your browser and navigate to http://localhost:3000 to view the app.

3. Enter a binary number (0's and 1's) in the input field and click the "Convert" button to see the decimal equivalent.

## Code Overview

### Technologies Used

- Vue.js with TypeScript setup
- Tailwind CSS for styling

### Components

- `App.vue`: Main component containing the UI elements and logic for binary to decimal conversion.
- `main.ts`: Entry point for the Vue.js application.
- `tailwind.config.js`: Tailwind CSS configuration file.

### Dependencies

- `vue@next`: Vue.js framework for building user interfaces.
- `@vue/compiler-sfc`: Vue 3 compiler for single-file components with TypeScript support.
- `tailwindcss`: Utility-first CSS framework for styling.
- `postcss`: CSS preprocessor for transforming styles with plugins.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Vue.js - [https://vuejs.org/](https://vuejs.org/)
- Tailwind CSS - [https://tailwindcss.com/](https://tailwindcss.com/)
