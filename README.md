# Reflection

This module introduces the basics of “Reflection” – mechanism allowing to obtain type information at runtime. Practical task includes implementation and usage of a custom attribute, as well as creation of a simple “plugin” application.

## Questions for the self-check:

1. What is reflection in .NET? 

2. What does reflection allow you to do? 

3. What are fully qualified type names? 

4. What examples of practical application of reflection can you imagine? 

5. Is it possible to get information about private fields/methods using reflection?


### Tasks 1: 

Create a console application which demonstrates the use of a custom attribute. 

Attribute should allow to read/write a configuration value via at least two configuration providers: 

FileConfigurationProvider and ConfigurationManagerConfigurationProvider, which would allow to get/store a setting value in a custom file and app.config (appsettings.json) respectively. 

It could be a single attribute ConfigurationItemAttribute with parameters:

* settingName, providerType (File, Configuration Manager); 

or multiple attributes: 

* FileConfigurationItemAttribute, ConfigurationManagerConfigurationItemAttribute. 

Any other settings providers are also acceptable, even instead of proposed ones (File / Configuration Manager). 


Requirements: 

1. Created attribute(s) should be applicable only to properties.

2. Attributes usage should be implemented in a base class (ConfigurationComponentBase) of a class where the attribute was applied. 

3. Attribute should allow to read/write setting values of basic types: int, float, string, TimeSpan.

4. Reading / Writing of the settings could be initiated either by a method used in Set / Get parts of the property, or, as a simpler approach, by the methods of the base class (ConfigurationComponentBase): 

    * SaveSettings, LoadSettings, which will be invoked externally.


### Task 2: 

Required modification of the application from task 1. 

Move the implementation of the configuration providers (FileConfigurationProvider, ConfigurationManagerConfigurationProvider) into separate assembly files (dll projects) connected to the application as plugins via reflection. 

Attributes themselves could be left in the application project (for easier usage), but the logic related to the specific settings storage should be moved into separate assemblies. 

## Self-study Materials

* [“Reflection in .NET” theory from docs.microsoft.com](https://docs.microsoft.com/en-us/dotnet/framework/reflection-and-codedom/reflection)
* [Assembly Class related theory from docs.microsoft.com](https://docs.microsoft.com/en-us/dotnet/api/system.reflection.assembly) 
* [LinkedIn Course (1h 20m) – CLR Reflection for Developers](https://www.linkedin.com/learning/clr-reflection-for-developers)
* [Example of an attribute implementation / usage](https://www.tutorialspoint.com/csharp/csharp_reflection.htm)
* [Example of a plugin-based application in .NET Core](https://docs.microsoft.com/en-us/dotnet/core/tutorials/creating-app-with-plugin-support)
* [A short (9 min) YouTube video with an example of plugin-based application](https://www.youtube.com/watch?v=vZqNLPEqNXQ)
* [“Configuration.Save Method” - example of reading settings from app.config file](https://docs.microsoft.com/en-us/dotnet/api/system.configuration.configurationmanager.appsettings)
* [“Configuration.Save Method” - example of saving settings via Configuration Manager](https://docs.microsoft.com/en-us/dotnet/api/system.configuration.configuration.save)
