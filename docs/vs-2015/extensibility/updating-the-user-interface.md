---
title: Aktualizace uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186360"
---
# <a name="updating-the-user-interface"></a>Aktualizace uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po implementaci příkazu můžete přidat kód pro aktualizaci uživatelského rozhraní se stavem vašich nových příkazů.  
  
 V typických aplikacích Win32 může být sada příkazů průběžně dotazována a stav jednotlivých příkazů lze upravit tak, jak je uživatel zobrazí. Vzhledem k tomu, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí může hostovat neomezený počet VSPackage, může rozsáhlé cyklické dotazování snížit rychlost odezvy, zejména dotazování napříč definičními sestaveními mezi spravovaným kódem a com.  
  
### <a name="to-update-the-ui"></a>Aktualizace uživatelského rozhraní  
  
1. Proveďte jeden z následujících kroků:  
  
    - Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodu.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>Rozhraní lze ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby získat následujícím způsobem.  
  
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
  
         Pokud parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> je nenulový ( `TRUE` ), provede se aktualizace synchronně a okamžitě. Pro zajištění dobrého výkonu doporučujeme předávat 0 ( `FALSE` ) pro tento parametr. Pokud chcete zabránit ukládání do mezipaměti, použijte `DontCache` příznak při vytváření příkazu v souboru. vsct. Nicméně používejte příznak s příznakem obezřetně nebo výkon se může snížit. Další informace o příznacích příkazu naleznete v dokumentaci [elementu příznak příkazu](../extensibility/command-flag-element.md) .  
  
    - V rozhraních VSPackage, které hostují ovládací prvek ActiveX pomocí modelu místní aktivace v okně, může být pohodlnější použít <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>Metoda v rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metoda v <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní jsou funkčně ekvivalentní. Jak by prostředí znovu provedlo dotaz na stav všech příkazů. Obvykle se aktualizace neprovádí okamžitě. Místo toho je aktualizace odložena až do doby nečinnosti. Prostředí ukládá do mezipaměti stav příkazu pro zajištění dobrého výkonu. Pokud chcete zabránit ukládání do mezipaměti, použijte `DontCache` příznak při vytváření příkazu v souboru. vsct. Nicméně příznak používejte opatrně, protože může dojít ke snížení výkonu.  
  
         Všimněte si, že můžete získat <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní voláním `QueryInterface` metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objektu nebo získáním rozhraní ze <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby.  
  
## <a name="see-also"></a>Viz také  
 [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementace](../extensibility/internals/command-implementation.md)
