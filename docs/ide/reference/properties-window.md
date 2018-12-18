---
title: Okno vlastností
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2848a8197dfe62836918de51ae6e7d01677dac6d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947297"
---
# <a name="properties-window"></a>Okno vlastností
Toto okno slouží k zobrazení a změna vlastnosti doby návrhu a události vybraných objektů, které se nacházejí v editorech a návrhářích. Můžete také **vlastnosti** okno Úprava a zobrazení souborů, projektů a řešení vlastnosti. Můžete najít **vlastnosti** okno na **zobrazení** nabídky. Můžete také otevřít ho stisknutím klávesy F4 nebo zadáním **vlastnosti** v **Snadné spuštění** okno.

 **Vlastnosti** zobrazuje různé typy úpravy pole, v závislosti na potřebách určité vlastnosti. Tyto úpravy polí zahrnují upravit pole, rozevírací seznamy a odkazy na vlastního editoru dialogových oken. Vlastnosti zobrazené šedě jsou jen pro čtení.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Název objektu

 Zobrazí seznam aktuálně vybraný objekt nebo objekty. Pouze objekty z aktivní editor nebo designer jsou viditelné. Když vyberete více objektů, zobrazí se pouze vlastnosti, které jsou společné pro všechny vybrané objekty.

 Zařazené do kategorie

 Podle kategorie uvádí všechny vlastnosti a hodnoty vlastností pro vybraný objekt. Lze sbalit kategorii a snížit počet viditelné vlastnosti. Když rozbalit nebo Sbalit kategorii, uvidíte plus (+) nebo minus (-) nalevo od název kategorie. Kategorie jsou uvedeny podle abecedy.

 Abecedně

 Abecedně seřadí všechny vlastnosti doby návrhu a události pro vybrané objekty. Chcete-li upravit vlastnost zrušeno šedé zobrazení, klikněte na buňku se záhlavím vpravo a zadejte změny.

 Stránky vlastností

 Zobrazí **stránky vlastností** dialogové okno nebo **Návrhář projektu** pro vybranou položku. Stránky vlastností zobrazí podmnožinu stejné nebo nadmnožinou vlastnosti dostupné ve **vlastnosti** okno. Toto tlačítko slouží k zobrazení a úprava vlastností souvisejících s aktivní konfigurace vašeho projektu.

 Vlastnosti

 Zobrazí vlastnosti pro objekt. Mnoho objektů také mít události, které lze zobrazit pomocí **vlastnosti** okno.

 Řazení podle vlastnosti zdroje

 Vlastnosti skupiny zdrojem, jako je například dědičnosti, použity styly a vazeb. K dispozici jenom při úpravě souborů XAML v návrháři.

 Události

 Zobrazuje události pro objekt.

> [!NOTE]
> To **vlastnosti** okno toolbar – ovládací prvek je dostupná pouze při formuláře nebo Návrháře řízení je aktivní v kontextu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Při úpravě soubory XAML, zobrazí se události na samostatné kartě okna Vlastnosti.


 Zprávy

 Zobrazí seznam všech zpráv systému Windows. Umožňuje přidat nebo odstranit funkce zadaná obslužná rutina pro zprávy uvedené pro vybrané třídy.

> [!NOTE]
> To **vlastnosti** okno toolbar – ovládací prvek je k dispozici pouze při **zobrazení tříd** je v kontextu aktivní okno [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Overrides

 Zobrazí seznam všech virtuálních funkcí pro vybrané třídy a umožňuje přidat nebo odstranit přepsání funkce.

> [!NOTE]
> To **vlastnosti** okno toolbar – ovládací prvek je k dispozici pouze při **zobrazení tříd** je v kontextu aktivní okno [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Podokno s popisem

 Zobrazuje typ vlastnosti a krátký popis vlastnosti. Chcete-li popis vlastnosti a odhlašování pomocí příkazu popis v místní nabídce.

> [!NOTE]
> To **vlastnosti** okno toolbar – ovládací prvek není k dispozici, při úpravě souborů XAML v návrháři.


 Zobrazení miniatur

 Při úpravě souborů XAML v návrháři, zobrazuje vizuální reprezentace aktuálně vybraného elementu.

 Hledat

 Poskytuje funkce hledání pro vlastnosti a události při úpravě souborů XAML v návrháři. Do vyhledávacího pole odpoví na částečné word hledání a aktualizace výsledky hledání během psaní.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)