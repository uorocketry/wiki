The [spdlog library](https://github.com/gabime/spdlog) is used for logging informational and error messages in the rocket-code. At the time of writing, it has been configured to log to a file and the console.

## Usage

The simplest way to log is to use the following macros. These will log to the default logger.
```c++
SPDLOG_TRACE("A trace message");
SPDLOG_DEBUG("A debug message");
SPDLOG_INFO("A info message");
SPDLOG_WARN("A warning message");
SPDLOG_ERROR("A error message");
SPDLOG_CRITICAL("A critical message");
```

However, if it is a section of the code that is logging often, using the above macros could slow down the application. Therefore, it could be better to do get an instance of the logger manually:

```c++
// In a class, the following line should be in the constructor and `logger` should be an instance variable.
auto logger = spdlog::default_logger();

// Now the following can be used when we need to log
SPDLOG_LOGGER_TRACE(logger, "A trace message");
SPDLOG_LOGGER_DEBUG(logger, "A debug message");
SPDLOG_LOGGER_INFO(logger, "A info message");
SPDLOG_LOGGER_WARN(logger, "A warning message");
SPDLOG_LOGGER_ERROR(logger, "A error message");
SPDLOG_LOGGER_CRITICAL(logger, "A critical message");
```

### Methods to avoid

Note that there are other methods to log, like the following:
```c++
auto logger = spdlog::default_logger();
	
logger->info("Try to avoid this.")
```
However, with the above code, the file and line number will not be logged. Therefore, it is better to use macros instead.


## Logging levels

The following levels are supported by spdlog:
- Critical
  * An extremely catastrophic situation. The application is in an unrecoverable state and is about to abort.
- Error
  * A serious issue and represents the failure of some important part of the application. However, this is not a fatal error and the application is able to continue working.
- Warning
  * Indicates the application *might* have a problem and that it is in an unusual situation.
- Info
  * Provide information about normal behaviour and milestones.
- Debug
  * Diagnostic information. This is probably more detailed information than necessary in normal 'production' situations.
- Trace
  * Extremely fine-grained information. Would be used to capture every single detail of the application.

*The logging levels' description is inspired from https://www.scalyr.com/blog/logging-levels/. Go see that website for more details.*

Using those logging levels allows changing how fine-grained the information is in the logs. For example, while using running the code at the competition, we might only want Info messages and up. However, if we are trying to debug an issue, we might want all message levels.

### Backtrace

spdlog supports backtrace. This allows us to dump a certain configurable number of past messages when needed, say if we encounter an error. The dump can include debug and trace messages, even if those levels are not logged normally.
To use the feature, simply add the following line when a backtrace dump is needed:
```c++
// e.g. if some error happened:
spdlog::dump_backtrace(); // log the last messages
```

## More information

See the spdlog documentation for more information on how to use it: https://github.com/gabime/spdlog/wiki
