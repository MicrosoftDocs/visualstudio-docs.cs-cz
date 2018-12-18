---
title: Příkaz dostupnosti | Dokumentace Microsoftu
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98250763f504bc7d142f15e559334f296a2e026b
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511131"
---
# <a name="command-availability"></a>Dostupnost příkazu

Kontext sady Visual Studio Určuje, které příkazy jsou k dispozici. Kontext můžete měnit v závislosti na aktuální projekt, aktuální editor, rozšíření VSPackages, která jsou načtena a další aspekty integrovaného vývojového prostředí (IDE).

## <a name="command-contexts"></a>Příkaz kontextů

Následující příkaz kontexty jsou nejčastěji:

- Integrované vývojové prostředí: Příkazy poskytované rozhraní IDE jsou vždy k dispozici.

- VSPackage: Rozšíření VSPackages můžete definovat při příkazy jsou k zobrazení nebo skrytí.

- Projekt: Projekt příkazy se zobrazují jenom pro aktuálně vybraný projekt.

- Editor: Pouze jeden editor může být aktivní v čase. Příkazy z aktivního editoru jsou k dispozici. Editor úzce spolupracuje se službou language. Služba jazyka musí zpracovat příkazy v kontextu editoru přidružené.

- Typ souboru: editoru můžete načíst více než jeden typ souboru. Dostupné příkazy můžete měnit v závislosti na typu souboru.

- Aktivní okno: poslední okno aktivní dokument nastavuje uživatelský kontext rozhraní (UI) pro vazby klíčů. Panel nástrojů, který má klíč vazby tabulku, která vypadá podobně jako interní webový prohlížeč, ale také nastavit kontextu uživatelského rozhraní. Pro dokument s kartami s více windows jako je například HTML editor má každá karta jiný příkaz kontextu identifikátor GUID. Po registraci panelu nástrojů je vždy k dispozici na **zobrazení** nabídky.

- Kontextu uživatelského rozhraní: kontexty uživatelského rozhraní jsou určeny hodnoty <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> třídy, například <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> při sestavení řešení nebo <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> když je aktivní ladicí program. Kontexty více uživatelského rozhraní může být aktivní ve stejnou dobu.

## <a name="define-custom-context-guids"></a>Definovat vlastní místní GUID

Pokud příslušný příkaz kontextu, již není definovaný identifikátor GUID, můžete definovat jeden v vašeho balíčku VSPackage a pak naprogramovat tak být aktivní nebo neaktivní podle potřeby řídit viditelnost příkazů:

1.  Zaregistrovat GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.

2.  Získat stav kontextu GUID voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.

3.  Zapnutí a vypnutí GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.
   
> [!CAUTION]
> Ujistěte se, že vaše VSPackage nemá vliv na všechny existující kontext identifikátory GUID vzhledem k tomu, že ostatní rozšíření VSPackages může záviset na ně.

## <a name="see-also"></a>Viz také:

- [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)