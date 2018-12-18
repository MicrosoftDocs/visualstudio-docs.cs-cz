---
title: Aktualizace uživatelského rozhraní | Dokumentace Microsoftu
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
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4e6b282ac58e523e8a2047e7f882d90b9f202bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765557"
---
# <a name="updating-the-user-interface"></a>Aktualizace uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po implementaci příkazu můžete přidat kód pro aktualizaci uživatelského rozhraní se stavem nové příkazy.  
  
 V typické aplikaci Win32 nepřetržitě testují sadu příkazů a stav jednotlivých příkazech je možné upravit, jak je uživatel zobrazit. Ale vzhledem k tomu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí můžete hostovat neomezený počet rozšíření VSPackages, rozsáhlé dotazování může snížit rychlost odezvy, zejména dotazování napříč sestavení vzájemné spolupráce mezi spravovaným kódem a modelu COM.  
  
### <a name="to-update-the-ui"></a>Aktualizace uživatelského rozhraní  
  
1.  Proveďte jeden z následujících kroků:  
  
    -   Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metody.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Rozhraní můžete získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby následujícím způsobem.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Pokud parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> zbývá nenulový (`TRUE`), pak aktualizace je provedena synchronně a okamžitě. Doporučujeme vám, že předáte nula (`FALSE`) pro tento parametr, který pomáhá zajistit dobrý výkon. Pokud chcete zabránit ukládání do mezipaměti, použijte `DontCache` příznak při vytváření příkazu v souboru .vsct. Nicméně, použijte příznak s rozvahou nebo se může snížit výkon. Další informace o příznaků příkazů najdete v článku [Command Flag – Element](../extensibility/command-flag-element.md) dokumentaci.  
  
    -   V balíčcích VSPackage, která hostování ovládacího prvku ActiveX s použitím modelu aktivace na místě v okně, může být vhodnější použít <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Metoda ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní jsou funkčně ekvivalentní. Oba způsobují prostředí tak, aby znovu odeslán dotaz na stav všech příkazů. Obvykle aktualizace nebude provedena okamžitě. Místo toho je aktualizace odložena až do doby nečinnosti. Prostředí ukládá do mezipaměti stav příkazu, který pomáhá zajistit dobrý výkon. Pokud chcete zabránit ukládání do mezipaměti, použijte `DontCache` příznak při vytváření příkazu v souboru .vsct. Však použijte příznak opatrně, protože může dojít ke snížení výkonu.  
  
         Všimněte si, že můžete získat <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní voláním `QueryInterface` metodu <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objektu nebo za získání rozhraní z <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby.  
  
## <a name="see-also"></a>Viz také  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementace](../extensibility/internals/command-implementation.md)

