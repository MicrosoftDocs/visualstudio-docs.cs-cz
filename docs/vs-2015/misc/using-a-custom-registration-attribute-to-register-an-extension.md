---
title: Pomocí atributu vlastní registrace k registraci rozšíření | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: douge
ms.openlocfilehash: 251c31efcbb8a72efac51f246e644a30a79ed999
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279835"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Pomocí atributu vlastní registrace k registraci rozšíření
V některých případech budete muset vytvořit nový atribut registrace pro vaše rozšíření. Přidat nové klíče registru nebo přidat nové hodnoty pro existující klíče, můžete použít atributy registrace. Nový atribut musí být odvozen od <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, a musí přepsat <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> a <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody.  
  
## <a name="creating-a-custom-attribute"></a>Vytváření vlastních atributů  
 Následující kód ukazuje, jak vytvořit nový atribut registrace.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> Se používá na třídy atributů k určení ovládací prvek programu (třídy, metody atd.), které se vztahují atribut, zda jej lze použít více než jednou a určuje, zda mohou dědit.  
  
### <a name="creating-a-registry-key"></a>Vytváří se klíč registru  
 Následující kód vytvoří vlastní atribut **vlastní** podklíče pod klíčem pro sady VSPackage, která je registrována.  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Vytváří se nová hodnota v rámci existující klíč registru  
 Vlastní hodnoty můžete přidat do existujícího klíče. Následující kód ukazuje, jak přidat novou hodnotu balíčku VSPackage registrační klíč.  
  
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