---
title: Registrace a zrušení registrace VSPackages | Microsoft Docs
description: Seznamte se s registrací a zrušením registrace rozšíření VSPackages, včetně atributů, které používáte, a souboru .pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48067ed883a44870b3b753cb5e3d6943eca91ca5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900301"
---
# <a name="register-and-unregister-vspackages"></a>Registrace a zrušení registrace balíčku VSPackage
Atributy se používají k registraci balíčku VSPackage, ale

## <a name="register-a-vspackage"></a>Registrace balíčku VSPackage
 Pomocí atributů můžete řídit registraci spravovaných balíčku VSPackage. Všechny registrační informace jsou obsaženy v *souboru .pkgdef.* Další informace o registraci na základě souborů najdete v tématu [Nástroj CreatePkgDef.](../extensibility/internals/createpkgdef-utility.md)

 Následující kód ukazuje, jak použít standardní registrační atributy k registraci balíčku VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Zrušení registrace rozšíření
 Pokud jste experimentovali s mnoha různými balíčky VSPackage a chcete je z experimentální instance odebrat, stačí spustit **příkaz Resetovat.** Na úvodní **stránce Visual Studio vyhledejte** Resetovat experimentální instanci nebo spusťte tento příkaz z příkazového řádku:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Pokud chcete odinstalovat rozšíření, které jste nainstalovali ve vývojové instanci nástroje Visual Studio, přejděte na Nástroje Rozšíření a aktualizace, vyhledejte rozšíření a klikněte  >  na **Odinstalovat.**

 Pokud z nějakého důvodu žádná z těchto metod neprovede odinstalaci rozšíření, můžete registraci sestavení VSPackage zrušit z příkazového řádku následujícím způsobem:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Použití vlastního atributu registrace k registraci rozšíření

V některých případech možná budete muset pro své rozšíření vytvořit nový atribut registrace. Atributy registrace můžete použít k přidání nových klíčů registru nebo k přidání nových hodnot do existujících klíčů. Nový atribut musí být odvozen od <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> a musí přepsat metody a <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Vytvoření vlastního atributu

Následující kód ukazuje, jak vytvořit nový atribut registrace.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 se používá u tříd atributů k určení elementu programu (třídy, metody atd.), ke kterému se atribut vztahuje, zda jej lze použít více než jednou a zda lze jej <xref:System.AttributeUsageAttribute> dědit.

### <a name="create-a-registry-key"></a>Vytvoření klíče registru

V následujícím kódu vlastní atribut  vytvoří vlastní podklíč pod klíčem pro balíček VSPackage, který je registrován.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Vytvoření nové hodnoty v rámci existujícího klíče registru

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
