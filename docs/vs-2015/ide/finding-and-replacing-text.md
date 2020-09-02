---
title: Hledání a nahrazování textu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 025ba2eb95514efc740d1f8f7b3bf674d6bf237a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645638"
---
# <a name="finding-and-replacing-text"></a>Hledání a nahrazení textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyhledat a nahradit text v editoru kódu sady Visual Studio a určitých textových oknech s textem, jako jsou například okna **výsledků hledání** , pomocí ovládacího prvku **Najít a nahradit** nebo **Vyhledat/nahradit v souborech**. Můžete také Hledat a nahrazovat v některých oknech návrháře, jako je například Návrhář XAML a Návrhář model Windows Forms a okna nástrojů.

 Můžete určit rozsah hledání na aktuální dokument, aktuální řešení nebo vlastní sadu složek. Můžete také zadat sadu přípon názvů souborů pro vyhledávání ve více souborech. Můžete přizpůsobit syntaxi hledání pomocí regulárních výrazů .NET.

 Chcete-li najít a nahradit regulární výrazy, přečtěte si téma [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> Pole **Najít/příkaz** je stále k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení se už nezobrazuje. Pole **Najít/příkaz** můžete zobrazit tak, že na panelu nástrojů **Standard** kliknete na **tlačítko Přidat nebo odebrat tlačítka** a pak zvolíte **Najít**. Další informace najdete v části [Najít/příkazové okno](../ide/find-command-box.md).

## <a name="find-and-replace-control"></a>Najít a nahradit ovládací prvek
 Ovládací prvek **Najít a nahradit** se zobrazí v pravém horním rohu okna Editor kódu. Ovládací prvek **Najít a nahradit** okamžitě zvýrazní všechny výskyty daného hledaného řetězce v aktuálním dokumentu. Můžete přecházet z jednoho výskytu na jiný kliknutím na tlačítko **Najít další** nebo tlačítko **Najít předchozí** v ovládacím prvku hledání.

 K možnostem nahrazení se dostanete tak, že vyberete tlačítko vedle textového pole **Najít** . Chcete-li provést nahrazení v jednom okamžiku, klikněte na tlačítko **nahradit další** vedle textového pole **nahradit** . Chcete-li nahradit všechny shody, klikněte na tlačítko **Nahradit vše** .

 Chcete-li změnit barvu zvýraznění shody, zvolte nabídku **nástroje** , vyberte možnost **Možnosti**a pak zvolte možnost **prostředí**a vyberte možnost **písma a barvy**. V seznamu **Zobrazit nastavení pro** vyberte možnost **textový editor**a potom v seznamu **Zobrazit položky** vyberte možnost **Najít zvýraznění (rozšíření)**.

### <a name="searching-tool-windows"></a>Hledání v oknech nástrojů
 Můžete použít ovládací prvek **Najít** v okně Code nebo text, jako je například **výstupní** okna a **výsledky hledání** v oknech výsledků, a to tak, že v nabídce **Upravit** vyberete **Najít a nahradit** nebo (CTRL + F).

 Verze ovládacího prvku Find je také k dispozici v některých oknech nástrojů. Můžete například filtrovat seznam ovládacích prvků v okně **panelu nástrojů** zadáním textu do vyhledávacího pole. Další okna nástrojů, která teď umožňují hledání obsahu, zahrnují **Průzkumník řešení**, okno **vlastnosti** a **Team Explorer**, mimo jiné.

## <a name="findreplace-in-files"></a>Najít/nahradit v souborech
 Funkce **Najít/nahradit v souborech** funguje jako ovládací prvek **Najít a nahradit** s tím rozdílem, že můžete definovat rozsah pro hledání. V editoru můžete nejen Hledat v aktuálním otevřeném souboru, ale můžete také prohledávat všechny otevřené dokumenty, celé řešení, aktuální projekt a vybrané sady složek. Můžete také Hledat podle přípony názvu souboru. Chcete-li získat přístup k dialogovému oknu **Najít/nahradit v souborech** , vyberte možnost **Najít a nahradit** v nabídce **Upravit** (nebo CTRL + SHIFT + F).

 Když zvolíte **Najít vše**, otevře se okno **výsledky hledání** a zobrazí se seznam shod pro vaše hledání. Výběr výsledku v seznamu zobrazí přidružený soubor a zvýrazní shodu. Pokud soubor ještě není otevřen pro úpravy, je otevřen na kartě náhledu na pravé straně karty. Pomocí ovládacího prvku **hledání** můžete vyhledat seznam **výsledků hledání** .

### <a name="creating-custom-search-folder-sets"></a>Vytváření vlastních sad složek výsledků hledání
 Rozsah vyhledávání můžete definovat tak, že kliknete na tlačítko **Zvolit složky výsledků hledání** (vypadá to jako **...**) vedle pole **Hledat v** . V dialogovém okně **Zvolit složky výsledků hledání** můžete zadat sadu složek, ve kterých se má hledat, a uložit specifikaci, aby ji bylo možné znovu použít později. Složky na vzdáleném počítači můžete zadat pouze v případě, že je namapovaná jednotka na místní počítač.

### <a name="creating-custom-component-sets"></a>Vytváření vlastních sad součástí
 Sady součástí můžete definovat jako rozsah hledání tak, že vyberete tlačítko **Upravit sadu vlastních komponent** vedle pole **Hledat v** . Můžete určit nainstalované komponenty .NET nebo COM, projekty sady Visual Studio, které jsou součástí vašeho řešení, nebo jakékoli sestavení nebo knihovnu typů (. dll,. tlb,. olb,. exe nebo. ocx). Chcete-li hledat odkazy, vyberte pole **Hledat v odkazech** .

## <a name="see-also"></a>Viz také
 [Používání regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
