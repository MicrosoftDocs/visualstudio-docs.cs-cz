---
title: 'Postup: Poskytnutí služby | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710776"
---
# <a name="how-to-provide-a-service"></a>Postup: Poskytnutí služby
VSPackage může poskytovat služby, které mohou používat jiné balíčky VSPackages. Chcete-li poskytovat službu, VSPackage musí zaregistrovat službu s Visual Studio a přidat službu.

 Třída <xref:Microsoft.VisualStudio.Shell.Package> implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer>oba a . <xref:System.ComponentModel.Design.IServiceContainer>obsahuje metody zpětného volání, které poskytují služby na vyžádání.

 Další informace o službách naleznete v [tématu Service essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Při VSPackage se chystá uvolnit, Visual Studio čeká, dokud všechny požadavky na služby, které poskytuje VSPackage byly dodány. Neumožňuje nové požadavky pro tyto služby. Neměli byste explicitně volat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> odvolat službu při uvolnění.

## <a name="implement-a-service"></a>Implementace služby

1. Vytvořte projekt VSIX **(Soubor** > **nového** > **projektu** > Visual**C#** > **Rozšiřitelnost** > **VSIX project).**

2. Přidejte VSPackage do projektu. V průzkumníku **řešení** vyberte uzel projektu a klepněte na tlačítko **Přidat** > **novou položku** > **Visual C# Položky** > **rozšiřitelnost** > **visual studio balíček**.

3. Chcete-li implementovat službu, musíte vytvořit tři typy:

   - Rozhraní, které popisuje službu. Mnoho z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody.

   - Rozhraní, které popisuje rozhraní služby. Toto rozhraní zahrnuje metody, které mají být implementovány.

   - Třída, která implementuje službu a rozhraní služby.

     Následující příklad ukazuje základní implementaci těchto tří typů. Konstruktor třídy služby musí nastavit poskytovatele služeb.

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

### <a name="register-a-service"></a>Registrace služby

1. Chcete-li zaregistrovat <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> službu, přidejte do Balíčku VSPackage, který poskytuje službu. Zde naleznete příklad:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Tento atribut `SMyService` se registruje v sadě Visual Studio.

    > [!NOTE]
    > Chcete-li zaregistrovat službu, která nahradí jinou službu se stejným názvem, použijte <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Všimněte si, že je povoleno pouze jedno přepsání služby.

### <a name="add-a-service"></a>Přidat službu

1. V Inicializátoru VSPackage přidejte službu a přidejte metodu zpětného volání k vytvoření služeb. Zde je změna, aby <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> se na metodu:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implementujte metodu zpětného volání, která by měla vytvořit a vrátit službu nebo hodnotu null, pokud ji nelze vytvořit.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio může odmítnout požadavek na poskytování služby. Činí tak, pokud jiný VSPackage již poskytuje službu.

3. Nyní můžete získat službu a používat její metody. Následující příklad ukazuje pomocí služby v inicializátoru, ale můžete získat službu kdekoli chcete použít službu.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     Hodnota `helloString` by měla být "Hello".

## <a name="see-also"></a>Viz také
- [Postup: Získání služby](../extensibility/how-to-get-a-service.md)
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
- [Základy služeb](../extensibility/internals/service-essentials.md)
