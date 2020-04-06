---
title: 'Postup: Poradce při potížích se službami | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710753"
---
# <a name="how-to-troubleshoot-services"></a>Postup: Poradce při potížích se službami
Při pokusu o získání služby může dojít k několika běžným problémům:

- Služba není registrována [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]u společnosti .

- Služba je požadována podle typu rozhraní a nikoli podle typu služby.

- VSPackage požadující službu nebyl aumístěn.

- Používá se nesprávný poskytovatel služeb.

  Pokud nelze získat požadovanou službu, volání <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> vrátí null. Vždy byste měli otestovat hodnotu null po vyžádání služby:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Řešení potíží se službou

1. Zkontrolujte systémový registr a zjistěte, zda byla služba správně zaregistrována. Další informace naleznete v [tématu How to: Provide a service](../extensibility/how-to-provide-a-service.md).

    Následující fragment souboru *REG* ukazuje, jak může být služba SVsTextManager registrována:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Ve výše uvedeném příkladu je [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]číslo verze verze , například 12.0 nebo 14.0, klíč {F5E7E71D-1401-11d1-883B-0000F87579D2} je identifikátor služby (SID) služby, SVsTextManager a výchozí hodnota {F5E7E720-1401-11d1-883B-0000F87579D2} je identifikátor GUID balíčku textového správce VSPackage, který poskytuje službu.

2. Při volání služby GetService použijte typ služby a nikoli typ rozhraní. Při požadování služby od [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrahuje identifikátor GUID z typu. Služba nebude nalezena, pokud existují následující podmínky:

   1. Typ rozhraní je předán GetService namísto typu služby.

   2. Žádné GUID je explicitně přiřazena rozhraní. Proto systém vytvoří výchozí identifikátor GUID pro objekt podle potřeby.

3. Ujistěte se, že VSPackage požadující službu byla umístěna. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]weby VSPackage po jeho sestavení <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>a před voláním .

    Pokud máte kód v konstruktoru VSPackage, který potřebuje `Initialize` službu, přesuňte jej do metody.

4. Ujistěte se, že používáte správného poskytovatele služeb.

    Ne všichni poskytovatelé služeb jsou stejní. Poskytovatel služeb, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] který přejde do okna nástroje se liší od toho, které předává VSPackage. Poskytovatel služeb okna nástroje <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>ví o , <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>ale neví o . Můžete volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> získat poskytovatele služeb VSPackage z okna nástroje.

    Pokud okno nástroje hostí uživatelský ovládací prvek nebo jiný kontejner ovládacího prvku, kontejner bude umístěn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelem komponenty systému Windows a nebude mít přístup k žádným službám. Můžete volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> získat poskytovatele služeb VSPackage z v rámci kontejneru ovládacího prvku.

## <a name="see-also"></a>Viz také
- [Seznam dostupných služeb](../extensibility/internals/list-of-available-services.md)
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
- [Základy služeb](../extensibility/internals/service-essentials.md)
