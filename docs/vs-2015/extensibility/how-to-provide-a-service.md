---
title: 'Postupy: poskytování služby | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e0d0425e0e931d28157439d3d8a4174f1d4961a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785908"
---
# <a name="how-to-provide-a-service"></a>Postupy: poskytování služby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage může poskytovat služby, které můžete použít jiné balíčky VSPackages. Poskytování služeb, musíte VSPackage registraci služby pomocí sady Visual Studio a přidejte službu.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Třída implementuje oba <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> a <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> obsahuje metody zpětného volání, které poskytují služby na vyžádání.  
  
 Další informace o službách najdete v tématu [základy služeb](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  VSPackage blížící se nenačte, Visual Studio čeká na všechny žádosti o služby, které poskytuje VSPackage byl dodán. Neumožňuje nové požadavky pro tyto služby. Neměli volat explicitně <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metoda odvolání přístupu služby při uvolnění.  
  
#### <a name="implementing-a-service"></a>Implementace služby  
  
1. Vytvořte projekt VSIX (**soubor / nový / Project / Visual C# / Extensiblity / projekt VSIX**).  
  
2. Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumníka řešení** a klikněte na tlačítko **přidat / nová položku / položky Visual C# / rozšiřitelnost / balíček Visual Studio**.  
  
3. K implementaci služby, je potřeba vytvořit tři typy:  
  
   - Rozhraní, který popisuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že mají žádné metody.  
  
   - Rozhraní, které popisují rozhraní služby. Toto rozhraní obsahuje metody k implementaci.  
  
   - Třída, která implementuje služba a služba rozhraní.  
  
     Následující příklad ukazuje velmi základní implementaci ze tří typů. Konstruktor třídy služeb, musíte nastavit poskytovatele služeb.  
  
   ```csharp  
   public class MyService : SMyService, IMyService  
   {  
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
       private string myString;  
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
       {  
           Trace.WriteLine(  
                  "Constructing a new instance of MyService");  
           serviceProvider = sp;  
       }  
       public void Hello()  
       {  
           myString = "hello";  
       }  
       public string Goodbye()  
       {  
          return "goodbye";  
       }  
   }  
   public interface SMyService  
   {  
   }  
   public interface IMyService  
   {  
       void Hello();  
       string Goodbye();  
   }  
  
   ```  
  
### <a name="registering-a-service"></a>Registrace služby  
  
1.  Chcete-li zaregistrovat služby, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage, která poskytuje služby. Tady je příklad:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Tento atribut zaregistruje `SMyService` pomocí sady Visual Studio.  
  
    > [!NOTE]
    >  Pokud chcete zaregistrovat službu, která nahrazuje jinou se stejným názvem, použijte <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Poznámka: Tento pouze jedno přepsání služby je povolen.  
  
### <a name="adding-a-service"></a>Přidání služeb  
  
1.  1.  V inicializátoru VSPackage přidat služby a přidejte metodu zpětného volání pro vytvoření služeb. Tady je změnit tak, aby <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementace metody zpětného volání, které by měl vytvořit a vrátit služby nebo hodnota null, pokud nelze vytvořit.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio může odmítnout žádost o poskytování služeb. Dělá to, pokud jiné VSPackage již poskytuje službu.  
  
3.  Nyní můžete získat službu a použijte její metody. Ukážeme to v inicializátoru, ale můžete získat službu kamkoli chcete používat službu.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Hodnota `helloString` by měl být "Hello".  
  
## <a name="see-also"></a>Viz také  
 [Postupy: získání služby](../extensibility/how-to-get-a-service.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)

