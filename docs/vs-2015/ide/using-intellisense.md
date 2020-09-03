---
title: Pomocí technologie IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 735f93b2f900b8681a1e9fee490de8e4b697f9e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656450"
---
# <a name="using-intellisense"></a>Používání atributu IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense je obecný termín pro několik funkcí: seznamy členů, informace o parametrech, rychlé informace a dokončování slov. Tyto funkce umožňují získat další informace o kódu, který používáte, zachovat si přehled o parametrech, které píšete, a přidávat volání vlastností a metod s pomocí několika klávesových úhozů.

 Mnoho aspektů technologie IntelliSense je specifických pro jazyk. Další informace o technologii IntelliSense pro různé jazyky naleznete v tématech uvedených v části Viz také.

## <a name="list-members"></a>Vypsat členy
 Po zadání spouštěcího znaku (například tečka ( `.` ) ve spravovaném kódu nebo `::` v jazyce C++) se zobrazí seznam platných členů z typu (nebo oboru názvů). Pokud budete pokračovat v zadávání znaků, seznam bude filtrován tak, aby zahrnoval pouze ty členy, kteří začínají danými znaky.

 Po výběru položky ji můžete vložit do kódu stisknutím klávesy TAB a zadáním mezery. Pokud vyberte položku a zadáte období, položka se zobrazí s uvedenou dobou, která vyvolá jiný seznam členů. Pokud vyberete položku, ale ještě před jejím vložením, zobrazí se rychlé informace pro položku.

 V seznamu členů ikona vlevo představuje typ členu, například obor názvů, třídu, funkci nebo proměnnou. Seznam ikon naleznete v tématu [zobrazení tříd a prohlížeč objektů ikony](../ide/class-view-and-object-browser-icons.md). Seznam může být poměrně dlouhý a posouvat se v něm můžete stisknutím klávesy PAGE UP a PAGE DOWN.

 ![Seznam členů sady Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

 Funkci **vypsat členy** můžete vyvolat ručně zadáním CTRL + J, kliknutím na **Upravit/IntelliSense/seznam členů**nebo kliknutím na tlačítko **seznam členů** na panelu nástrojů editoru. Při vyvolání na prázdném řádku nebo mimo podporovaný rozsah zobrazí seznam symboly v globálním oboru názvů.

 Chcete-li vypnout členy seznamu ve výchozím nastavení (tak, aby se nezobrazily, pokud není výslovně vyvoláno), vyberte možnost **Nástroje/možnosti/všechny jazyky** a zrušte výběr možnosti **Automatické zobrazení členů**. Pokud chcete vypnout seznam členů jenom pro určitý jazyk, přečtěte si **Obecné** nastavení daného jazyka.

 Můžete také změnit nastavení na režim návrhu, ve kterém je do kódu vložen pouze text, který zadáte. Například pokud zadáte identifikátor, který není uveden v seznamu, a stisknete klávesu TAB, v režimu ukončení by vstup nahradil zadaný identifikátor. Chcete-li přepnout mezi režimem dokončení a režimem návrhu, stiskněte kombinaci kláves CTRL + ALT + MEZERNÍK nebo klikněte na tlačítko **Upravit/IntelliSense/přepnout režim dokončení**.

## <a name="parameter-info"></a>Informace o parametrech
 Informace o parametru poskytují informace o počtu, názvech a typech parametrů vyžadovaných metodou, atributem parametru obecného typu (v jazyce C#) nebo šablonou (v jazyce C++).

 Parametr tučně označuje další parametr, který je vyžadován při zadávání funkce. Pro přetížené funkce můžete použít klávesy se šipkami nahoru a dolů a zobrazit tak alternativní informace o parametru pro přetížení funkce.

 ![Informace o parametrech](../ide/media/vs2015-param-info.png "VS2015_param_Info")

 Když opatřujete poznámkami funkce a parametry s komentáři XML dokumentace, komentáře se zobrazí jako informace o parametru. Další informace naleznete v tématu [poskytnutí komentářů kódu XML](../ide/supplying-xml-code-comments.md).

 Informace o parametrech můžete vyvolat ručně kliknutím na **Upravit informace o IntelliSense/parametru**, zadáním kombinace kláves CTRL + SHIFT + MEZERNÍK nebo kliknutím na tlačítko **informace o parametru** na panelu nástrojů editoru.

## <a name="quick-info"></a>Rychlé informace
 Rychlé informace zobrazí úplnou deklaraci pro libovolný identifikátor ve vašem kódu.

 ![Rychlé informace pro Visual Studio](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")

 Když vyberete člena v poli **seznam členů** , zobrazí se také pole rychlé informace.

 ![Informace o parametrech v souboru kódu&#35; jazyka C](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")

 Rychlé informace můžete vyvolat ručně kliknutím na **Upravit/IntelliSense/rychlé informace**, zadáním kombinace kláves CTRL + I nebo kliknutím na tlačítko pro **rychlé informace** na panelu nástrojů editoru.

 Pokud je funkce přetížena, technologie IntelliSense nemusí zobrazit informace pro všechny formy přetížení.

 Rychlé informace v jazyce C++ můžete vypnout nastavením **Možnosti nástroje/možnosti/textový editor/C/C++/Advanced/auto rychlé informace** na `false` .

## <a name="complete-word"></a>Dokončit slovo
 Jakmile zadáte dostatečný počet znaků pro odstranění dvojznačnosti termínu, funkce Dokončit slovo dokončí zbytek proměnné, příkazu nebo názvu funkce. Můžete vyvolat úplné slovo kliknutím na **Upravit/IntelliSense/dokončit slovo**, zadáním kombinace kláves CTRL + MEZERNÍK nebo kliknutím na tlačítko **Dokončit slovo** na panelu nástrojů editoru.

## <a name="intellisense-options"></a>Možnosti technologie IntelliSense
 Možnosti technologie IntelliSense jsou standardně povoleny. Chcete-li je vypnout, klikněte na tlačítko **Nástroje/možnosti/textový editor** a zrušte výběr **informací o parametrech** nebo **Automatické seznamy členů** , pokud nechcete, aby funkce členové seznamu byly.

## <a name="troubleshooting-intellisense"></a>Řešení potíží technologie IntelliSense
 Možnosti technologie IntelliSense nemusí v určitých případech fungovat podle očekávání.

 **Kurzor je pod chybou kódu.** Je možné, že nebudete moci používat technologii IntelliSense, pokud v kódu nad kurzorem existuje nekompletní funkce nebo jiná chyba, protože technologie IntelliSense nemusí být schopna analyzovat prvky kódu. Tento problém lze vyřešit okomentováním odpovídajícího kódu.

 **Kurzor je v komentáři kódu.** IntelliSense nemůžete použít, pokud je kurzor v komentáři ve zdrojovém souboru.

 **Kurzor je v řetězcovém literálu.** IntelliSense nemůžete použít, pokud je kurzor v uvozovkách kolem řetězcového literálu, jako v následujícím příkladu:

```
MessageBox( hWnd, "String literal|") )
```

 **Automatické možnosti jsou vypnuté.** Ve výchozím nastavení funguje technologie IntelliSense automaticky, ale můžete ji zakázat. Použít funkci IntelliSense můžete i v případě, že je zakázáno automatické dokončování.

## <a name="see-also"></a>Viz také
 [Visual Basic specifické](../ide/visual-basic-specific-intellisense.md) technologie IntelliSense [Visual C#](../ide/visual-csharp-intellisense.md) IntelliSense [JavaScript](../ide/javascript-intellisense.md) – [zadávání komentářů kódu XML](../ide/supplying-xml-code-comments.md)
