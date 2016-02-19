InjectionMap.Wpf is a small extension to InjectionMap for WPF Applications. 
This extension allows viewmodels to be injected into the DataContext of a View (FrameworkElement).

# Usage
------------------------------
- Create a View (Usercontrol/Window/...)  
```csharp
<Window x:Class="MainWindow">
	...
</Window>
```
Create a ViewModel (A class that will be added to the DataContext)
```csharp
namespace ViewModels
{
	public class ViewModel : INotifyPropertyChanged
	{
		public ViewModel(ISettings settings)
		{
		  ...
		}
	}
}
```
Map the dependencies
```csharp
using(var mapper = new InjectionMapper())
{
      mapper.Map<ISettings, Settings>();
}
```
Bind the ViewModel to the View
```csharp
<Window x:Class="MainWindow"
		xmlns:wf="http://schemas.wickedflame.ch/2013/xaml/presentation"
        xmlns:vm="clr-namespace:ViewModels"
        wf:InjectionResolver.Resolve="{x:Type vm:ViewModel}">
		<!-- Optional Namespace for InjectionMap.Wpf: xmlns:wf="clr-namespace:InjectionMap;assembly=personalplaner.common" -->
...
</Window>
```

For ViewModels that just use the default constructor, the ViewModel does not have to be mapped to InjectionMap before resolving.
For ViewModels that need Parameters, InjectionMap will use ConstructorInjection to resolve and pass the values to the constructor.

## Installation
------------------------------
InjectionMap can be installed from [NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) through the package manager console:  

    PM > Install-Package InjectionMap.Wpf