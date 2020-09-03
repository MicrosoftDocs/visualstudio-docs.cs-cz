---
title: Registrace a zrušení registrace VSPackage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701585"
---
# <a name="register-and-unregister-vspackages"></a>Registrace a zrušení registrace VSPackage
Atributy můžete použít k registraci VSPackage, ale

## <a name="register-a-vspackage"></a>Registrace VSPackage
 Pomocí atributů můžete řídit registraci spravovaných VSPackage. Všechny registrační informace jsou obsaženy v souboru *. pkgdef* . Další informace o registraci na základě souborů naleznete v tématu [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).

 Následující kód ukazuje, jak použít standardní registrační atributy k registraci sady VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Zrušení registrace rozšíření
 Pokud jste experimentování s velkým množstvím různých VSPackage a chcete je odebrat z experimentální instance, stačí spustit příkaz pro **obnovení** . Na úvodní stránce počítače vyhledejte **resetování experimentální instance sady Visual Studio** nebo spusťte tento příkaz z příkazového řádku:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Pokud chcete odinstalovat rozšíření, které jste nainstalovali do vývojové instance sady Visual Studio, přejděte na **nástroje**  >  **rozšíření a aktualizace**, Najděte rozšíření a klikněte na **odinstalovat**.

 Pokud z nějakého důvodu neuspěje žádná z těchto metod při odinstalaci rozšíření, můžete zrušit registraci sestavení VSPackage z příkazového řádku následujícím způsobem:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Použití vlastního registračního atributu k registraci rozšíření

V některých případech může být nutné vytvořit nový registrační atribut pro vaše rozšíření. Registrační atributy můžete použít k přidání nových klíčů registru nebo k přidání nových hodnot do existujících klíčů. Nový atribut musí být odvozen z <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> a musí přepsat <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody a.

### <a name="create-a-custom-attribute"></a>Vytvoření vlastního atributu

Následující kód ukazuje, jak vytvořit nový registrační atribut.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 Se <xref:System.AttributeUsageAttribute> používá v třídách atributů k určení prvku programu (třídy, metody atd.), na který se atribut vztahuje, zda jej lze použít více než jednou a zda jej lze zdědit.

### <a name="create-a-registry-key"></a>Vytvoření klíče registru

V následujícím kódu vlastní atribut vytvoří **vlastní** podklíč pod klíčem pro VSPackage, který je zaregistrován.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Vytvoří novou hodnotu v existujícím klíči registru.

Můžete přidat vlastní hodnoty do existujícího klíče. Následující kód ukazuje, jak přidat novou hodnotu do registračního klíče VSPackage.

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
