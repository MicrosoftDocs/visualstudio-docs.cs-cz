---
title: 'Postupy: odstraňování potíží se službami | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d2e1e59b5d2bd1210511b355676407a1368143f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834211"
---
# <a name="how-to-troubleshoot-services"></a>Postupy: odstraňování potíží se službami
Existuje několik běžných problémů, které se mohou vyskytnout při pokusu o získání služby:  
  
- Služba není zaregistrována [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Typ rozhraní a ne typ služby, je požadována služba.  
  
- VSPackage žádosti o služby nebyl umístěn.  
  
- Chybný zprostředkovatel se používá.  
  
  Pokud požadovanou službu nelze získat, volání <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> , vrátí hodnotu null. Test pro null by měla vždy po žádosti služby:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="to-troubleshoot-a-service"></a>Řešení potíží s služby  
  
1. Zkontrolujte, jestli služba správně zaregistrovaný do systémového registru. Další informace najdete v tématu [postupy: poskytování služby](../extensibility/how-to-provide-a-service.md).  
  
    Následující *.reg* souboru fragmentu ukazuje, jak může být služba SVsTextManager zaregistrovaná:  
  
   ```  
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
   "Name"="SVsTextManager"  
   ```  
  
    V příkladu výše uvedené číslo verze je verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], například 12.0 nebo 14.0, klíč {F5E7E71D-1401-11d1-883B-0000F87579D2} je služba identifikátor (SID) služby, SVsTextManager a {výchozí hodnotu F5E7E720-1401-11D1-883B-0000F87579D2} je balíček GUID textový správce balíčku VSPackage, která poskytuje služby.  
  
2. Při volání GetService používejte typ služby a není typem rozhraní. Při žádosti o službu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrahuje identifikátor GUID z typu. Služba nebude nalezena při splnění následujících podmínek:  
  
   1.  Typ rozhraní je předán GetService místo typu služby.  
  
   2.  Žádný identifikátor GUID je explicitně přiřazeny rozhraní. Proto systém vytvoří výchozí identifikátor GUID objektu podle potřeby.  
  
3. Ujistěte se, že byl umístěn VSPackage žádosti o službu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poté, co je vytvořen a před voláním lokality VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
    Pokud máte kód v balíčku VSPackage konstruktor, který potřebuje služby, přesuňte ho do `Initialize` metody.  
  
4. Ujistěte se, že používáte správné služby poskytovatele.  
  
    Ne všichni poskytovatelé služby jsou stejné. Poskytovatel služeb, který [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] předá do panelu nástrojů se liší od ten pak předá VSPackage. Poskytovatel služeb okno nástroj ví o <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ale neví o <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Můžete volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> zobrazíte poskytovatele služeb VSPackage z v rámci panelu nástrojů.  
  
    Pokud uživatelský ovládací prvek nebo jiném kontejneru ovládacího prvku je hostitelem panelu nástrojů, kontejner bude umístěna komponenty modelem Windows a nebudete mít přístup k libovolnému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] služby. Můžete volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> zobrazíte VSPackage poskytovatele služeb v rámci kontejneru ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:  
 [Seznam dostupných služeb](../extensibility/internals/list-of-available-services.md)   
 [Použít a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služby](../extensibility/internals/service-essentials.md)