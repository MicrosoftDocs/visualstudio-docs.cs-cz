---
title: Rozšíření a přizpůsobení oken nástrojů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711821"
---
# <a name="extend-and-customize-tool-windows"></a>Rozšiřování a přizpůsobení oken nástrojů
Visual Studio poskytuje několik různých typů oken, například okna nástrojů, okna dokumentů a dialogová okna. Další okna, jako je okno **vlastnosti** , okno **výstup** a okno **seznam úkolů** , jsou typy oken nástrojů.

## <a name="tool-windows"></a>Okna nástrojů
 Okna nástrojů sady Visual Studio jsou obvykle okna jen pro čtení, která nejsou založená na souborech. V takovém případě se liší od oken dokumentu, které zobrazují soubory v režimu pro čtení i zápis. Příklady oken nástrojů jsou **panely nástrojů**, **Průzkumník řešení**, okno **vlastnosti** a **webový prohlížeč** .

 Chcete-li zjistit, jak vytvořit jednoduchý panel nástrojů, přečtěte si téma [Přidání okna nástroje](../extensibility/adding-a-tool-window.md).

 Chcete-li zaregistrovat okno nástrojů v aplikaci Visual Studio, přečtěte si téma [registrace okna nástroje](../extensibility/registering-a-tool-window.md).

 Okna nástrojů jsou ve výchozím nastavení jediná instance, což znamená, že v jednom okamžiku může být otevřena pouze jedna instance okna nástroje. Po otevření okna nástroje s jednou instancí zůstane otevřené, dokud se IDE nezavře. Při zavření okna nástroje s jednou instancí se změní pouze jeho viditelnost. Můžete také vytvořit okna nástrojů s více instancemi, aby bylo možné současně otevřít více instancí okna. Další informace najdete v tématu [Vytvoření nástroje s více instancemi](../extensibility/creating-a-multi-instance-tool-window.md) .

 Okna nástrojů mohou být *Dynamická*, což znamená, že jsou viditelné vždy, když platí jejich související kontext uživatelského rozhraní. Použití automatického viditelnosti může snížit zbytečně velký počet oken v integrovaném vývojovém prostředí (IDE). Další informace naleznete v tématu [otevření dynamického okna nástroje](../extensibility/opening-a-dynamic-tool-window.md).

 Okna nástrojů lze ukotvit, plovoucí nebo se záložkami v rámci rámce dokumentu. Rámec okna nástroje je poskytován rozhraním IDE a slouží k řízení velikosti, umístění, stavu ukotvení a dalších trvalých vlastností. Obsah se zobrazí v podokně okna nástroje. Výchozí velikost a umístění platí pouze při prvním otevření okna nástroje; po tom, co je stav okna nástroje trvalé.

 Podokna okna nástroje mohou hostovat uživatelské ovládací prvky WPF a podporují panely nástrojů. Můžete přepsat <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> vlastnost a vrátit tak popisovač hostovaného ovládacího prvku.

 Do oken nástrojů můžete přidat mnoho různých funkcí. Například můžete přidat panel nástrojů: [Přidat panel nástrojů do panelu](../extensibility/adding-a-toolbar-to-a-tool-window.md) nástrojů nebo místní nabídky: [Přidat místní nabídku do okna nástroje](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Můžete přidat ovládací prvek hledání, který umožňuje hledat položky v okně nástroje: [Přidat hledání do okna nástroje](../extensibility/adding-search-to-a-tool-window.md).

 Můžete se přihlásit k odběru událostí okna nástroje: [přihlášení k odběru události](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Roztažení stávajících oken nástrojů
 Můžete přidat informace o okně nástroje na novou stránku **Možnosti** a nové nastavení na stránce **vlastnosti** a zapsat do oken **seznam úkolů** a **výstup** . Další informace najdete v tématu věnovaném [rozšiřování vlastností, seznam úkolů, výstupu a možností Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modální dialogová okna
 V rozšíření sady Visual Studio byste měli vytvořit modální dialogová okna jejich odvozením z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , což umožňuje jejich kontrolu a zbytek uživatelského rozhraní. Další informace najdete v tématu [vytváření a Správa modálních](../extensibility/creating-and-managing-modal-dialog-boxes.md)dialogových oken.

## <a name="see-also"></a>Viz také
- [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Roztažení projektů](../extensibility/extending-projects.md)
- [Rozšiřování řešení](../extensibility/extending-solutions.md)
