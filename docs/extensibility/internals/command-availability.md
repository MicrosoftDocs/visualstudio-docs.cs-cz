---
title: Dostupnost příkazu | Dokumenty společnosti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709702"
---
# <a name="command-availability"></a>Dostupnost příkazu

Kontext sady Visual Studio určuje, které příkazy jsou k dispozici. Kontext se může změnit v závislosti na aktuálním projektu, aktuálním editoru, vspackages, které jsou načteny a další aspekty integrovaného vývojového prostředí (IDE).

## <a name="command-contexts"></a>Kontexty příkazů

Následující kontexty příkazů jsou nejběžnější:

- IDE: Příkazy poskytované rozhraní min. jsou vždy k dispozici.

- VSPackage: VSPackages můžete definovat, kdy příkazy mají být zobrazeny nebo skryté.

- Projekt: Příkazy projektu se zobrazí pouze pro aktuálně vybraný projekt.

- Editor: Pouze jeden editor může být aktivní najednou. Příkazy z aktivního editoru jsou k dispozici. Editor úzce spolupracuje s jazykovou službou. Služba jazyka musí zpracovávat své příkazy v kontextu přidruženého editoru.

- Typ souboru: Editor může načíst více než jeden typ souboru. Dostupné příkazy se mohou měnit v závislosti na typu souboru.

- Aktivní okno: Okno posledního aktivního dokumentu nastaví kontext uživatelského rozhraní (UI) pro klíčové vazby. Okno nástroje, které má tabulku vazby klíčů, která se podobá internímu webovému prohlížeči, by však také mohlo nastavit kontext uživatelského prostředí. Pro okna dokumentů s více kartami, jako je například editor HTML, má každá karta jiný identifikátor GUID kontextu příkazu. Po registraci nástroje je okno nástroje vždy k dispozici v nabídce **Zobrazení.**

- Kontext ui: Kontexty ui jsou určeny hodnotami <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> třídy, například při <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> stavění řešení nebo při aktivníladicí program. Více kontextů ui může být aktivní současně.

## <a name="define-custom-context-guids"></a>Definování vlastních identifikátorů GUID kontextu

Pokud není ještě definován příslušný identifikátor GUID kontextu příkazu, můžete jej definovat v balíčku VSPackage a poté jej naprogramovat tak, aby byl aktivní nebo neaktivní, jak je požadováno pro řízení viditelnosti příkazů:

1. Zaregistrujte identifikátory GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> kontextu voláním metody.

2. Získejte stav identifikátoru GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> kontextu voláním metody.

3. Zapněte a vypněte identifikátory GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.

> [!CAUTION]
> Ujistěte se, že váš VSPackage nemá vliv na všechny existující identifikátory GUID kontextu, protože ostatní VSPackages může záviset na nich.

## <a name="see-also"></a>Viz také

- [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
