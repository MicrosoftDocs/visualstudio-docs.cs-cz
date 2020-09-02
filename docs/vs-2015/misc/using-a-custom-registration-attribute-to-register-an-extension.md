---
title: Použití vlastního registračního atributu k registraci rozšíření | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935781"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Použití vlastního registračního atributu k registraci rozšíření
V některých případech může být nutné vytvořit nový registrační atribut pro vaše rozšíření. Registrační atributy můžete použít k přidání nových klíčů registru nebo k přidání nových hodnot do existujících klíčů. Nový atribut musí být odvozen z <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> a musí přepsat <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody a.  
  
## <a name="creating-a-custom-attribute"></a>Vytvoření vlastního atributu  
 Následující kód ukazuje, jak vytvořit nový registrační atribut.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 Se <xref:System.AttributeUsageAttribute> používá v třídách atributů k určení prvku programu (třídy, metody atd.), na který se atribut vztahuje, zda jej lze použít více než jednou a zda jej lze zdědit.  
  
### <a name="creating-a-registry-key"></a>Vytvoření klíče registru  
 V následujícím kódu vlastní atribut vytvoří **vlastní** podklíč pod klíčem pro VSPackage, který je zaregistrován.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Vytvoření nové hodnoty v existujícím klíči registru  
 Můžete přidat vlastní hodnoty do existujícího klíče. Následující kód ukazuje, jak přidat novou hodnotu do registračního klíče VSPackage.  
  
```  
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