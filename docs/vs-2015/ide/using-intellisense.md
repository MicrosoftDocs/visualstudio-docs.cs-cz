---
title: Používání atributu IntelliSense | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 586a0b31166f3b7696865e54f7d2df9c415315f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197187"
---
# <a name="using-intellisense"></a>Používání atributu IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense je obecný termín pro několik funkcí: seznamy členů, informace o parametrech, rychlé informace a dokončování slov. Tyto funkce umožňují získat další informace o kódu, který používáte, zachovat si přehled o parametrech, které píšete, a přidávat volání vlastností a metod s pomocí několika klávesových úhozů.  
  
 Mnoho aspektů technologie IntelliSense je specifických pro jazyk. Další informace o technologii IntelliSense pro různé jazyky naleznete v tématech uvedených v části Viz také.  
  
## <a name="list-members"></a>Vypsat členy  
 Po zadání znaku aktivační události se zobrazí seznam platných členů z typu (nebo oboru názvů) (například, období (`.`) ve spravovaném kódu nebo `::` v jazyce C++). Pokud budete pokračovat v zadávání znaků, seznam bude filtrován tak, aby zahrnoval pouze ty členy, kteří začínají danými znaky.  
  
 Po výběru položky ji můžete vložit do kódu stisknutím klávesy TAB a zadáním mezery. Pokud vyberte položku a zadáte období, položka se zobrazí s uvedenou dobou, která vyvolá jiný seznam členů. Pokud vyberete položku, ale ještě před jejím vložením, zobrazí se rychlé informace pro položku.  
  
 V seznamu členů ikona vlevo představuje typ členu, například obor názvů, třídu, funkci nebo proměnnou. Seznam ikon naleznete v tématu [třídy View and Object Browser Icons](../ide/class-view-and-object-browser-icons.md). Seznam může být poměrně dlouhý a posouvat se v něm můžete stisknutím klávesy PAGE UP a PAGE DOWN.  
  
 ![Seznam členů sady Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")  
  
 Můžete vyvolat **seznam členů** funkce ručně zadáním kombinace kláves CTRL + J, kliknutím na **upravit/IntelliSense/vypsat členy**, nebo kliknutím **seznam členů** tlačítko v editoru panel nástrojů. Při vyvolání na prázdném řádku nebo mimo podporovaný rozsah zobrazí seznam symboly v globálním oboru názvů.  
  
 Chcete-li vypnout členy seznamu ve výchozím nastavení (tak, že se nezobrazí, pokud nejsou konkrétně vyvolány), přejděte na **Nástroje/možnosti/všechny jazyky** a zrušte zaškrtnutí možnosti **automatický seznam členů**. Pokud chcete vypnout funkci vypsat členy pouze pro určitý jazyk, přejděte **Obecné** nastavení pro daný jazyk.  
  
 Můžete také změnit nastavení na režim návrhu, ve kterém je do kódu vložen pouze text, který zadáte. Například pokud zadáte identifikátor, který není uveden v seznamu, a stisknete klávesu TAB, v režimu ukončení by vstup nahradil zadaný identifikátor. Chcete-li přepnout mezi doplňovacím režimem a režimem návrhu, stiskněte kombinaci kláves CTRL + ALT + MEZERNÍK nebo kliknutím na **upravit/IntelliSense/přepnout režim dokončení**.  
  
## <a name="parameter-info"></a>Informace o parametrech  
 Informace o parametru poskytují informace o počtu, názvech a typech parametrů vyžadovaných metodou, atributem parametru obecného typu (v jazyce C#) nebo šablonou (v jazyce C++).  
  
 Parametr tučně označuje další parametr, který je vyžadován při zadávání funkce. Pro přetížené funkce můžete použít klávesy se šipkami nahoru a dolů a zobrazit tak alternativní informace o parametru pro přetížení funkce.  
  
 ![Parameter Info](../ide/media/vs2015-param-info.png "VS2015_param_Info")  
  
 Když opatřujete poznámkami funkce a parametry s komentáři XML dokumentace, komentáře se zobrazí jako informace o parametru. Další informace najdete v tématu [zadávání komentářů ke kódu XML](../ide/supplying-xml-code-comments.md).  
  
 Informace o parametrech lze vyvolat ručně kliknutím **upravit informace o IntelliSense/parametru**, zadáním kombinace kláves CTRL + SHIFT + MEZERNÍK nebo kliknutím **informace o parametru** tlačítko na panelu nástrojů editoru.  
  
## <a name="quick-info"></a>Rychlé informace  
 Rychlé informace zobrazí úplnou deklaraci pro libovolný identifikátor ve vašem kódu.  
  
 ![Visual Studio Quick Info](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")  
  
 Vyberete-li člena v **seznam členů** , rychlé informace zobrazí se také pole.  
  
 ![Informace o parametrech ve C&#35; souboru s kódem](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")  
  
 Rychlé informace lze vyvolat ručně kliknutím **upravit/IntelliSense/parametru informace**, zadáním kombinace kláves CTRL + I nebo kliknutím **rychlé informace** tlačítko na panelu nástrojů editoru.  
  
 Pokud je funkce přetížena, technologie IntelliSense nemusí zobrazit informace pro všechny formy přetížení.  
  
 Rychlé informace v jazyce c++ můžete vypnout nastavením **nástroje / Možnosti / textový Editor/C/C + +/ Upřesnit/automatické informace** k `false`.  
  
## <a name="complete-word"></a>Dokončit slovo  
 Jakmile zadáte dostatečný počet znaků pro odstranění dvojznačnosti termínu, funkce Dokončit slovo dokončí zbytek proměnné, příkazu nebo názvu funkce. Dokončit slovo můžete vyvolat kliknutím **upravit/IntelliSense/dokončit slovo**, zadáním kombinace kláves CTRL + MEZERNÍK nebo kliknutím **dokončit slovo** tlačítko na panelu nástrojů editoru.  
  
## <a name="intellisense-options"></a>Možnosti technologie IntelliSense  
 Možnosti technologie IntelliSense jsou standardně povoleny. Chcete-li je vypnout, klikněte na tlačítko **nástroje/Možnosti/textový Editor** a zrušte zaškrtnutí možnosti **informace o parametrech** nebo **automatický seznam členů** Pokud nechcete, aby funkci vypsat členy.  
  
## <a name="troubleshooting-intellisense"></a>Řešení potíží technologie IntelliSense  
 Možnosti technologie IntelliSense nemusí v určitých případech fungovat podle očekávání.  
  
 **Kurzor je pod chybě s kódem.** Nebudete moct používat technologii IntelliSense, pokud neúplné funkce nebo jiná chyba v kódu nad kurzorem existuje, protože nemusí být možné zpracovat prvky kódu technologie IntelliSense. Tento problém lze vyřešit okomentováním odpovídajícího kódu.  
  
 **Kurzor je v komentáři kódu.** Technologii IntelliSense nelze použít, pokud je kurzor v komentáři ve zdrojovém souboru.  
  
 **Kurzor je v řetězcovém literálu.** Technologii IntelliSense nelze použít, pokud je kurzor v uvozovkách okolo literálu řetězce, jako v následujícím příkladu:  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Automatické možnosti jsou vypnuté.** Ve výchozím nastavení funguje technologie IntelliSense automaticky, ale lze je vypnout. Použít funkci IntelliSense můžete i v případě, že je zakázáno automatické dokončování.  
  
## <a name="see-also"></a>Viz také  
 [Specifické pro jazyk Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)   
 [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md)   
 [Technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md)   
 [Zadávání komentářů ke kódu XML](../ide/supplying-xml-code-comments.md)



