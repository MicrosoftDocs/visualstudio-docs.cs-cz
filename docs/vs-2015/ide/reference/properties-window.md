---
title: Okno vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662077"
---
# <a name="properties-window"></a>Okno vlastností
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí tohoto okna můžete zobrazit a změnit vlastnosti doby návrhu a události vybraných objektů, které jsou umístěny v editorech a návrhářích. Můžete také použít okno **vlastnosti** pro úpravu a zobrazení souboru, projektu a vlastností řešení. Okno **vlastnosti** můžete najít v nabídce **zobrazení** . Můžete ho také otevřít stisknutím klávesy F4 nebo zadáním **vlastnosti** v okně **Snadné spuštění** .

 V okně **vlastnosti** se zobrazují různé typy editačních polí v závislosti na potřebách konkrétní vlastnosti. Tato pole pro úpravy obsahují pole pro úpravy, rozevírací seznamy a odkazy na dialogová okna vlastního editoru. Vlastnosti zobrazené šedě jsou jen pro čtení.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Název objektu vypíše aktuálně vybraný objekt nebo objekty. Viditelné jsou pouze objekty z aktivního editoru nebo návrháře. Když vyberete více objektů, zobrazí se pouze vlastnosti společné pro všechny vybrané objekty.

 Kategorizuje seznam všech vlastností a hodnot vlastností pro vybraný objekt podle kategorie. Můžete sbalit kategorii a snížit tak počet viditelných vlastností. Když rozbalíte nebo sbalíte kategorii, zobrazí se znaménko plus (+) nebo minus (-) nalevo od názvu kategorie. Kategorie jsou uvedeny v abecedním pořadí.

 Abecední abecedně řadí všechny vlastnosti a události v době návrhu pro vybrané objekty. Chcete-li upravit neztlumenou vlastnost, klikněte na buňku vpravo a zadejte změny.

 Na stránkách vlastností se zobrazí dialogové okno **stránky vlastností** nebo **Návrhář projektu** pro vybranou položku. Stránky vlastností zobrazují podmnožinu, stejnou nebo nadmnožinu vlastností, které jsou k dispozici v okně **vlastnosti** . Pomocí tohoto tlačítka můžete zobrazit a upravit vlastnosti týkající se aktivní konfigurace projektu.

 Vlastnosti zobrazí vlastnosti objektu. Mnoho objektů má také události, které lze zobrazit v okně **vlastnosti** .

 Seřadit podle vlastností zdrojového seskupení vlastností podle zdroje, jako je dědění, aplikované styly a vazby. K dispozici pouze při úpravách souborů XAML v návrháři.

 Události zobrazí události pro objekt.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici pouze v případě, že je formulář nebo návrhář ovládacího prvku aktivní v kontextu projektu [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Při úpravách souborů XAML se události zobrazí na samostatné kartě v okně Vlastnosti.

 Zprávy obsahují seznam všech zpráv systému Windows. Umožňuje přidat nebo odstranit zadané funkce obslužných rutin pro zprávy poskytované pro vybranou třídu.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici, pouze pokud je **zobrazení tříd** aktivním oknem v kontextu projektu [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 Přepíše seznam všech virtuálních funkcí pro vybranou třídu a umožňuje přidat nebo odstranit přepisování funkcí.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici, pouze pokud je **zobrazení tříd** aktivním oknem v kontextu projektu [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 Podokno popis zobrazuje typ vlastnosti a krátký popis vlastnosti. Popis vlastnosti můžete změnit na vypnuto a pomocí příkazu popis v místní nabídce.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** není při úpravách souborů XAML v Návrháři k dispozici.

 Zobrazení miniatur zobrazuje vizuální znázornění aktuálně vybraného prvku při úpravách souborů XAML v návrháři.

 Při úpravách souborů XAML v Návrháři poskytuje funkce Search vyhledávací funkci pro vlastnosti a události. Vyhledávací pole reaguje na částečné slovní hledání a aktualizuje výsledky hledání při psaní.

## <a name="see-also"></a>Viz také
 [Vlastnosti projektu – odkaz](../../ide/reference/project-properties-reference.md) na [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
