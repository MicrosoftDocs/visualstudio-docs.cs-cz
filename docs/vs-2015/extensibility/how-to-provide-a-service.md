---
title: 'Postupy: poskytování služby | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802742"
---
# <a name="how-to-provide-a-service"></a>Postupy: Poskytování služby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage může poskytovat služby, které mohou používat jiné sady VSPackage. Aby bylo možné poskytnout službu, VSPackage musí službu zaregistrovat v aplikaci Visual Studio a přidat službu.  
  
 <xref:Microsoft.VisualStudio.Shell.Package>Třída implementuje i <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> obsahuje metody zpětného volání, které poskytují služby na vyžádání.  
  
 Další informace o službách najdete v tématu [základy služby](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> Když se chystá uvolnění VSPackage, Visual Studio počká, dokud nebudou doručeny všechny žádosti o služby, které VSPackage nabízí. Nepovoluje nové požadavky na tyto služby. Nevolejte explicitně <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodu pro odvolání služby při uvolňování.  
  
#### <a name="implementing-a-service"></a>Implementace služby  
  
1. Vytvořte projekt VSIX (**soubor/nový/projekt/Visual C#/Extensiblity/VSIX projekt**).  
  
2. Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumník řešení** a klikněte na **přidat/nová položka/Visual C# položky/rozšiřitelnost/balíček sady Visual Studio**.  
  
3. Chcete-li implementovat službu, je nutné vytvořit tři typy:  
  
   - Rozhraní, které popisuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody.  
  
   - Rozhraní, které popisuje rozhraní služby. Toto rozhraní zahrnuje metody, které mají být implementovány.  
  
   - Třída, která implementuje službu i rozhraní služby.  
  
     Následující příklad ukazuje velmi základní implementaci tří typů. Konstruktor třídy služby musí nastavit poskytovatele služby.  
  
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
  
1. Chcete-li zaregistrovat službu, přidejte do balíčku <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage, který poskytuje službu. Tady je příklad:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Tento atribut se registruje `SMyService` v aplikaci Visual Studio.  
  
    > [!NOTE]
    > Chcete-li zaregistrovat službu, která nahrazuje jinou službu se stejným názvem, použijte <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Všimněte si, že je povoleno pouze jedno přepsání služby.  
  
### <a name="adding-a-service"></a>Přidání služby  
  
1. 1.  Do inicializátoru VSPackage přidejte službu a přidejte metodu zpětného volání, která vytvoří služby. Tady je změna, která se má provést v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodě:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Implementujte metodu zpětného volání, která by měla vytvořit a vrátit službu, nebo hodnotu null, pokud ji nelze vytvořit.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio může odmítnout žádost o poskytování služby. To znamená, že pokud již služba podporuje jiný VSPackage.  
  
3. Nyní můžete získat službu a použít její metody. Tato možnost se zobrazí v inicializátoru, ale můžete ji získat kdekoli, kde chcete službu používat.  
  
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
  
     Hodnota `helloString` by měla být "Hello".  
  
## <a name="see-also"></a>Viz také  
 [Postupy: získání služby](../extensibility/how-to-get-a-service.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)
