---
title: Aktualizace uživatelského rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b3bc8c4b87aefe62cbd27e64fc426ddb7abf96e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139153"
---
# <a name="updating-the-user-interface"></a>Aktualizace uživatelského rozhraní
Po implementaci příkazu můžete přidat kód pro aktualizace uživatelského rozhraní se stavem nové příkazy.  
  
 V typické aplikaci Win32 nepřetržitě testují sadu příkazů nástroje a stav jednotlivých příkazy lze upravit, jako je zobrazit uživatele. Ale protože [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí může hostovat neomezený počet VSPackages, rozsáhlé dotazování může snížit kratší reakční doby, zejména dotazování napříč sestavení vzájemné spolupráce mezi spravovaného kódu a COM.  
  
### <a name="to-update-the-ui"></a>Aktualizace uživatelského rozhraní  
  
1.  Proveďte jeden z následujících kroků:  
  
    -   Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metoda.  
  
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
  
         Pokud parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> je nulová (`TRUE`), pak aktualizace probíhá synchronně a okamžitě. Doporučujeme vám, že předáváte nula (`FALSE`) pro tento parametr můžete udržovat dobrý výkon. Pokud chcete, aby se zabránilo ukládání do mezipaměti, budou použity `DontCache` příznak při vytváření příkazu v souboru .vsct. Nicméně, použijte příznak opatrně nebo může dojít ke snížení výkonu. Další informace o příkazu příznaky najdete v tématu [Element Command příznak](../extensibility/command-flag-element.md) dokumentaci.  
  
    -   V VSPackages, který hostovat pomocí modelu aktivace na místě v okně Ovládací prvek ActiveX, může být pohodlnější použití <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metoda. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Metoda v <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metoda v <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní jsou funkčně rovnocenné. Obě způsobit prostředí tak, aby znovu dotazování na stav všech příkazů. Obvykle se aktualizace není provedena okamžitě. Místo toho je zpožděna aktualizace, dokud doby nečinnosti. Prostředí ukládá do mezipaměti stav příkazu můžete udržovat dobrý výkon. Pokud chcete, aby se zabránilo ukládání do mezipaměti, budou použity `DontCache` příznak při vytváření příkazu v souboru .vsct. Nicméně použijte příznak opatrně, protože může snížit výkon.  
  
         Všimněte si, že můžete získat <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní voláním `QueryInterface` metodu <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objektu nebo nástrojem získává se z <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby.  
  
## <a name="see-also"></a>Viz také  
 [Jak přidat VSPackages prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementace](../extensibility/internals/command-implementation.md)