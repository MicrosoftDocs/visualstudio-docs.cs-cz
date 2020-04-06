---
title: Rozšíření a přizpůsobení nástroje Windows | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711821"
---
# <a name="extend-and-customize-tool-windows"></a>Rozšíření a přizpůsobení oken nástrojů
Visual Studio poskytuje několik různých typů oken, například okna nástrojů, okna dokumentů a dialogová okna. Ostatní okna, například okno **Vlastnosti,** **okno Výstup** a **Seznam úkolů,** jsou typy oken nástrojů.

## <a name="tool-windows"></a>Okna nástrojů
 Okna nástrojů sady Visual Studio jsou obvykle okna jen pro čtení, která nejsou založená na souborech. V tomto se liší od oken dokumentů, které zobrazují soubory v režimu čtení a zápisu. Příklady oken nástrojů jsou **panel nástrojů**, **Průzkumník řešení**, **Vlastnosti** a **webový prohlížeč.**

 Informace o tom, jak vytvořit jednoduché okno nástroje, naleznete [v tématu Přidání okna nástroje](../extensibility/adding-a-tool-window.md).

 Pokud chcete zaregistrovat okno nástroje v sadě Visual Studio, přečtěte si informace [o registraci okna nástroje](../extensibility/registering-a-tool-window.md).

 Okna nástrojů jsou ve výchozím nastavení jednoinstancí, což znamená, že současně může být otevřena pouze jedna instance okna nástroje. Po otevření okna nástroje jedné instance zůstane otevřené, dokud se zavře ide. Když zavřete okno nástroje jedné instance, změní se pouze jeho viditelnost. Můžete také vytvořit okna nástrojů s více instancemi, takže více instancí okna může být otevřeno současně. Další informace naleznete [v tématu Vytvoření okna nástroje pro více instancí.](../extensibility/creating-a-multi-instance-tool-window.md)

 Okna nástrojů mohou být *dynamická*, což znamená, že jsou viditelná vždy, když se použije jejich související kontext ui. Použití automatické viditelnosti může snížit nepořádek oken v prostředí IDE. Další informace naleznete [v tématu Otevření okna dynamického nástroje](../extensibility/opening-a-dynamic-tool-window.md).

 Okna nástrojů mohou být ukotvena, plovoucí nebo s kartami v rámečku dokumentu. Rámeček okna nástroje je poskytován rozhraním IDE a slouží k řízení velikosti, umístění, stavu ukotvení a dalších trvalých vlastností. Podokno okna nástroje zobrazuje obsah. Výchozí velikost a umístění platí pouze při prvním otevření okna nástroje. poté je stav okna nástroje trvalý.

 Podokna oken nástrojů mohou hostovat uživatelské ovládací prvky WPF a podporují panely nástrojů. Vlastnost můžete přepsat <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> a vrátit popisovač hostovaného ovládacího prvku.

 Do oken nástrojů můžete přidat mnoho různých funkcí. Můžete například přidat panel nástrojů: [Přidání panelu nástrojů do okna nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md) nebo do místní nabídky: Přidání místní nabídky do okna [nástroje](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Můžete přidat ovládací prvek Hledání, který umožňuje prohledávat položky v okně nástroje: [Přidat hledání do okna nástroje](../extensibility/adding-search-to-a-tool-window.md).

 Můžete se přihlásit k odběru událostí v okně nástroje: [Přihlásit se k odběru události](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Rozšíření existujících oken nástrojů
 Informace o okně nástroje můžete přidat na novou stránku **Možnosti** a nové nastavení na stránce **Vlastnosti,** napište do oken **Seznam úkolů** a **Výstup.** Další informace naleznete [v tématu Rozšíření oken Vlastnosti, Seznam úkolů, Výstup a Možnosti](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modální dialogová okna
 V rozšíření sady Visual Studio byste měli vytvořit modální dialogová okna jejich odvozením z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, což umožňuje jejich řízení a zbytek ui. Další informace naleznete v [tématu Vytvoření a správa modálních dialogových oken](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Viz také
- [Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Rozšířit projekty](../extensibility/extending-projects.md)
- [Rozšířit řešení](../extensibility/extending-solutions.md)
