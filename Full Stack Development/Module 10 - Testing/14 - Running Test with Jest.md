# Running Test with Jest

## NPM Commands

In a Node.js project, running tests is often managed through npm scripts defined in the `package.json` file. These scripts execute Jest commands for running tests. Tests can be categorized based on their type or focus, allowing for targeted testing.

Example of how npm commands can be structured:

- **Integration tests**: `npm run test:integration`
- **API tests**: `npm run test:api`
- **End-to-end tests**: `npm run test:e2e`
- **Run with watch mode (for development)**: `npm run test:watch`
- **Run all tests**: `npm run test`

## Running with Jest

Jest provides multiple ways to run tests, either through npm scripts or directly via command-line interfaces (CLI). Here are some common Jest commands:

- **Run tests manually**: You can execute tests manually using the Jest command, either by calling `jest path/to/file` or `npx jest path/to/file`, depending on how Jest is installed.
- **Run a single test file**: `npx jest path/to/file`
- **Run tests matching a specific name**: `npx jest -t name-of-spec`
- **Run all tests**: `npx jest`

## Watching Tests

During development, Jest can be configured to watch files for changes and automatically run tests whenever modifications are detected. This is achieved by using the `--watchAll` flag when running Jest from the command line.

## Jest Config File

Jest supports a configuration file named `jest.config.js`, where various options can be specified. These options include behaviors when tests fail, directories to search for tests, and filenames to exclude or include in testing.

## Logging Test Output

Tests should log output to the console for immediate feedback. Additionally, test results may be logged to a file in a designated logs directory. This logging behavior can be configured in the Jest config file or managed manually through npm run commands.

[YouTube video player](https://www.youtube.com/watch?v=FgnxcUQ5vho)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=FgnxcUQ5vho)
