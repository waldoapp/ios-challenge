# iOS Challenge

Much of the iOS work we do at Waldo is understanding not only how an arbitrary
app is behaving at runtime, but also how it is actually built. This can include
determining on the fly which libraries and frameworks the app has loaded into
memory.

This challenge aims to give you a taste of the kind of work needed to bring
Waldo to life.

## Task

Create an iOS framework that can be linked into a simulator app. It should be
built to run on both M1 (`arm64`) and Intel (`x86_64`) simulator devices
(although you are _not_ required to actually test your solution on both
architectures). Assume a target of iOS 14 or higher.

Upon load, your framework immediately sends a log message via `os_log`
announcing its presence. It then arranges to be invoked whenever a library or
framework is _dynamically_ loaded into the app. Each time your framework is
invoked because a library or framework has been loaded into the app, it should
send a log message via `os_log` with a format similar to:

```
Loaded /path/to/SomeLibrary.dylib
Loaded /path/to/SomeFramework.framework/SomeFramework
```

> **Important:** Bear in mind that some libraries or frameworks may have been
> loaded into the app _before_ your framework is loaded, and some _after_. Your
> solution _must_ account for both of these cases, as well as the case where a
> library or framework is loaded dynamically into the app at _some future
> time_.

## Restrictions

- You may implement your solution in Swift or Objective-C.
- You _must not_ use any third-party libraries in your solution — only
  Apple-provided libraries and frameworks are acceptable.

## Bonus Points

In the README for your solution, describe how you might “inject” your framework
into an already-built app that you do not have the source code for.

## Testing

You can clone the app at https://github.com/waldoapp/TravelDemo and modify it
to link against your framework for testing purposes. Alternately, you may use
some other app for this purpose. However, you _must_ maintain your solution in
its own Xcode project for submission purposes.

Keep both Xcode projects (your framework and the app using your framework)
easily accessible; you will be needing them to develop against for a subsequent
interview.

## Submission

Create a zip archive of the folder containing your solution. Include source
code, README, Xcode project, and Makefile (or build shell script). Do _not_
include anything related to any app you may have used to test your solution.

Please send this zip archive to developers@waldo.io.
