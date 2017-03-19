# Folder Monitor (WatchService) 

## File change notification example with Watch Service API
Java 7 adds a new feature for its NIO package called Watch Service API which allows applications monitoring directories and files for change events such as creation, deletion and modification. The Watch Service API is fairly simple to use, and relieves programmers from using third party libraries for files change monitoring. In this article, we’ll see how to use this API in the simplest form with a simple demo program. All interfaces and classes in the Watch Service API can be found in the package `java.nio.file`.


First, create a new `WatchService` object like this:

```java
WatchService watcher = FileSystems.getDefault().newWatchService();
```

Then register this `WatchService` for a given directory like the following:

```java
Path dir = Paths.get("Path/To/Watched/Directory");
dir.register(watcher, ENTRY_CREATE, ENTRY_DELETE, ENTRY_MODIFY);
```


The `register()` method of the Path class takes a `WatchService` object and a varargs list of event types which the application needs to get notified. The supported event types are:
* ENTRY_CREATE: indicates that a directory or file is created.
* ENTRY_DELETE: indicates that a directory or file is deleted.
* ENTRY_MODIFY: indicates that a directory or file is modified.
* OVERFLOW: indicates that the event might have been lost or discarded. This event is always implicitly registered so we don’t need to explicitly specify it in the `register()` method.
All these event types are declared in the java.nio.file.StandardWatchEventKinds class.

#### NOTES: 
The Watch Service API does not allow registering an individual file. We’ll get a `java.nio.file.NotDirectoryException` if trying to do so.


### Setup

provide following:

```java
//provide a path of folder
 Path dir = Paths.get("C:\\Users\\PiyushMittal\\Desktop\\garbage");
```
 

### Maven

no external dependency is required to run the program.
only `java1.7` is required.


the following code in main is used to run the sending mail.

```java
	Main.java
```


references:
 [**File change notification example with Watch Service API**](http://www.codejava.net/java-se/file-io/file-change-notification-example-with-watch-service-api)
