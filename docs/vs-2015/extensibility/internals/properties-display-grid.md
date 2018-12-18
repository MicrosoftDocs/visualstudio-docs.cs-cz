---
title: Vlastnosti zobrazení mřížky | Dokumentace Microsoftu
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
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a3db18bacb2aee7bd908be4246c1ce0701e8fee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741390"
---
# <a name="properties-display-grid"></a>Zobrazení mřížky okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Vlastnosti** okně se zobrazí pole v mřížce. Levý sloupec obsahuje názvy vlastností; pravý sloupec obsahuje hodnoty vlastností.  
  
## <a name="working-with-the-grid"></a>Práce s mřížky  
 V seznamu dvěma sloupci jsou uvedeny vlastnosti nezávislé na konfiguraci, které lze změnit v době návrhu a jejich aktuální nastavení. Všimněte si, že se nemusí zobrazit všechny vlastnosti. Vlastnost můžete nastavit jako skrytý, například implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. Konkrétně k skrýt vlastnosti, které mají podřízené vlastnosti zobrazíte [skrytí vlastnosti, které mají podřízené vlastnosti](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Push informací **vlastnosti** okno, integrovaném vývojovém prostředí používá <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je volán rozšíření VSPackages pro každé okno, obsahující vybrat objekty s souvisejících vlastností, který se má zobrazit **vlastnosti** okna. **Průzkumník řešení**vaší implementace <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> volání `GetProperty` pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ve vaší hierarchii projektu k získání zobrazitelné objekty v hierarchii.  
  
 Pokud vaše VSPackage nepodporuje <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, rozhraní IDE se pokusí použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> pomocí hodnoty pro <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , zadejte hierarchie položky nebo položek.  
  
 Projekt není nutné vytvářet VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> vzhledem k tomu, že okno prostředí IDE zadat balíček, který implementuje (například **Průzkumníku řešení**) vytvoří <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> svým jménem.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se skládá ze tří metod, které jsou volány integrovaném vývojovém prostředí:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> obsahuje počet vybraných zobrazeného v objektů **vlastnosti** okna.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Vrátí `IDispatch` objekty, které jsou vybrány, který se má zobrazit **vlastnosti** okna.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> Díky tomu může některý z objektů vrácených podle <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> výběr podle uživatele. To umožňuje balíčku VSPackage vizuálně aktualizovat výběru zobrazí uživatelům v uživatelském rozhraní.  
  
  **Vlastnosti** extrahuje informace z okna `IDispatch` objekty se načíst vlastnosti prochází se jím. Používá prohlížeč vlastností `IDispatch` žádat objektu vlastností podporuje dotazováním `ITypeInfo`, který pochází z `IDispatch::GetTypeInfo`. Prohlížeč tyto hodnoty pak používá k naplnění **vlastnosti** okno a změnit hodnoty jednotlivých vlastností se zobrazí v mřížce. Informace o vlastnostech je udržována v rámci samotného objektu.  
  
  Protože vrácených objektů podporují `IDispatch`, volající může získat informace, jako je název objektu voláním buď `IDispatch::Invoke` nebo `ITypeInfo::Invoke` s identifikátorem předdefinované odeslání (DISPID), který představuje požadované informace. Jsou záporné Ujistěte se, že nepřekrývaly s uživatelem definované identifikátory deklarované hodnoty dispID.  
  
  **Vlastnosti** okně se zobrazí různé typy polí v závislosti na atributy specifické vlastnosti vybraného objektu. Tato pole obsahují editační políčka, rozevírací seznamy a odkazy na vlastní editor dialogových oknech.  
  
- Jsou načteny hodnoty obsažené v výčtový seznam <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> dotaz pro `IDispatch`. Hodnoty získané z výčtový seznam lze změnit v mřížce vlastností poklepáním na název pole, nebo kliknutím na hodnotu a výběrem nové hodnoty z rozevíracího seznamu. Pro vlastnosti, které mají předdefinovaná nastavení z výčtové seznamy jsou dvojitým kliknutím na název vlastnosti v seznamu vlastnosti procházení dostupných možností. Předdefinované vlastnosti pouze dvě možnosti, jako jsou true nebo false dvakrát klikněte na název vlastnosti přepínat mezi volby.  
  
- Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> je `false`, která udává, že se změnil hodnotu, hodnota se zobrazí tučným písmem. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> slouží k určení, pokud se hodnota můžete obnovit na původní hodnotu. Pokud ano, můžete změnit zpět na výchozí hodnotu tak, že kliknete pravým tlačítkem hodnotu a zvolíte **resetování** v nabídce Zobrazit. V opačném případě budete muset ručně změňte hodnotu zpět na výchozí hodnotu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> také umožňuje lokalizovat a skrýt názvy vlastností, které jsou zobrazeny v době návrhu, ale nemá vliv na názvy vlastností, které zobrazují za běhu.  
  
- Kliknutím na tlačítko se třemi tečkami (...) se zobrazí seznam hodnot vlastností, ze kterého může uživatel vybrat (například výběr barvy nebo seznamu písma). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> obsahuje tyto hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)

