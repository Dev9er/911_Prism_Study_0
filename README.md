# PrismStudy
[1]: 01-BootstrapperShell/
[Bootstrapper and the Shell][1] | Create a basic bootstrapper and shell
- App.xaml
    - Application x:Class="BootstrapperShell.App"
- App.xaml.cs
    - App : Application
        - OnStartUp
            var bootstrapper = new Bootstrapper();
            bootstrapper.Run();
- Bootstrapper.cs
    - Bootstrapper : PrismBootstrapper
        - CreateShell()
            return Container.Resolve<MainWindow>();
        - RegisterTypes(IContainerRegistery containerRegistry)
- MainWindow.xaml
    - Windows x:Class="BootstrapperShell.Views.MainWindow"
- MainWindow.xaml.cs
    - MainWindow : Window
- App.OnStartUp()
    >> RegisterTypes() >> CreateShell()
        >> MainWindow()
    >> CreateShell(): Container.Resolve<MainWindow>()
cf. Bootstrapper: Run() >> ConfigureViewModelLocator() >>
    Initialize():
    1. ContainLocator.SetContainerExtension(CreateContainerExtention)
    2. CreateModuleCatalog()
    3. RegisterRequiredTypes()
    4. RegisterTypes()
    5. ConfigureModuleCatalog
    6. _containerExtention.Resolve<RegionAdapterMappings>()
    7. ConfigureRegionAdapterMappings()
    8. ConfigureDefaultRegionBehaviors()
    9. RegisterFrameworkExceptionTypes()
    10. CreateShell()
    11. MvvmHelpers.AutowireViewModel(shell)
    12. RegionManager.SetRegionManager()
    13. RegionManager.UpdateRegions()
    14. InitializeShell()
    15. InitializeModules()

# Prism Library
## Dependency Injection
### Registering Types
- Registering Transient Services
    - containerRegistry.Register<FooService>();
    - containerRegistry.Register<IBarService, BarService>();
- Registering Singleton Services
    - containerRegistry.RegisterSingleton<FooService>();
    - containerRegistry.RegisterSingleton<IBarService, BarService>();
- Registering a Service Instance
    - containerRegistry.RegisterInstance<IFoo>(new FooImplementation());
- if (containerRegistry.IsRegistered<ISomeService>())
## Commanding

