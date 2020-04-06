---
title: Registrace a zrušení registrace vspackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f345bdbd3cf5858d495937c743b580abf5e3dd50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701585"
---
# <a name="register-and-unregister-vspackages"></a>Registrace a zrušení registrace vspackages
Atributy se používají k registraci balíčku VSPackage, ale

## <a name="register-a-vspackage"></a>Registrace balíčku VSPackage
 Atributy můžete použít k řízení registrace spravovaných balíčků VSPackages. Všechny registrační informace jsou obsaženy v souboru *.pkgdef.* Další informace o registraci založené na souborech naleznete v [tématu CreatePkgDef utility](../extensibility/internals/createpkgdef-utility.md).

 Následující kód ukazuje, jak používat standardní atributy registrace k registraci vspackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Zrušení registrace rozšíření
 Pokud jste experimentovali s mnoha různými Balíčky VSPackages a chcete je odebrat z experimentální instance, stačí spustit příkaz **Reset.** Vyhledejte **možnost Obnovit experimentální instanci sady Visual Studio** na úvodní stránce počítače nebo spusťte tento příkaz z příkazového řádku:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Pokud chcete odinstalovat rozšíření, které jste nainstalovali ve vývojové instanci sady Visual Studio, přejděte na **nástroje** > **rozšíření a aktualizace**, vyhledejte rozšíření a klepněte na tlačítko **Odinstalovat**.

 Pokud z nějakého důvodu ani jedna z těchto metod uspěje při odinstalaci rozšíření, můžete zrušit registraci sestavení VSPackage z příkazového řádku následujícím způsobem:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Použití vlastního atributu registrace k registraci rozšíření

V některých případech může být nutné vytvořit nový atribut registrace pro rozšíření. Atributy registrace můžete použít k přidání nových klíčů registru nebo k přidání nových hodnot do existujících klíčů. Nový atribut musí <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>být odvozen z , <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> a musí přepsat metody a.

### <a name="create-a-custom-attribute"></a>Vytvoření vlastního atributu

Následující kód ukazuje, jak vytvořit nový atribut registrace.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Používá <xref:System.AttributeUsageAttribute> se na třídy atributů k určení prvku programu (třída, metoda, atd.), ke kterému se atribut vystřídá, zda jej lze použít více než jednou a zda může být zděděn.

### <a name="create-a-registry-key"></a>Vytvoření klíče registru

V následujícím kódu vlastní atribut vytvoří **vlastní** podklíč pod klíčem pro VSPackage, který je registrován.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");
}
```

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Vytvoření nové hodnoty pod existujícím klíčem registru

K existujícímu klíči můžete přidat vlastní hodnoty. Následující kód ukazuje, jak přidat novou hodnotu do registračního klíče VSPackage.

```csharp
public override void Register(RegistrationAttribute.RegistrationContext context)
{
    Key packageKey = null;
    try
    {
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");
        packageKey.SetValue("NewCustom", 1);
    }
    finally
    {
        if (packageKey != null)
            packageKey.Close();
    }
}

public override void Unregister(RegistrationContext context)
{
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");
}
```

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
