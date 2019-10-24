---
title: Aktualizace uživatelského rozhraní | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718789"
---
# <a name="updating-the-user-interface"></a>Aktualizace uživatelského rozhraní
Po implementaci příkazu můžete přidat kód pro aktualizaci uživatelského rozhraní se stavem vašich nových příkazů.

 V typických aplikacích Win32 může být sada příkazů průběžně dotazována a stav jednotlivých příkazů lze upravit tak, jak je uživatel zobrazí. Vzhledem k tomu, že prostředí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může hostovat neomezený počet VSPackage, může rozsáhlé cyklické dotazování snížit rychlost odezvy, zejména dotazování napříč definičními sestaveními mezi spravovaným kódem a COM.

### <a name="to-update-the-ui"></a>Aktualizace uživatelského rozhraní

1. Proveďte jeden z následujících kroků:

    - Zavolejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         @No__t_0 rozhraní lze získat z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby, a to následujícím způsobem.

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

         Pokud je parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> nenulovou hodnotou (`TRUE`), provede se aktualizace synchronně a okamžitě. Pro zajištění dobrého výkonu doporučujeme předávat 0 (`FALSE`) pro tento parametr. Pokud chcete zabránit ukládání do mezipaměti, při vytváření příkazu v souboru. vsct použijte příznak `DontCache`. Nicméně používejte příznak s příznakem obezřetně nebo výkon se může snížit. Další informace o příznacích příkazu naleznete v dokumentaci [elementu příznak příkazu](../extensibility/command-flag-element.md) .

    - V rozhraních VSPackage, které hostují ovládací prvek ActiveX pomocí modelu místní aktivace v okně, může být pohodlnější použít metodu <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> v rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> a metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> v rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> jsou funkčně ekvivalentní. Jak by prostředí znovu provedlo dotaz na stav všech příkazů. Obvykle se aktualizace neprovádí okamžitě. Místo toho je aktualizace odložena až do doby nečinnosti. Prostředí ukládá do mezipaměti stav příkazu pro zajištění dobrého výkonu. Pokud chcete zabránit ukládání do mezipaměti, při vytváření příkazu v souboru. vsct použijte příznak `DontCache`. Nicméně příznak používejte opatrně, protože může dojít ke snížení výkonu.

         Všimněte si, že můžete získat rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> voláním metody `QueryInterface` na objektu <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> nebo získáním rozhraní ze služby <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>Viz také:
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementace](../extensibility/internals/command-implementation.md)