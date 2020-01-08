---
title: Webový prohlížeč, prostředí, dialogové okno Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Environment.Web Browser
- VS.ToolsOptionsPages.Environment.WebBrowser
- VS.ToolsOptionsPages.Environment.Web_Browser
helpviewer_keywords:
- browsers, customizing
- searching, search page for Web browser
- Web browsers, customizing
- searches, default Web browser search page
- URLs, specifying VS home page
- home page
- Options dialog box, Web settings
- Internet Explorer, setting options
ms.assetid: 586db4eb-032d-4cb5-93a6-a7c14de1ae49
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8915bef3bba477dd515b1d176971cfb9949e9899
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596499"
---
# <a name="options-dialog-box-environment--web-browser"></a>Dialogové okno Možnosti: prostředí \> webový prohlížeč

Nastaví možnosti pro interní webový prohlížeč i Internet Explorer. Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na tlačítko **Možnosti** v nabídce **nástroje** , rozbalte složku **prostředí** a vyberte možnost **webový prohlížeč**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../environment-settings.md#reset-settings).

> [!IMPORTANT]
> Otevřením určitých souborů nebo komponent z webu můžete v počítači spustit kód.

## <a name="home-page"></a>Domovská stránka

Nastaví stránku, která se zobrazí, když otevřete webový prohlížeč IDE.

## <a name="search-page"></a>Stránka hledání

Umožňuje určit stránku vyhledávání pro interní webový prohlížeč. Toto umístění se může lišit od stránky vyhledávání používané instancemi prohlížeče Internet Explorer, které jsou spouštěny mimo integrované vývojové prostředí (IDE).

## <a name="view-source-in"></a>Zobrazit zdroj v

Nastaví Editor použitý k otevření webové stránky při výběru možnosti **Zobrazit zdroj** na stránce z interního webového prohlížeče.

- **Editor zdrojového kódu** Tuto možnost vyberte, pokud chcete zobrazit zdroj v [editoru](../../ide/writing-code-in-the-code-and-text-editor.md).

- **Editor HTML** Tuto možnost vyberte, pokud chcete zobrazit zdroj v [Návrháři HTML](https://msdn.microsoft.com/Library/640043cc-3657-4677-a091-bc315e636477). Pomocí tohoto výběru můžete upravit webovou stránku v jednom ze dvou zobrazení: zobrazení Návrh nebo standardní textové zobrazení zdroje.

- **Externí editor** Tuto možnost vyberte, pokud chcete zobrazit zdroj v jiném editoru. Zadejte cestu libovolného editoru, který zvolíte, například Notepad. exe.

## <a name="internet-explorer-options"></a>Možnosti Internet Exploreru

Kliknutím můžete změnit možnosti pro Internet Explorer v dialogovém okně **Vlastnosti Internetu** . Změny provedené v tomto dialogovém okně mají vliv na vnitřní webový prohlížeč a instance aplikace Internet Explorer, které jsou iniciovány mimo Visual Studio IDE (například z nabídky Start).

> [!NOTE]
> Pomocí dialogového okna **Procházet s** můžete nahradit interní webový prohlížeč sady Visual Studio prohlížečem podle vašeho výběru. Můžete získat přístup k dialogovému oknu procházet s pomocí kliknutí pravým tlačítkem nebo místní nabídky, například souboru HTML v projektu.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [HTML Designer](https://msdn.microsoft.com/Library/640043cc-3657-4677-a091-bc315e636477)
