# Reflection

Questions for the self-check:

What is reflection in .NET? 

What does reflection allow you to do? 

What are fully qualified type names? 

What examples of practical application of reflection can you imagine? 

Is it possible to get information about private fields/methods using reflection?


# Tasks 1: 

Create a console application which demonstrates the use of a custom attribute. 

Attribute should allow to read/write a configuration value via at least two configuration providers: 

FileConfigurationProvider and ConfigurationManagerConfigurationProvider, which would allow to get/store a setting value in a custom file and app.config (appsettings.json) respectively. 

It could be a single attribute ConfigurationItemAttribute with parameters:

settingName, providerType (File, Configuration Manager); or multiple attributes: 

FileConfigurationItemAttribute, ConfigurationManagerConfigurationItemAttribute. 

Any other settings providers are also acceptable, even instead of proposed ones (File / Configuration Manager). 


Requirements: 

1. Created attribute(s) should be applicable only to properties.

2. Attributes usage should be implemented in a base class (ConfigurationComponentBase) of a class where the attribute was applied. 

3. Attribute should allow to read/write setting values of basic types: int, float, string, TimeSpan.

4. Reading / Writing of the settings could be initiated either by a method used in Set / Get parts of the property, or, as a simpler approach, by the methods of the base class (ConfigurationComponentBase): 

SaveSettings, LoadSettings, which will be invoked externally.


# Task 2: 

Required modification of the application from task 1. 

Move the implementation of the configuration providers (FileConfigurationProvider, ConfigurationManagerConfigurationProvider) into separate assembly files (dll projects) connected to the application as plugins via reflection. 

Attributes themselves could be left in the application project (for easier usage), but the logic related to the specific settings storage should be moved into separate assemblies. 
