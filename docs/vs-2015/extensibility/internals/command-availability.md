---
title: Dostupnost příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780970"
---
# <a name="command-availability"></a>Dostupnost příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kontext sady Visual Studio určuje, které příkazy jsou k dispozici. Kontext se může změnit v závislosti na aktuálním projektu, aktuálním editoru, rozhraních VSPackage, které jsou načteny, a dalších aspektech integrovaného vývojového prostředí (IDE).  
  
## <a name="command-contexts"></a>Kontexty příkazů  
 Následující kontexty příkazů jsou nejběžnější.  
  
- **Rozhraní IDE** Příkazy poskytované rozhraním IDE jsou vždy k dispozici.  
  
- **VSPackage** VSPackage můžou definovat, kdy se mají příkazy zobrazovat nebo skrývat.  
  
- **Projekt** Příkazy projektu se zobrazí pouze pro aktuálně vybraný projekt.  
  
- **Editor** V jednom okamžiku může být aktivní pouze jeden editor. K dispozici jsou příkazy z aktivního editoru. Editor úzce spolupracuje s jazykovou službou. Služba jazyka musí zpracovat své příkazy v kontextu přidruženého editoru.  
  
- **Typ souboru** Editor může načíst více než jeden typ souboru. Dostupné příkazy se můžou měnit v závislosti na typu souboru.  
  
- **Aktivní okno** Poslední aktivní okno dokumentu nastaví kontext uživatelského rozhraní (UI) pro klíčové vazby. Nicméně okno nástroje, které má tabulku vazby klíčů, která se podobá internímu webovému prohlížeči, může také nastavit kontext uživatelského rozhraní. U oken dokumentů s více kartami, jako je editor HTML, má každá karta jiný identifikátor GUID kontextu příkazu. Po registraci je okno nástroje vždy k dispozici v nabídce **zobrazení** .  
  
- **Kontext uživatelského rozhraní** Kontexty uživatelského rozhraní jsou identifikovány hodnotami <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> třídy, například <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> při sestavení řešení nebo <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> při aktivním ladicím programu. Současně může být aktivní více kontextů uživatelského rozhraní.  
  
## <a name="defining-custom-context-guids"></a>Definování identifikátorů GUID vlastního kontextu  
 Pokud identifikátor GUID příslušného kontextu příkazu ještě není definovaný, můžete ho definovat ve VSPackage a pak ho programovat jako aktivní nebo neaktivní, jak je potřeba k řízení viditelnosti příkazů.  
  
1. Zaregistrujte identifikátory GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.  
  
2. Získejte stav GUID kontextu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.  
  
3. Zapněte a vypněte kontextové identifikátory GUID voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.  
  
    > [!CAUTION]
    > Ujistěte se, že VSPackage nemá vliv na žádné existující identifikátory GUID kontextu, protože na nich mohou být závislé jiné sady VSPackage.  
  
## <a name="see-also"></a>Viz také  
 [Objekty kontextu výběru](../../extensibility/internals/selection-context-objects.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
