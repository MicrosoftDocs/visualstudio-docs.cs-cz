---
title: Vlastní uživatelské rozhraní (řízení zdrojového balíčku VSPackage) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 237a79fe0225f54bd8be1f779f241bc54f13cd09
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728542"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Vlastní uživatelské rozhraní (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage deklaruje jeho položky nabídky a příslušné stavy výchozí soubor tabulky příkazů aplikace Visual Studio (.vsct). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrované vývojové prostředí (IDE) zobrazí položky nabídky v jejich výchozí stavy, dokud načtení sady VSPackage. Následně <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda je volána k povolení nebo zakázání položky nabídky.  
  
 VSPackage můžete nastavit klíč registru, takže sady VSPackage mohou být načteny automaticky v závislosti na kontextu příkaz uživatelské rozhraní (UI), i když obvykle správy zdrojových kódů VSPackage by se měly načíst na požádání namísto pouze přepnutí na konkrétním kontextu uživatelského rozhraní. Další informace o tomto klíči registru AutoLoadPackages najdete v tématu [Správa balíčky VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Uživatelské rozhraní balíčku VSPackage  
 Zdrojový ovládací prvek balíček je implementovaný jako VSPackage a nepoužívá žádné uživatelské rozhraní z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Každý ovládací prvek zdroje balíčku VSPackage musíte zadat své vlastní prvky uživatelského rozhraní, jako je například položky nabídky, skupiny nabídek, okna nástrojů, panelů nástrojů a všechny požadované uživatelského rozhraní pro nastavení možností konkrétní do správy zdrojového kódu VSPackage. Tyto prvky uživatelského rozhraní je možné povolit staticky nebo dynamicky. Statické prvky uživatelského rozhraní jsou definovány v souboru .vsct a zobrazují, jestli sady VSPackage je načtena, nebo ne. Dynamické prvky uživatelského rozhraní může být viditelné v závislosti na kontextu uživatelského rozhraní konkrétním příkazem, například <xref:EnvDTE.Constants.vsContextNoSolution>, nebo jako výsledek volání <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Viditelnost dynamické prvky uživatelského rozhraní v souladu s strategie pro opožděné načtení rozšíření VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Omezení uživatelského rozhraní na balíčky VSPackage správy zdrojového  
 Vzhledem k tomu, že ovládací prvek zdroje balíčku VSPackage nelze odebrat z prostředí IDE až po načtení, musí být možné je zadat v neaktivním stavu sady VSPackage. Když VSPackage obdrží oznámení, že není už aktivní, sady VSPackage zakáže jeho uživatelské rozhraní a ignoruje zásahu externí prostředí IDE. Implementace sady VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda by měla příkazy skryje, když sady VSPackage není aktivní.  
  
 Každý musí implementovat balíčku VSPackage správy zdrojového kódu `IVsSccProvider` rozhraní. Dvě metody v rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, musí být implementované sady VSPackage.  
  
 Ovládací prvek zdroje balíčku VSPackage může odběru jste se přihlásili k různým událostem IDE, které jsou implementované <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, a tak dále. Navíc sady VSPackage může implementovali rozhraní registru povoleny zpětné volání, jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Tyto musí všechny se ignoruje, pokud neaktivní.  
  
 Následující seznam obsahuje rozhraní ovlivněnému v aktivním stavu balíčku VSPackage správy zdrojového kódu:  
  
- Sledování událostí dokumenty projektu.  
  
- Řešení události.  
  
- Rozhraní trvalého řešení. Pokud je neaktivní, by neměla balíčky zápis do souborů .sln a .suo.  
  
- Prvky pro otevřenou vlastnost.  
  
  Požadovaný <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, a také všechny volitelné rozhraní související se správou zdrojového kódu nejsou volána, když ovládací prvek zdroje balíčku VSPackage je neaktivní.  
  
  Když [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spustí rozhraní IDE, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nastaví kontext příkaz uživatelského rozhraní na ID ovládacího prvku zdroje aktuální výchozí ID balíčku VSPackage. To způsobí, že statické uživatelského ovládacího prvku aktivní zdroje balíčku VSPackage se zobrazí v integrovaném vývojovém prostředí bez skutečně načtení sady VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pozastaví VSPackage k registraci ve službě [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> předtím, než provede všechna volání do sady VSPackage.  
  
  Následující tabulka popisuje konkrétní podrobnosti o tom, jak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] skryje různé položky uživatelského rozhraní IDE.  
  
|Položka uživatelského rozhraní|Popis|  
|-------------|-----------------|  
|Nabídky a panely nástrojů|Zdrojový ovládací prvek balíček musíte nastavit počáteční stav viditelnosti nabídek a panelů nástrojů pro balíček ID zdrojového ovládacího prvku v [visibilityconstraints –](../../extensibility/visibilityconstraints-element.md) část souboru .vsct. Díky tomu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí odpovídajícím způsobem nastavit stav položky nabídky bez načítání sady VSPackage a volání implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda.|  
|Nástroje systému windows|Ovládací prvek zdroje balíčku VSPackage skryje všechny okna nástrojů, který ho vlastní, když se provádí neaktivní.|  
|Možnosti stránky konkrétní balíčku VSPackage správy zdrojového kódu|Klíč registru HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts umožňuje VSPackage nastavovat kontexty, ve kterých se vyžaduje její stránky možností, které se zobrazí. Položky registru pod tímto klíčem musel být vytvořené pomocí služby ID (SID) pro službu správy zdrojových kódů a přiřadíte jí hodnotu DWORD na 1. Pokaždé, když se uživatelského rozhraní dojde k události v kontextu, který je zaregistrován balíčku VSPackage správy zdrojového kódu, bude volána sady VSPackage, pokud je aktivní.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)

