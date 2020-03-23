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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1be1d4fa9f1b088547bb21dfb64254209783d7e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565705"
---
# <a name="properties-window"></a>Vlastnosti – okno

Toto okno slouží k zobrazení a změně vlastností návrhu a událostí vybraných objektů, které jsou umístěny v editorech a návrhářích. Okno **Vlastnosti** můžete také použít k úpravám a zobrazení vlastností souboru, projektu a řešení. Okno **Vlastnosti** najdete v nabídce **Zobrazení.** Můžete ji také otevřít stisknutím **klávesy F4** nebo zadáním **příkazu Vlastnosti** do vyhledávacího pole.

Okno **Vlastnosti** zobrazuje různé typy polí pro úpravy v závislosti na potřebách určité vlastnosti. Tato editační pole zahrnují editační pole, rozevírací seznamy a odkazy na vlastní dialogová okna editoru. Vlastnosti zobrazené šedě jsou jen pro čtení.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

Název objektu\
Zobrazí seznam aktuálně vybraných objektů nebo objektů. Viditelné jsou pouze objekty z aktivního editoru nebo návrháře. Když vyberete více objektů, zobrazí se pouze vlastnosti společné pro všechny vybrané objekty.

Kategorizováno\
Zobrazí seznam všech vlastností a hodnot vlastností vybraného objektu podle kategorie. Kategorii můžete sbalit, abyste snížili počet viditelných vlastností. Když rozbalíte nebo sbalíte kategorii, zobrazí se nalevo od názvu kategorie plus (+) nebo mínus (-). Kategorie jsou uvedeny abecedně.

Abecední\
Abecedně seřadí všechny vlastnosti a události návrhu pro vybrané objekty. Chcete-li upravit neztlumenou vlastnost, klepněte do buňky vpravo a zadejte změny.

Stránky vlastností\
Zobrazí dialogové okno **Stránky vlastností** nebo **Návrhář projektu** pro vybranou položku. Stránky vlastností zobrazí podmnožinu, stejnou nebo nadmnožinu vlastností dostupných v okně **Vlastnosti.** Toto tlačítko slouží k zobrazení a úpravám vlastností souvisejících s aktivní konfigurací projektu.

Vlastnosti\
Zobrazí vlastnosti objektu. Mnoho objektů má také události, které lze zobrazit pomocí okna **Vlastnosti.**

Seřadit podle zdroje vlastností\
Seskupí vlastnosti podle zdroje, například dědičnost, použité styly a vazby. K dispozici pouze při úpravách souborů XAML v návrháři.

Události\
Zobrazí události objektu.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **Vlastnosti** je k dispozici [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pouze v případě, že je v kontextu projektu aktivní návrhář formuláře nebo ovládacího prvku. Při úpravách souborů XAML se události zobrazují na samostatné kartě okna vlastností.

Zprávy\
Zobrazí seznam všech zpráv systému Windows. Umožňuje přidat nebo odstranit zadané funkce obslužné rutiny pro zprávy poskytované pro vybranou třídu.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **Vlastnosti** je k dispozici [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pouze v **případě, že zobrazení třídy** je aktivní okno v kontextu projektu.

Lokální změny\
Zobrazí seznam všech virtuálních funkcí pro vybranou třídu a umožní vám přidat nebo odstranit přepsání funkcí.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **Vlastnosti** je k dispozici [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pouze v **případě, že zobrazení třídy** je aktivní okno v kontextu projektu.

Podokno popis\
Zobrazuje typ vlastnosti a krátký popis vlastnosti. Popis vlastnosti můžete vypnout a zapnout pomocí příkazu Popis v místní nabídce.

> [!NOTE]
> Tento ovládací prvek panelu nástrojů okna **Vlastnosti** není k dispozici při úpravách souborů XAML v návrháři.

Zobrazení miniatur\
Zobrazuje vizuální reprezentaci aktuálně vybraného prvku při úpravách souborů XAML v návrháři.

Hledat\
Poskytuje funkci Hledat vlastnosti a události při úpravách souborů XAML v návrháři. Vyhledávací pole reaguje na částečné hledání slov a aktualizuje výsledky hledání při psaní.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
