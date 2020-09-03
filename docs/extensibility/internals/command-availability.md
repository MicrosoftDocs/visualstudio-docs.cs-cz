---
title: Dostupnost příkazu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709702"
---
# <a name="command-availability"></a>Dostupnost příkazu

Kontext sady Visual Studio určuje, které příkazy jsou k dispozici. Kontext se může změnit v závislosti na aktuálním projektu, aktuálním editoru, rozhraních VSPackage, které jsou načteny, a dalších aspektech integrovaného vývojového prostředí (IDE).

## <a name="command-contexts"></a>Kontexty příkazů

Nejběžnější jsou následující příkazy:

- Integrované vývojové prostředí (IDE): příkazy poskytované rozhraním IDE jsou vždy k dispozici.

- VSPackage: VSPackage můžou definovat, kdy se mají příkazy zobrazovat nebo skrývat.

- Projekt: příkazy projektu se zobrazí pouze pro aktuálně vybraný projekt.

- Editor: v jednom okamžiku může být aktivní pouze jeden editor. K dispozici jsou příkazy z aktivního editoru. Editor úzce spolupracuje s jazykovou službou. Služba jazyka musí zpracovat své příkazy v kontextu přidruženého editoru.

- Typ souboru: editor může načíst více než jeden typ souboru. Dostupné příkazy se můžou měnit v závislosti na typu souboru.

- Aktivní okno: poslední aktivní okno dokumentu nastavuje kontext uživatelského rozhraní (UI) pro klíčové vazby. Nicméně okno nástroje, které má tabulku vazby klíčů, která se podobá internímu webovému prohlížeči, může také nastavit kontext uživatelského rozhraní. U oken dokumentů s více kartami, jako je editor HTML, má každá karta jiný identifikátor GUID kontextu příkazu. Po registraci je okno nástroje vždy k dispozici v nabídce **zobrazení** .

- Kontext uživatelského rozhraní: kontexty uživatelského rozhraní jsou identifikovány hodnotami <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> třídy, například <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> při sestavení řešení nebo <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> při aktivním ladicím programu. Současně může být aktivní více kontextů uživatelského rozhraní.

## <a name="define-custom-context-guids"></a>Definování identifikátorů GUID vlastního kontextu

Pokud identifikátor GUID příslušného kontextu příkazu ještě není definovaný, můžete ho definovat ve VSPackage a pak ho programovat jako aktivní nebo neaktivní, jak je potřeba k řízení viditelnosti příkazů:

1. Zaregistrujte identifikátory GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.

2. Získejte stav GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.

3. Zapněte a vypněte kontextové identifikátory GUID voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.

> [!CAUTION]
> Ujistěte se, že VSPackage nemá vliv na žádné existující identifikátory GUID kontextu, protože na nich mohou být závislé jiné sady VSPackage.

## <a name="see-also"></a>Viz také

- [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
