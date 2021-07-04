---
title: Informace o okně nástroje Průzkumník řešení
description: přečtěte si, jak můžete pomocí okna Průzkumník řešení nástrojů v Visual Studio vytvořit & spravovat soubory, projekty a řešení.
ms.date: 06/29/2021
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbbae8b974a7e88abffd9a12eb253dfea6c7165b
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280487"
---
# <a name="how-to-use-solution-explorer"></a>Jak používat Průzkumník řešení

Můžete použít okno Průzkumník řešení nástrojů k vytvoření & správě řešení a projektů a k zobrazení & interakce s vaším kódem. V tomto článku se podíváme na možnosti uživatelského rozhraní (UI), které vám to pomůžou udělat.

> [!NOTE]
> toto téma se vztahuje pouze na Visual Studio v Windows.

## <a name="solution-explorer-tool-window"></a>Okno nástroje Průzkumník řešení

začněte tím, že se podíváme na okno Průzkumník řešení tool v [rozhraní IDE Visual Studio](../get-started/visual-studio-ide.md)s otevřeným konzolovým řešením C#, která má dva projekty.

[![Okno Průzkumník řešení nástrojů v Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Okno nástroje obsahuje následující prvky uživatelského rozhraní (uživatelské rozhraní):

- **Řádek nabídek**, kde můžete určit, jak se budou soubory zobrazovat
- **Panel hledání**, kde můžete vyhledat konkrétní soubory a typy souborů
- **Hlavní okno**, kde můžete zobrazit a spravovat soubory, projekty a & řešení
- **Uzel řešení**, kde můžete spravovat vaše řešení
- **uzel Project**, kde můžete spravovat projekt (y)
- **Uzel závislosti**, kde můžete spravovat řešení & závislosti projektu
- **Uzel programu**, kde můžete zobrazit, upravit a spravovat program nebo aplikaci (aplikace)
- **[karta změny git](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)**, kde můžete použít GitHub Git & v rámci Visual Studio ke spolupráci na projektech s týmem

> [!TIP]
> pokud nevidíte okno Průzkumník řešení tool, můžete ho otevřít z panelu nabídek Visual Studio pomocí **zobrazení**  >  **Průzkumník řešení** nebo stisknutím klávesy **Ctrl** + **Alt** + **L**.

## <a name="solution-explorer-menu-bar"></a>Řádek nabídek Průzkumník řešení

Chcete-li pokračovat, podíváme se na Průzkumník řešení panelu nabídek.

![Průzkumník řešení řádku nabídek v Visual Studio.](media/solution-explorer-menu-bar.png)

Řádek nabídek obsahuje následující prvky uživatelského rozhraní, zleva doprava:

- Tlačítko **zpět** pro přepínání mezi výsledky hledání
- Tlačítko **pro přeposílání** pro přepínání mezi výsledky hledání
- Tlačítko **Domů** pro návrat k výchozímu zobrazení
- **Přepínač** pro přepínání mezi řešeními a dostupnými zobrazeními
- **Nedokončené změny** – tlačítko filtru & rozevírací nabídka pro zobrazení otevřených souborů nebo souborů s nedokončenými změnami
- Tlačítko **synchronizovat s aktivním dokumentem** pro vyhledání souboru z editoru kódu
- Tlačítko **aktualizovat** , které se zobrazí jenom v případě, že vyberete závislost, jako je například funkce nebo balíček
- **Sbalit vše** – tlačítko pro sbalení zobrazení souboru v hlavním okně
- Tlačítko **Zobrazit všechny soubory** , chcete-li zobrazit všechny soubory včetně [nenačtených projektů](filtered-solutions.md#toggle-unloaded-project-visibility)
- Tlačítko **vlastnosti** , chcete-li zobrazit a změnit nastavení pro konkrétní soubory a součásti
- **Náhled vybraných položek** – tlačítko pro zobrazení vybraného souboru nebo komponenty v editoru kódu

### <a name="solution-explorer-right-click-context-menu"></a>Průzkumník řešení místní nabídce kliknutím pravým tlačítkem myši

V Průzkumník řešení existuje několik vlastností souboru, se kterými můžete pracovat pomocí místní nabídky po kliknutí pravým tlačítkem myši. Další informace o možnostech kontextové nabídky po kliknutí pravým tlačítkem myši najdete na stránce [Správa projektů a vlastností řešení](managing-project-and-solution-properties.md) .

## <a name="see-also"></a>Viz také

- [Co jsou řešení a projekty v Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Přizpůsobení rozložení oken v Visual Studio](customizing-window-layouts-in-visual-studio.md)
