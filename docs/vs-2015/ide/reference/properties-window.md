---
title: Okno vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3faa4b9e0bf7d0ad59a33ed93f895a83e6ff8dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282370"
---
# <a name="properties-window"></a>Okno vlastností
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Toto okno k zobrazení a změna vlastností návrhu a událostí vybraných objektů, které se nacházejí v editorech a návrhářích. Můžete také použít **vlastnosti** okna k úpravám a zobrazování souborů, projektů a vlastností řešení. Můžete najít **vlastnosti** na okno **zobrazení** nabídky. Můžete také otevřít ji stisknutím klávesy F4 nebo zadáním **vlastnosti** v **Snadné spuštění** okna.  
  
 **Vlastnosti** okno zobrazuje různé typy editačních polí v závislosti na potřebách určité vlastnosti. Tato editační pole zahrnout editační políčka, rozevírací seznamy a odkazy na vlastní editor dialogových oknech. Vlastnosti zobrazené šedě jsou jen pro čtení.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Název objektu  
 Zobrazí seznam aktuálně vybraný objekt nebo objekty. Jsou zobrazeny pouze objekty z aktivního editoru nebo návrháře. Když vyberete více objektů, zobrazí se pouze vlastnosti, které jsou společné pro všechny vybrané objekty.  
  
 Zařazených do kategorií  
 Uvádí všechny vlastnosti a hodnoty vlastností pro vybraný objekt podle kategorie. Můžete sbalit kategorii a snížit počet viditelných vlastností. Když rozbalíte nebo sbalíte kategorii, zobrazí se znak plus (+) nebo minus (-) nalevo od názvu kategorie. Kategorie jsou uvedeny podle abecedy.  
  
 Abecední seznam  
 Seřadí podle abecedy všechny vlastnosti doby návrhu a události vybraných objektů. Chcete-li upravit nezašedlou vlastnost, klikněte na buňku napravo a zadejte změny.  
  
 Stránky vlastností  
 Zobrazí **stránky vlastností** dialogové okno nebo **Návrháře projektu** pro vybranou položku. Stránky vlastností zobrazí podmnožinu, stejnou nebo nadmnožinu vlastností dostupných v **vlastnosti** okna. Toto tlačítko slouží k zobrazení a úpravám vlastností vztahujících se k aktivní konfiguraci projektu.  
  
 Vlastnosti  
 Zobrazí vlastnosti objektu. Mnoho objektů má také události, které lze zobrazit pomocí **vlastnosti** okna.  
  
 Řadit podle zdroje vlastnosti  
 Vlastnosti skupiny podle zdroje, jako je dědičnost, využívají styly a vazby. K dispozici pouze při úpravách souborů XAML v návrháři.  
  
 Události  
 Zobrazí události objektu.  
  
> [!NOTE]
>  To **vlastnosti** ovládací prvek panelu nástrojů okna je pouze k dispozici, když je formulář nebo návrhář ovládacího prvku je aktivní v kontextu [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektu. Při úpravách souborů XAML, události se zobrazí na samostatné kartě v okně Vlastnosti.  
  
 Zprávy  
 Obsahuje seznam všech zpráv Windows. Umožňuje přidat nebo odstranit zadané funkce obslužné rutiny pro zprávy zadané pro vybranou třídu.  
  
> [!NOTE]
>  To **vlastnosti** ovládací prvek panelu nástrojů okna je k dispozici pouze při **zobrazení tříd** aktivní okno v kontextu [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektu.  
  
 Overrides  
 Obsahuje seznam všech virtuálních funkcí pro vybranou třídu a umožňuje přidat nebo odstranit přepisující funkce.  
  
> [!NOTE]
>  To **vlastnosti** ovládací prvek panelu nástrojů okna je k dispozici pouze při **zobrazení tříd** aktivní okno v kontextu [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektu.  
  
 Podokno s popisem  
 Zobrazuje typ vlastnosti a krátký popis vlastnosti. Popis vlastnosti vypínat a zapínat pomocí příkazu popis v místní nabídce můžete vypnout.  
  
> [!NOTE]
>  To **vlastnosti** ovládací prvek panelu nástrojů okna není k dispozici při úpravách souborů XAML v návrháři.  
  
 Zobrazení miniatur  
 Zobrazí vizuální znázornění aktuálně vybraného prvku při úpravách souborů XAML v návrháři.  
  
 Hledat  
 Poskytuje funkce vyhledávání pro vlastnosti a události při úpravách souborů XAML v návrháři. Vyhledávací pole reaguje na částečné slovní vyhledávání a aktualizuje výsledky hledání během psaní.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)   
 [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)



