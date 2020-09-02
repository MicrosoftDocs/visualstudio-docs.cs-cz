---
title: 'Postupy: řešení potíží se službami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204072"
---
# <a name="how-to-troubleshoot-services"></a>Postupy: Řešení problémů se službami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K dispozici je několik běžných problémů, ke kterým může dojít při pokusu o získání služby:  
  
- Služba není zaregistrovaná v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Služba se požaduje podle typu rozhraní, nikoli podle typu služby.  
  
- Rozhraní VSPackage požadující službu nebylo zablokováno.  
  
- Je použit nesprávný poskytovatel služby.  
  
  Pokud nelze získat požadovanou službu, volání <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> vrátí hodnotu null. Po vyžádání služby byste měli vždycky testovat hodnotu null:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Řešení potíží se službou  
  
1. Zkontrolujte systémový registr a zjistěte, jestli je služba správně zaregistrovaná. Další informace najdete v tématu [Registrace služeb](../misc/registering-services.md).  
  
     Následující fragment souboru REG ukazuje, jak může být služba SVsTextManager zaregistrovaná:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     V předchozím příkladu je číslo verze verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , například 12,0 nebo 14,0, klíč {F5E7E71D-1401-11D1-883B-0000F87579D2} je identifikátor (SID) služby, SVsTextManager a výchozí hodnota {F5E7E720-1401-11D1-883B-0000F87579D2} je identifikátor GUID balíčku VSPackage správce textu, který tuto službu poskytuje.  
  
2. Při volání metody GetService použijte typ služby, nikoli typ rozhraní. Při vyžádání služby z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Package> rozhraní EXTRAHUJE identifikátor GUID z tohoto typu. Služba nebude nalezena, pokud existují následující podmínky:  
  
    1. Typ rozhraní se předává metodě GetService místo typu služby.  
  
    2. K rozhraní není explicitně přiřazen žádný identifikátor GUID. Proto systém vytvoří pro objekt výchozí identifikátor GUID podle potřeby.  
  
3. Ujistěte se, že rozhraní VSPackage požadující službu byla zablokována. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lokality vytvoří VSPackage po jeho sestavení a před voláním <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Pokud máte kód v konstruktoru VSPackage, který potřebuje službu, přesuňte ho do metody Initialize.  
  
4. Ujistěte se, že používáte správného poskytovatele služeb.  
  
     Ne všichni poskytovatelé služeb jsou podobně. Poskytovatel služeb, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] předává do okna nástroje, se liší od toho, který se předává do VSPackage. Poskytovatel služeb systému Windows ví o <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , ale neví o nástroji <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Můžete zavolat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro získání poskytovatele služby VSPackage v rámci okna nástroje.  
  
     Pokud okno nástroje hostuje uživatelský ovládací prvek nebo jiný kontejner ovládacích prvků, bude tento kontejner zadaný modelem komponent Windows a nebude mít přístup k žádným [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] službám. Můžete zavolat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro získání poskytovatele služby VSPackage z kontejneru ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Seznam dostupných služeb](../extensibility/internals/list-of-available-services.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)
