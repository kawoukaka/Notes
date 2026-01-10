# OOP Design Patterns with Real-World Examples

## Creational Patterns

### Singleton
- Intent: ensure one instance with global access.
- Real-world: configuration registry, connection pools.
- Example: Java `Runtime.getRuntime()`. https://docs.oracle.com/javase/8/docs/api/java/lang/Runtime.html

### Factory Method
- Intent: delegate object creation to subclasses.
- Real-world: framework plugins, drivers.
- Example: Java `Calendar.getInstance()`. https://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html#getInstance--

### Abstract Factory
- Intent: create families of related objects.
- Real-world: UI toolkits with themed components.
- Example: Swing `LookAndFeel` factories. https://docs.oracle.com/javase/8/docs/api/javax/swing/LookAndFeel.html

### Builder
- Intent: construct complex objects step-by-step.
- Real-world: HTTP request builders.
- Example: OkHttp `Request.Builder`. https://square.github.io/okhttp/

### Prototype
- Intent: clone objects instead of constructing anew.
- Real-world: document templates, object pooling.
- Example: Java `Cloneable` pattern. https://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html

## Structural Patterns

### Adapter
- Intent: bridge incompatible interfaces.
- Real-world: legacy API integration.
- Example: Java `InputStreamReader` adapts byte to char streams. https://docs.oracle.com/javase/8/docs/api/java/io/InputStreamReader.html

### Bridge
- Intent: separate abstraction from implementation.
- Real-world: multiple rendering backends.
- Example: JDBC bridges app code to database drivers. https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/

### Composite
- Intent: treat individual and aggregate objects uniformly.
- Real-world: UI component trees.
- Example: Swing `JComponent` containment. https://docs.oracle.com/javase/8/docs/api/javax/swing/JComponent.html

### Decorator
- Intent: add behavior dynamically.
- Real-world: stream wrappers, middleware.
- Example: Java `BufferedInputStream` wraps `InputStream`. https://docs.oracle.com/javase/8/docs/api/java/io/BufferedInputStream.html

### Facade
- Intent: simplify a complex subsystem.
- Real-world: SDKs for cloud services.
- Example: AWS SDK clients as facade. https://github.com/aws/aws-sdk-java

### Flyweight
- Intent: share common state to save memory.
- Real-world: text rendering glyphs.
- Example: Java `Integer.valueOf` caching. https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#valueOf-int-

### Proxy
- Intent: control access to another object.
- Real-world: lazy loading, access control.
- Example: Java dynamic proxies. https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Proxy.html

## Behavioral Patterns

### Chain of Responsibility
- Intent: pass request along a chain of handlers.
- Real-world: web middleware pipelines.
- Example: Servlet filters. https://docs.oracle.com/javaee/6/api/javax/servlet/Filter.html

### Command
- Intent: encapsulate request as object.
- Real-world: job queues, undo/redo.
- Example: Java `Runnable` as command. https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html

### Interpreter
- Intent: define grammar and interpret language.
- Real-world: DSLs for rules.
- Example: ANTLR parser trees. https://github.com/antlr/antlr4

### Iterator
- Intent: sequential access without exposing internals.
- Real-world: collection traversal.
- Example: Java `Iterator`. https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html

### Mediator
- Intent: centralize complex communication.
- Real-world: UI dialog coordination.
- Example: Java `EventBus` patterns (Guava). https://github.com/google/guava

### Memento
- Intent: capture and restore object state.
- Real-world: undo/rollback.
- Example: text editor snapshots (generic pattern).

### Observer
- Intent: one-to-many notifications.
- Real-world: event listeners.
- Example: Java `PropertyChangeListener`. https://docs.oracle.com/javase/8/docs/api/java/beans/PropertyChangeListener.html

### State
- Intent: change behavior when internal state changes.
- Real-world: workflow engines.
- Example: Spring state machine. https://github.com/spring-projects/spring-statemachine

### Strategy
- Intent: swap algorithms at runtime.
- Real-world: payment routing, compression choice.
- Example: Java `Comparator`. https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html

### Template Method
- Intent: define algorithm skeleton with hooks.
- Real-world: frameworks calling user code.
- Example: JUnit lifecycle methods. https://junit.org/junit4/

### Visitor
- Intent: add operations without modifying structures.
- Real-world: AST processing.
- Example: Eclipse JDT AST visitors. https://github.com/eclipse-jdt/eclipse.jdt.core
