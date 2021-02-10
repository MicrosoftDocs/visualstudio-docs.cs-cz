---
title: Okno vlastností
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ff6435aa006de851a14f4f04570d086a86a5999
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967979"
---
# <a name="properties-window"></a>Vlastnosti – okno

Pomocí tohoto okna můžete zobrazit a změnit vlastnosti doby návrhu a události vybraných objektů, které jsou umístěny v editorech a návrhářích. Můžete také použít okno **vlastnosti** pro úpravu a zobrazení souboru, projektu a vlastností řešení. Okno **vlastnosti** můžete najít v nabídce **zobrazení** . Můžete ho také otevřít stisknutím klávesy **F4** nebo zadáním **vlastností** do vyhledávacího pole.

V okně **vlastnosti** se zobrazují různé typy editačních polí v závislosti na potřebách konkrétní vlastnosti. Tato pole pro úpravy obsahují pole pro úpravy, rozevírací seznamy a odkazy na dialogová okna vlastního editoru. Vlastnosti zobrazené šedě jsou jen pro čtení.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

Název objektu \
Vypíše aktuálně vybraný objekt nebo objekty. Viditelné jsou pouze objekty z aktivního editoru nebo návrháře. Když vyberete více objektů, zobrazí se pouze vlastnosti společné pro všechny vybrané objekty.

Dané
Zobrazí seznam všech vlastností a hodnot vlastností pro vybraný objekt podle kategorie. Můžete sbalit kategorii a snížit tak počet viditelných vlastností. Když rozbalíte nebo sbalíte kategorii, zobrazí se znaménko plus (+) nebo minus (-) nalevo od názvu kategorie. Kategorie jsou uvedeny v abecedním pořadí.

Abecední
Abecedně řadí všechny vlastnosti a události pro vybrané objekty v době návrhu. Chcete-li upravit neztlumenou vlastnost, klikněte na buňku vpravo a zadejte změny.

Stránky vlastností \
Zobrazí dialogové okno **stránky vlastností** nebo **Návrháře projektu** pro vybranou položku. Stránky vlastností zobrazují podmnožinu, stejnou nebo nadmnožinu vlastností, které jsou k dispozici v okně **vlastnosti** . Pomocí tohoto tlačítka můžete zobrazit a upravit vlastnosti týkající se aktivní konfigurace projektu.

Vlastnosti
Zobrazí vlastnosti objektu. Mnoho objektů má také události, které lze zobrazit v okně **vlastnosti** .

Seřadit podle zdroje vlastnosti \
Seskupuje vlastnosti podle zdroje, jako je dědičnost, použité styly a vazby. K dispozici pouze při úpravách souborů XAML v návrháři.

Událost
Zobrazí události pro objekt.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici pouze v případě, že je formulář nebo návrhář ovládacího prvku aktivní v kontextu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Při úpravách souborů XAML se události zobrazí na samostatné kartě v okně Vlastnosti.

Zprávy
Zobrazí všechny zprávy systému Windows. Umožňuje přidat nebo odstranit zadané funkce obslužných rutin pro zprávy poskytované pro vybranou třídu.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici, pouze pokud je **zobrazení tříd** aktivním oknem v kontextu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Těžuje
Zobrazí seznam všech virtuálních funkcí pro vybranou třídu a umožňuje přidat nebo odstranit přepisování funkcí.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** je k dispozici, pouze pokud je **zobrazení tříd** aktivním oknem v kontextu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Podokno popisu \
Zobrazuje typ vlastnosti a krátký popis vlastnosti. Popis vlastnosti můžete změnit na vypnuto a pomocí příkazu popis v místní nabídce.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **vlastnosti** není při úpravách souborů XAML v Návrháři k dispozici.

Zobrazení miniatur \
Zobrazuje vizuální znázornění aktuálně vybraného prvku při úpravách souborů XAML v návrháři.

Nápovědě
Poskytuje vyhledávací funkci pro vlastnosti a události při úpravách souborů XAML v návrháři. Vyhledávací pole reaguje na částečné slovní hledání a aktualizuje výsledky hledání při psaní.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
