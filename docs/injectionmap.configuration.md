InjectionMap.Configuration is a small extension to InjectionMap that allows the definition of mappings in the application configuration file. The definition of mappings is created with xml based late binding.

# Usage
------------------------------

```csharp
public interface IContractOne { }
public interface IContractTwo 
{
	IContractOne Contract{ get; set; }
}

public class ObjectTypeOne : IContractOne { }
public class ObjectTypeTwo : IContractTwo 
{ 
	// Property for PropertyInjection
	public IContractOne Contract { get; set; }
}
```
Define the mappings in the config file.
```csharp
<configuration>
  <configSections>
    <!-- Define the section -->
    <section name="injectionMap" type="InjectionMap.Configuration.InjectionMapSection, InjectionMap.Configuration" />
  </configSections>

  <injectionMap>
    <mappings>
      <!-- Map IContractOne to ObjectTypeOne -->
      <map contract="TestApp.IContractOne, TestApp" mappedType="TestApp.ObjectTypeOne, TestApp"/>
      <!-- Map ObjectTypeOne to self -->
      <map contract="TestApp.ObjectTypeOne, TestApp" toSelf="true"/>
      <!-- PropertyInjection -->
      <map contract="TestApp.IContractTwo, TestApp" mappedType="TestApp.ObjectTypeTwo, TestApp">
	      <properties>
		      <!-- The property "Contract" will be resolved and injected -->
	          <property name="Contract"/>
	      </properties>
      </map>
    </mappings>
    <initializers>
      <!-- Register MapInitializers -->
      <init contract="TestApp.InjectionMapInitializer, TestApp"/>
    </initializers>
  </injectionMap>
</configuration>
```
The Section has to be called "injectionMap" for InjectionMap to find it.
Import the namespace InjectionMap.Configuration and create a instance of MapInitializer. To initialize the configuration just call the extensionmethod Initialize() on MapInitializer. This call should only be made once per AppDomain, ideally in the application startup.
```csharp
using InjectionMap;
...

using (var mapper = new MapInitializer())
{
    mapper.Initialize();
}
```
## Installation
------------------------------
InjectionMap.Configuration can be installed from [NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) through the package manager console:  

    PM > Install-Package InjectionMap.Configuration