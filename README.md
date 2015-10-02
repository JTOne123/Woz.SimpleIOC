# Woz.SimpleIOC

A compact lightweight thread safe IOC library for .NET compiled to a pertable class library with support for:
- .NET Framework 4.5
- .NET Framework 4.5.1
- .NET Framework 4.6
- ASP.NET Core 5
- Windows Universal 10
- Windows 8
- Windows Phone 8.1
- Windows Phone Silverlight 8

It provides:
- Multiple named registrations per interface or class.
- Object lifetime to create instance or singleton objects.

# Background

While this might appear to be a new project with few commits it is a recent rewrite of my personal long standing IOC library that has existed for a few years. It has been used in small and large scale projects, the largest being a set of web services that runs a company backend with 500K+ lines of code.

# Sample registrations:

// Register a singleton for an interface.
IOC.Register<IThing>(() => new thing());

//Register a named singleton for an interface.
IOC.Register<IThing>("Name", () => new thing())

//Register a named via enum singleton for an interface.
IOC.Register<IThing>(EnumType.Value, () => new thing())

// Register an instance for an interface.
IOC.Register<IThing>(ObjectLifetime.Instance, () => new thing());

// Register a named Instance for an interface.
IOC.Register<IThing>("Name", ObjectLifetime.Instance, () => new thing());

// Register with nested resolution.
IOC.Register<IThing>(() => new thing(IOC.Resolve<IList<int>()));

# Sample resolutions

// Resolve an instance.
var instance = IOC.Resolve<IThing>();

// Resolve a named instance.
var instance = IOC.Resolve<IThing>("Name");

# Other operations 

// Flush the registration list.
IOC.Clear();

