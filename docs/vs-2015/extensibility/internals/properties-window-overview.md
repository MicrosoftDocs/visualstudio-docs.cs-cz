---
title: Přehled okna vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700744"
---
# <a name="properties-window-overview"></a>Přehled okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **vlastnosti** se používá k zobrazení vlastností pro objekty vybrané ve dvou hlavních typech systému Windows, které jsou k dispozici v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Tyto dva typy oken jsou:  
  
- Okna nástrojů, například Průzkumník řešení, Zobrazení tříd a prohlížeč objektů  
  
- Okna dokumentu obsahující taková editory a návrháře jako Návrhář formulářů, editor XML a editor HTML  
  
## <a name="using-the-properties-window"></a>Použití okna vlastnosti  
 V okně **vlastnosti** se zobrazí vlastnosti jedné nebo více vybraných položek. Je-li vybráno více položek, zobrazí se průnik všech vlastností pro všechny vybrané objekty.  
  
 Události související s vybraným objektem v okně návrhu formuláře nebo editoru HTML pomocí metadat COM+ se zobrazí v okně **vlastnosti** . Můžete například vybrat tlačítko a zobrazit jeho přidružené události, jako je například `OnClick` událost, která může být propojena s tímto tlačítkem.  
  
 Události zobrazené v okně **vlastnosti** se primárně používají s objekty, které jsou vázány na kód. Pokud upravujete formát souboru, který neobsahuje žádné položky k provádění kódu, nebudete mít žádné události. Události se zobrazují pouze v okně **vlastnosti** , pokud existuje vazba mezi běžícím kódem a určitými událostmi, které jsou spojeny s konkrétními objekty. Příkladem může být kód za vybraným objektem, který se spustí při aktivaci tohoto objektu.  
  
 V následující tabulce jsou uvedena primární rozhraní používaná oknem **vlastnosti** .  
  
|Název rozhraní|Popis|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Poskytuje seznam kategorií v okně **vlastnosti** a mapuje každou vlastnost na kategorii.|  
|[Rozhraní IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Zpřístupňuje metody a vlastnosti objektu pro programové nástroje a další aplikace, které podporují automatizaci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Poskytuje tlačítka pro tři tečky (...) označovaná jako *tvůrci* , kteří otevřou modální dialogová okna implementovaná samotným objektem. Používá se, když uživatel nemůže v textovém poli snadno zadat hodnotu. Například může být použit k otevření výběru barvy, který určuje hodnotu RGB za vás.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Poskytuje přístup k objektům, které slouží k aktualizaci informací zobrazených v okně **vlastnosti** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je implementováno pomocí VSPackage pro každé okno, které obsahuje vybrané objekty se souvisejícími vlastnostmi, které mají být zobrazeny.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Poskytuje informace o typu objektu, například metody rozhraní a polí struktury.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umožňuje VSPackage získat oznámení o událostech výběru a načíst informace o aktuální hierarchii projektu, položce, hodnotě prvku a kontextu uživatelského rozhraní příkazu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Poskytuje prostředí s přístupem k více výběrům.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Slouží k poskytnutí lokalizovaných názvů pro některé vlastnosti, které se zobrazují v okně **vlastnosti** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Upozorní zaregistrované sady VSPackage změn na aktuální výběr, hodnotu prvku nebo kontext uživatelského rozhraní příkazu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Oznamuje prostředí změny v aktuálním výběru a poskytuje přístup k informacím o hierarchii a položkách, které se týkají nového výběru.|  
  
 Další informace o najdete v `IDispatch` knihovně MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)   
 [Pole a rozhraní okna Vlastnosti](../../extensibility/internals/properties-window-fields-and-interfaces.md)
