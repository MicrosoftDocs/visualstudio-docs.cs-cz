---
title: Aktualizace uživatelského rozhraní | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698890"
---
# <a name="updating-the-user-interface"></a>Aktualizace uživatelského rozhraní
Po implementaci příkazu můžete přidat kód pro aktualizaci uživatelského rozhraní se stavem nových příkazů.

 V typické aplikaci Win32 lze sadu příkazů průběžně dotazovat a stav jednotlivých příkazů lze upravit podle toho, jak je uživatel zobrazí. Však vzhledem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k tomu, že prostředí může hostit neomezený počet VSPackages, rozsáhlé dotazování může snížit odezvu, zejména dotazování mezi sestavení mezi spravovaným kódem a COM.

### <a name="to-update-the-ui"></a>Aktualizace nového ui

1. Proveďte jeden z následujících kroků:

    - Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metody.

         Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lze získat ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby, takto.

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

         Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> je parametr nenulová`TRUE`( ), pak je aktualizace provedena synchronně a okamžitě. Doporučujeme předat nulu`FALSE`( ) pro tento parametr pomoci udržet dobrý výkon. Pokud se chcete vyhnout ukládání do `DontCache` mezipaměti, použijte příznak při vytváření příkazu v souboru .vsct. Nicméně, používat příznak opatrně nebo výkon může snížit. Další informace o vlajkách příkazů naleznete v dokumentaci [k prvku command flag.](../extensibility/command-flag-element.md)

    - V Balíčcích VSPackages, které jsou hostitelem ovládacího prvku ActiveX pomocí modelu aktivace <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> na místě v okně, může být vhodnější použít metodu. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> v <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> v rozhraní jsou funkčně ekvivalentní. Obě způsobit prostředí znovu dotaz na stav všech příkazů. Aktualizace se obvykle neprovádí okamžitě. Místo toho je aktualizace zpožděna až do doby nečinnosti. Prostředí ukládá do mezipaměti stav příkazu, aby se zachoval dobrý výkon. Pokud se chcete vyhnout ukládání do `DontCache` mezipaměti, použijte příznak při vytváření příkazu v souboru .vsct. Nicméně používat příznak opatrně, protože výkon může snížit.

         Všimněte si, <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> že můžete `QueryInterface` získat rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> voláním metody na <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> objekt nebo získáním rozhraní ze služby.

## <a name="see-also"></a>Viz také
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementace](../extensibility/internals/command-implementation.md)
