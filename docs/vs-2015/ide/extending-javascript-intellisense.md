---
title: Rozšíření JavaScript IntelliSense | Dokumentace Microsoftu
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
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 239416a1638940207a8dcb78b395ed1915e8a93a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867068"
---
# <a name="extending-javascript-intellisense"></a>Rozšíření JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce rozšíření technologie IntelliSense jazyka JavaScript umožňuje přizpůsobit výsledky technologie IntelliSense v editoru jazyka JavaScript pro knihovny třetích stran. Tím lze vylepšit zkušenosti vývojáře, kteří používají tyto knihovny.  
  
 Služba jazyka JavaScript poskytuje funkce technologie IntelliSense pro JavaScript knihovny třetích stran, které jsou přidány do projektu. Pro většinu knihoven dokončování příkazů automaticky poskytuje služba služba jazyka. Následující obrázek znázorňuje příklad dokončování příkazů:  
  
 ![Příklad dokončování](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Pokud vaše knihovna obsahuje popis proměnné, funkce a objekty v standardních značek komentářů jazyka JavaScript (/ /), automaticky využíváte, ve výchozím nastavení z funkce rozšíření technologie IntelliSense, které obsahují popisné informace v místním okně, které Zobrazí se vpravo od prvků do seznamu dokončení nebo zadejte levou závorku ve volání funkce. Komentáře v místním okně obsahovat popis člena. Následující příklad ukazuje seznamu dokončení v místním okně.  
  
 ![Příklad rychlé informace pop&#45;nahoru pole](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Další vylepšení prostředí pro vývojáře, můžete chtít poskytnout informace o typu pro vývojáře v místním okně. Můžete zadat informace o typu pomocí jazyka JavaScript [dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md) místo značky pro komentáře standard. Přidat komentáře dokumentace XML pomocí značky pro komentáře třemi lomítky (/ / / / /) a definovanou sadu elementů XML.  
  
 Alternativně můžete poskytnout informace o typu pomocí rozšíření technologie IntelliSense jazyka JavaScript. Tato funkce umožňuje upravit výsledky technologie IntelliSense tak, že vytváření rozšíření pro JavaScript a jejich přidání na kontext skriptu. V rozšíření, které je soubor jazyka JavaScript, se přihlásíte k odběru událostí, které jsou vystavené `intellisense` objektu služby jazyka. Rozšíření technologie IntelliSense jazyka JavaScript je preferovaným řešením pro knihovny, pokud vzor chování v knihovně zabraňuje služba jazyka JavaScript poskytuje požadované úrovni podporu technologie IntelliSense a pokud o alternativu k deklarativní XML Dokumentační komentáře je také potřeba. Přizpůsobením výsledky technologie IntelliSense můžete vytvořit prostředí IntelliSense, prvotřídní, bez ohledu na případné vzorce chování, které můžete narazit na omezení možnosti výchozí služba jazyka. Další informace najdete v tématu [doplňování výrazů pro identifikátory](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Přidávání rozšíření do kontextu skriptu  
 Rozšíření technologie IntelliSense provádět musí být přidán do aktuální skriptovací kontext. Rozšíření je možné automaticky přidat do kontextu skriptu pomocí mechanismu automatického zjišťování, nebo můžete přidat rozšíření na kontext skriptu ručně pomocí referenčních skupin nebo direktiva odkazu.  
  
 Mechanismus automatického zjišťování umožňuje služba jazyka automaticky najděte rozšíření, které podle konvence pojmenování souborů *NázevKnihovny*. intellisense.js a, které se nacházejí ve stejném adresáři jako knihovny do která se vztahuje rozšíření. Například by platnou příponu knihovny jQuery jQuery.intellisense.js. Pro více omezující jQuery rozšíření můžete použít názvy souborů, například jQuery-1.7.1.intellisense.js (rozšíření specifické pro verzi) nebo jQuery.ui.intellisense.js (rozšíření knihovny jQuery oboru). Nejvíc omezující verze rozšíření se používá, pokud je nalezen více než jedno rozšíření pro danou knihovnu.  
  
 Pokud chcete použít rozšíření pro všechny soubory projektu JavaScript, můžete místo toho přidejte rozšíření do referenční skupiny. Existuje několik typů referenčních skupin, buď ty, které obsahují implicitní odkazy a ty, které zahrnují vyhrazených pracovních serverů odkazů. Chcete-li přidat rozšíření, je obvykle potřeba přidat soubor jako implicitní referenční skupina, buď **implicitní (Windows)**, **implicitní (Web)**. Implicitní odkazy jsou v oboru pro každý soubor .js otevřený v editoru kódu. Když použijete tuto metodu, budete muset přidat rozšíření a soubor, který je doplnit rozšíření.  
  
 Použití **IntelliSense** stránku **možnosti** dialogové okno Přidat rozšíření jako referenční skupiny. Můžete přistupovat **IntelliSense** stránky výběrem **nástroje**, **možnosti** na řádku nabídek a pak zvolíte **textový Editor**, **JavaScript**, **IntelliSense**, **odkazy**. Další informace o referenčních skupin najdete v tématu [technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md) a [možnosti, textový Editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Pokud chcete použít rozšíření pro konkrétní sadu souborů, použijte direktivu odkaz. Když použijete tuto metodu, musíte odkazovat na rozšíření a soubor, který je doplnit rozšíření. Informace o použití direktivy odkazu naleznete v tématu [technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Zpracování událostí technologie IntelliSense  
 Funkce rozšíření umožňuje přizpůsobit výsledky technologie IntelliSense se přihlásíte k odběru událostí, jako `statementcompletion` událostí služby jazyka `intellisense` objektu. Následující příklad ukazuje, jednoduché rozšíření, která se používá služba jazyka skrýt členy, které začínají znakem podtržítka z dokončování příkazů. Tento kód je obsažen v underscorefilter.js a probíhá \\ \\ *cestu instalace sady Visual Studio*\JavaScript\References složky.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 V předchozím kódu rozšíření kontroluje [vlastnost targetName](#TargetName) a [vlastnost cíle](#Target) vlastnosti `statementcompletion` vyloučit objekty, jako objekt události `this` a `window`a zajistit, že je možné identifikovat seznamu dokončení platný příkaz. Pokud seznam pro doplňování lze identifikovat, rozšíření aktualizuje dokončování příkazů [položky vlastnost](#Items) kolekce filtrováním členy, které začínají znakem podtržítka.  
  
 Další příklady najdete \\ \\ *cestu instalace sady Visual Studio*\JavaScript\References složky. Soubor showPlainComments.js v této složce obsahuje příklady použití dalších událostí a poskytuje výchozí podporu technologie IntelliSense pro standardních značek komentářů jazyka JavaScript (/ /). Podobně jako underscorefilter.js showPlainComments.js je již dostupný jako rozšíření pracovní a zobrazí se výsledný informací technologie IntelliSense při použití značky pro komentáře v kódu pro proměnné, funkce a objekty. Další příklady najdete v tématu [příklady kódu](#CodeExamples).  
  
> [!WARNING]
>  Při úpravě souborů rozšíření, které jsou součástí sady Visual Studio, můžete kdykoli deaktivovat technologie IntelliSense jazyka JavaScript nebo funkce podporované rozšířením.  
  
 Do kódu rozšíření, můžete vytvořit pomocí obslužné rutiny pro následující typy událostí `addEventListener`:  
  
- `statementcompletion`, který přidá obslužnou rutinu pro událost dokončení příkazu. Dokončování příkazů obsahuje seznam členů pro konkrétní typ, který se zobrazí po zadání speciální znak, jako je tečka (.) nebo seznam identifikátorů, které se zobrazí při psaní nebo když stisknete kombinaci kláves CTRL + J. Obslužná rutina přijímá události objektu typu `CompletionEvent`, která podporuje následující členy: [položky vlastnost](#Items), [vlastnost cíle](#Target), [vlastnost targetName](#TargetName), a [oboru vlastnost](#Scope).  
  
- `signaturehelp`, který přidá obslužnou rutinu pro informace o parametru technologie IntelliSense. Informace o parametrech poskytuje informace o číslo, názvech a typech parametrů vyžadovaných funkcí. Obslužná rutina přijímá události objektu typu `SignatureHelpEvent`, která podporuje následující členy: [vlastnost cíle](#Target), [parentObject vlastnost](#ParentObject), [functionComments vlastnost](#FunctionComments), [functionHelp vlastnost](#FunctionHelp).  
  
- `statementcompletionhint`, který přidá obslužnou rutinu pro rychlé informace technologie IntelliSense. Místní pole Rychlé informace zobrazí úplnou deklaraci pro identifikátory v kódu. Obslužná rutina přijímá události objektu typu `CompletionHintEvent`, která podporuje následující členy: [completionItem vlastnost](#CompletionItem), a [symbolHelp vlastnost](#SymbolHelp).  
  
  Příklady, které ukazují funkce technologie IntelliSense, jako je doplňování výrazů a informace o parametrech, rychlé informace najdete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
>  V jazyce JavaScript rychlé informace odkazuje na místním okně, které se zobrazí napravo od seznamu dokončení. Rychlé informace nelze vyvolat ručně.  
  
##  <a name="intellisenseObject"></a> technologie IntelliSense objektu  
 V následující tabulce jsou uvedeny funkce, které jsou k dispozici pro `intellisense` objektu. `intellisense` Objekt je k dispozici pouze v době návrhu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Přidá obslužnou rutinu události pro událost technologie IntelliSense.<br /><br /> `type` je hodnota řetězce. Platné hodnoty jsou `statementcompletion`, `signaturehelp`, a `statementcompletionhint`.<br /><br /> `handler` je funkce obslužné rutiny událostí, která bude přijímat události objektu jednoho z následujících typů:<br /><br /> -   `CompletionEvent`, používá pro `statementcompletion` událostí.<br />-   `SignatureHelpEvent`, používá pro `signaturehelp` událostí.<br />-   `CompletionHintEvent`, používá pro `statementcompletionhint` událostí.<br /><br /> Příklady, které tuto funkci použít, najdete v části [příklady kódu](#CodeExamples).|  
|`annotate(obj, doc);`|Dokumentace ke službě pro objekt určuje zkopírováním dokumentační komentáře z jednoho objektu na jiný objekt.<br /><br /> `obj` Určuje objekt, do kterého chcete kopírovat v dokumentaci.<br /><br /> `doc` Určuje objekt, ze kterého chcete kopírovat v dokumentaci.<br /><br /> Příklad, který ukazuje, jak tuto funkci použít, najdete v části [přidávání poznámek IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Vrátí komentáře pro zadanou funkci.<br /><br /> `func` Určuje funkci, pro které jsou vráceny komentáře.<br /><br /> Můžete nastavit `func` parametr pomocí `completionItem.value`.<br /><br /> Vrácený `functionComments` objekt zahrnuje následující členy: `above`, `inside`, a `paramComment`. Další informace najdete v tématu [functionComments vlastnost](#FunctionComments) vlastnost.<br /><br /> `getFunctionComments` mohou být volány pouze v jednom z obslužné rutiny událostí, které jsou registrovány `addEventListener`.<br /><br /> Příklad, který ukazuje, jak tuto funkci použít, najdete v části \\ \\ *cestu instalace sady Visual Studio*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Odešle diagnostické zprávy v okně výstupu.<br /><br /> `msg` je řetězec, který obsahuje zprávu.<br /><br /> Příklad, který ukazuje, jak tuto funkci použít, najdete v části [odesílání zpráv do okna výstup](#Logging).|  
|`nullWithCompletionsOf(value);`|Vrátí zvláštní hodnota null, pro kterou je seznam pro doplňování určeno předaný objekt `value` parametru.<br /><br /> `value` Určuje seznam dokončení pro vrácené hodnoty. `value` může být libovolného typu.<br /><br /> Nulová návratová hodnota je považován za hodnotu null v době návrhu, ale seznamu dokončení pro vrácená hodnota je stejná jako v seznamu dokončení `value` parametru.<br /><br /> Jedno použití pro tuto funkci je na poskytovat technologii IntelliSense pro návratovou hodnotu, pokud návratový typ je předvídatelné za běhu, ale vrácená hodnota je `null` v době návrhu.|  
|`redirectDefinition(func, definition);`|Dá pokyn, technologie IntelliSense zadané definici funkce nahrazujícím původní funkce func při parametru nápovědy nebo **přejít k definici** je požadováno.<br /><br /> `func` Určuje cílová funkce.<br /><br /> `definition` Určuje funkce, která se použijí místo cílová funkce pro informace o parametrech a **přejít k definici**.|  
|`setCallContext(func, thisArg);`|Nastaví kontext volání nebo rozsah pro zadanou funkci.<br /><br /> `func` Určuje funkci, pro kterou chcete nastavit obor.<br /><br /> `thisArg` je objekt literálu do kterého `this` může odkazovat klíčové slovo, které určuje nový obor pro člena. Můžete například zahrnout argumenty předané v tomto parametru `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` poskytuje podobné chování `Function.prototype.bind`, s tím rozdílem, že jej použít pouze pro podporu technologie IntelliSense v době návrhu. Můžete použít `setCallContext` k nastavení oboru funkce, pokud chcete simulovat volání kód, který je jinak nedostupný, takže při volání funkce, bude obsahovat volání funkce správný rozsah a argumenty.|  
|`undefinedWithCompletionsOf(value);`|Vrátí speciální nedefinovaná hodnota, pro kterou je seznam pro doplňování určeno předaný objekt `value` parametru.<br /><br /> `value` Určuje seznam dokončení pro vrácené hodnoty. `value` může být libovolného typu.<br /><br /> Nedefinované vracet hodnotou zacházet jako definováno v době návrhu, ale dokončení seznamu pro vrácená hodnota je stejný jako seznamu dokončení pro `value` parametru.<br /><br /> Jedno použití této funkce je poskytovat technologii IntelliSense pro návratovou hodnotu, pokud je návratový typ předvídatelné za běhu, ale vrácená hodnota je definováno v době návrhu.|  
|`version()`|Vrátí verzi sady Visual Studio.|  
  
## <a name="event-members"></a>Události  
 Následující části popisují členy, které jsou vystaveny v objektu události pro následující události: `statementcompletion`, `signaturehelp`, a `statementcompletionhint`.  
  
###  <a name="CompletionItem"></a> completionItem vlastnost  
 Vrátí identifikátor, označované jako položky dokončení, pro kterou je požadována v místním okně Rychlé informace. Tato vlastnost je k dispozici pro `statementcompletionhint` objektu události a [položky vlastnost](#Items) vlastnost `statementcompletion` objektu události.  
  
 Návratová hodnota: `completionItem` objektu  
  
 Následují členové `completionItem` objektu:  
  
-   `name`. Čtení a zápis při použití v `items` kolekci; jinak jen pro čtení. Vrátí řetězec, který určuje položky dokončení.  
  
-   `kind`. Čtení a zápis při použití v `items` kolekci; jinak jen pro čtení. Vrátí řetězec, který představuje typ položky dokončení. Možné hodnoty jsou metody, pole, vlastnost, parametr, proměnné a rezervován.  
  
-   `glyph`. Čtení a zápis při použití v `items` kolekci; jinak jen pro čtení. Vrátí řetězec, který představuje ikonu, která se zobrazí v seznamu dokončení. Možné hodnoty parametru `glyph` použijte následující formát: vs:*glyphType*, kde *glyphType* odpovídá členy jazykově nezávislé <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> výčet. Například `vs:GlyphGroupMethod` je jednou z možných hodnot pro `glyph`. Když `glyph` není nastavená, `kind` vlastnost určuje výchozí ikona.  
  
-   `parentObject`. Jen pro čtení. Vrátí nadřazený objekt.  
  
-   `value`. Jen pro čtení. Vrátí objekt, který představuje hodnotu položky dokončení.  
  
-   `comments`. Jen pro čtení. Vrátí řetězec, který obsahuje komentáře, které jsou nad pole nebo proměnné.  
  
-   `scope`. Jen pro čtení. Vrátí rozsah položky dokončení. Možné hodnoty jsou globální, místní, parametr a člena.  
  
###  <a name="Items"></a> položky vlastnosti  
 Získá nebo nastaví pole příkazu položek dokončení. Každý prvek v poli je [completionItem vlastnost](#CompletionItem) objektu. `items` Vlastnost je k dispozici pro `statementcompletion` objektu události.  
  
 Návratová hodnota: pole  
  
###  <a name="FunctionComments"></a> functionComments vlastnost  
 Vrátí komentáře pro funkci. Tato vlastnost je k dispozici pro `signaturehelp` objektu události.  
  
 Návratová hodnota: `comments` objektu  
  
 Následují členové `comments` objektu:  
  
-   `above`. Vrátí komentáře nad funkce.  
  
-   `inside`. Vrátí komentáře uvnitř funkce, obvykle ve formátu VSDoc.  
  
-   `paramComments`. Vrátí pole představující komentáře pro každého parametru ve funkci. Členy pole patří:  
  
    -   `name`. Vrátí řetězec představující název parametru.  
  
    -   `comment`. Vrátí řetězec, který obsahuje parametr komentář.  
  
###  <a name="FunctionHelp"></a> functionHelp vlastnost  
 Vrátí Nápověda pro funkci. Tato vlastnost je k dispozici pro `signaturehelp` objektu události.  
  
 Návratová hodnota: `functionHelp` objektu  
  
 Následují členové `functionHelp` objektu:  
  
-   `functionName`. Čtení a zápis Vrátí řetězec, který obsahuje název funkce.  
  
-   `signatures`. Čtení a zápis Získá nebo nastaví pole signatury funkce. Každý prvek v poli je `signature` objektu. Některé `signature` vlastnosti, jako například `locid`, odpovídají na běžné [dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md) atributy.  
  
     Členové `signature` objekt obsahovat:  
  
    -   `description`. Čtení a zápis Vrátí řetězec, který popisuje funkce.  
  
    -   `locid`. Čtení a zápis Vrátí identifikátor řetězce, který obsahuje informace o lokalizaci, informace o funkci.  
  
    -   `helpKeyword`. Čtení a zápis Vrátí řetězec, který obsahuje klíčové slovo nápovědy.  
  
    -   `externalFile`. Čtení a zápis Vrátí řetězec, který představuje soubor, který obsahuje ID člena.  
  
    -   `externalid`. Čtení a zápis Vrátí řetězec, který představuje ID členské funkce.  
  
    -   `params`. Čtení a zápis Získá nebo nastaví pole parametrů pro funkci. Každý prvek v poli parametrů `parameter` objekt, který obsahuje vlastnosti, které odpovídají na následující atributy [ \<param >](../ide/param-javascript.md) element:  
  
        -   `name`. Čtení a zápis Vrátí řetězec představující název parametru.  
  
        -   `type`. Čtení a zápis Vrátí řetězec, který představuje typ parametru.  
  
        -   `elementType`. Čtení a zápis Pokud je typ `Array`, vrátí řetězec, který představuje typ prvků v poli.  
  
        -   `description`. Čtení a zápis Vrátí řetězec, který popisuje parametr.  
  
        -   `locid`. Čtení a zápis Vrátí identifikátor řetězce, který obsahuje informace o lokalizaci, informace o funkci.  
  
        -   `optional`. Čtení a zápis Vrátí řetězec, který označuje, zda se jedná o volitelný parametr. `true` Označuje, že parametr je volitelná. `false` označuje, že není.  
  
    -   `returnValue`. Čtení a zápis Získá nebo nastaví návratovou hodnotu objekt s vlastnostmi, které odpovídají na následující atributy [ \<vrátí >](../ide/returns-javascript.md) element:  
  
        -   `type`. Čtení a zápis Vrátí řetězec, který představuje návratovým typem.  
  
        -   `elementType`. Čtení a zápis Pokud je typ `Array`, vrátí řetězec, který představuje typ prvků v poli.  
  
        -   `description`. Čtení a zápis Vrátí řetězec, který popisuje návratovou hodnotu.  
  
        -   `locid`. Čtení a zápis Vrátí identifikátor řetězce, který obsahuje informace o lokalizaci, informace o funkci.  
  
        -   `helpKeyword`. Čtení a zápis Vrátí řetězec, který obsahuje klíčové slovo nápovědy.  
  
        -   `externalFile`. Čtení a zápis Vrátí řetězec, který představuje soubor, který obsahuje ID člena.  
  
        -   `externalid`. Čtení a zápis Vrátí řetězec, který představuje ID členské funkce.  
  
###  <a name="ParentObject"></a> parentObject vlastnost  
 Vrátí nadřazený objekt členské funkce. Například pro `document.getElementByID`, `parentObject` vrátí `document` objektu. Tato vlastnost je k dispozici pro `signaturehelp` objektu události.  
  
 Návratová hodnota: objekt  
  
###  <a name="Target"></a> Vlastnost cíle  
 Vrátí objekt, který představuje položku vlevo od znaku aktivační události, které je tečka (.). Pro funkce `target` vrátí funkci, pro kterou je požadována informace o parametru. Tato vlastnost je k dispozici pro `statementcompletion` a `signaturehelp` objekty událostí.  
  
 Návratová hodnota: objekt  
  
###  <a name="TargetName"></a> Vlastnost targetName  
 Vrátí řetězec, který představuje cíl. Například pro "this." `targetName` vrátí "this". Pro "A.B" (když je ukazatel myši po "B") `targetName` vrátí "B". Tato vlastnost je k dispozici pro `statementcompletion` objektu události.  
  
 Návratová hodnota: řetězec  
  
###  <a name="SymbolHelp"></a> symbolHelp vlastnost  
 Vrátí položky dokončení, pro kterou je požadována v místním okně Rychlé informace. Tato vlastnost je k dispozici pro `statementcompletionhint` objektu události.  
  
 Návratová hodnota: `symbolHelp` objektu.  
  
 Některé vlastnosti `symbolHelp` objektů, jako například `locid`, odpovídají na běžné [dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md) atributy.  
  
 Následují členové `symbolHelp` objektu:  
  
-   `name`. Čtení a zápis Vrátí řetězec, který obsahuje název identifikátoru.  
  
-   `symbolType`. Čtení a zápis Vrátí řetězec, který představuje typ symbolu. Možné hodnoty zahrnují neznámý, logická hodnota, číslo, řetězec, objekt, funkce, pole, datum a regulární výraz.  
  
-   `symbolDisplayType`. Čtení a zápis Vrátí řetězec, který obsahuje název typu pro zobrazení. Pokud `symbolDisplayType` není nastavena, `symbolType` se používá.  
  
-   `elementType`. Čtení a zápis Pokud `symbolType` je `Array`, vrátí řetězec, který představuje typ prvků v poli.  
  
-   `scope`. Čtení a zápis Vrátí řetězec, který představuje obor symbolu. Možné hodnoty zahrnují parametr globální, místní a člena.  
  
-   `description`. Čtení a zápis Vrátí řetězec, který obsahuje popis daného symbolu.  
  
-   `locid`. Čtení a zápis Vrátí identifikátor řetězce, který obsahuje informace o lokalizaci o symbolu.  
  
-   `helpKeyword`. Čtení a zápis Vrátí řetězec, který obsahuje klíčové slovo nápovědy.  
  
-   `externalFile`. Čtení a zápis Vrátí řetězec, který představuje soubor, který obsahuje ID člena.  
  
-   `externalid`. Čtení a zápis Vrátí řetězec, který představuje ID člena symbolu.  
  
-   `functionHelp`. Čtení a zápis Vrátí [functionHelp vlastnost](#FunctionHelp), který by mohl obsahovat informace při `symbolType` je funkce.  
  
###  <a name="Scope"></a> obor vlastnost  
 Vrátí obor dokončení události. Možné hodnoty pro dokončení obor je globální a členy. Tato vlastnost je k dispozici pro `statementcompletion` objektu události.  
  
 Návratová hodnota: řetězec  
  
## <a name="debugging-intellisense-extensions"></a>Ladění rozšíření technologie IntelliSense  
 Nelze ladit rozšíření, ale můžete použít [intellisense objekt](#intellisenseObject) funkce odesílat informace v okně Výstup Visual Studia. Příklad, který ukazuje, jak tuto funkci použít, najdete v části [odesílání zpráv do okna výstup](#Logging) dále v tomto tématu. Pro `logMessage` fungovat, musí být zaregistrovaný aspoň jedna obslužná rutina události v rozšíření.  
  
##  <a name="CodeExamples"></a> Příklady kódu  
 Tato část obsahuje příklady kódu, které ukazují, jak používat rozšíření IntelliSense rozhraní API. Existují také jiné způsoby, jak pomocí těchto rozhraní API. Další příklady najdete v následující soubory v seznamu \\ \\ *cestu instalace sady Visual Studio*\JavaScript\References složky. Tyto příklady, které používá služba jazyka JavaScript pracují.  
  
-   underscoreFilter.js. Tento kód skryje soukromé členy z technologie IntelliSense. Obsahuje obslužné rutiny událostí pro `statementcompletion` událostí.  
  
-   showPlainComments.js. Tento kód poskytuje podporu technologie IntelliSense pro standardní komentáře. Obsahuje obslužné rutiny událostí pro `signaturehelp` a `statementcompletionhint` události.  
  
###  <a name="Annotations"></a> Přidávání poznámek technologie IntelliSense  
 Následující postup ukazuje, jak poskytnout podporu technologie IntelliSense dokumentace pro knihovny třetí strany beze změny knihovny přímo. K tomuto účelu můžete použít `intellisense.annotate` v rozšíření.  
  
 Pro tento příklad fungoval musíte tyto soubory jazyka JavaScript v projektu:  
  
-   demoLib.js, což je soubor projektu, který představuje knihovnu třetí strany.  
  
-   demoLib.intellisense.js, což je rozšíření technologie IntelliSense. Tento soubor nemusí být součástí projektu, ale musí být ve stejné složce jako exampleLib.js.  
  
-   appCode.js, což je soubor projektu, který představuje kód aplikace.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Přidat poznámku technologie IntelliSense  
  
1.  Přidejte následující kód do demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  Přidejte následující kód do demoLib.intellisense.js.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  Přidejte následující direktivy odkazu jako první řádek v appCode.js. Cesta se tady použít označuje, že soubory jazyka JavaScript jsou ve stejné složce.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  AppCode.js zadejte následující kód. Zobrazí se vám dokumentační komentáře XML v rozšíření zobrazí jako informace o parametru technologie IntelliSense.  
  
     ![Příklad znázorňující použití intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5.  AppCode.js zadejte následující kód. Při psaní uvidíte standardních komentářů v rozšíření zobrazí jako rychlé informace technologie IntelliSense.  
  
     ![Příklad znázorňující použití intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
###  <a name="Logging"></a> Odesílání zpráv do okna výstup  
 Následující postup ukazuje, jak odesílat zprávy v okně výstupu. Můžete odesílat zprávy pomoci při ladění rozšíření technologie IntelliSense.  
  
 Pro tento příklad fungoval musíte tyto soubory jazyka JavaScript v projektu:  
  
-   exampleLib.js, což je soubor projektu, který představuje knihovnu třetí strany.  
  
-   exampleLib.intellisense.js, což je rozšíření technologie IntelliSense. Tento soubor nemusí být součástí projektu, ale musí být ve stejné složce jako exampleLib.js.  
  
-   appCode.js, což je soubor projektu, který představuje kód aplikace.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Odeslat zprávu do okna výstup  
  
1.  Přidejte následující kód do exampleLib.js.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  Přidejte následující kód do exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  Přidejte následující direktivy odkazu jako první řádek v appCode.js. Cesta se tady použít označuje, že soubory jazyka JavaScript jsou ve stejné složce.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  V okně výstupu zvolte **jazyková služba JavaScriptu** v **zobrazit výstup z:** seznamu. (Chcete-li zobrazit okno výstup, vyberte **výstup** v nabídce Zobrazit.)  
  
5.  AppCode.js zadejte následující kód. Během psaní zobrazuje v okně Výstup zprávy ze služby jazyka. První zprávu v okně výstupu označuje požádal dokončování aktuálního oboru.  
  
    ```javascript  
    some  
    ```  
  
     Následuje výstupu, který by se měla zobrazit částečné zobrazení.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  Zvolte **Vymazat vše** tlačítka v okně výstup.  
  
7.  Zadáním následujícího kódu. První zprávu v okně výstupu označuje požádal seznam členů.  
  
    ```javascript  
    someVar.  
    ```  
  
     Toto je částečné zobrazení, které byste měli vidět výstup:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> Změna ikony technologie IntelliSense  
 Následující postup ukazuje, jak změnit ikony ve výchozím nastavení zobrazí v IntelliSense. To může být užitečné, když zadáte, aby IntelliSense informace o konkrétní knihovny konceptů, jako jsou obory názvů, třídy, rozhraní a výčty.  
  
 K dispozici ikona hodnoty, najdete v části <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Pro tento příklad fungoval musíte tyto soubory jazyka JavaScript v projektu:  
  
-   exampleLib.js, což je projekt soubor knihovny represens třetí strany.  
  
-   exampleLib.intellisense.js, což je rozšíření technologie IntelliSense. Tento soubor nemusí být součástí projektu, ale musí být ve stejné složce jako exampleLib.js.  
  
-   appCode.js, což je soubor projektu, který představuje kód aplikace.  
  
##### <a name="to-change-the-icons"></a>Chcete-li změnit ikony  
  
1.  Přidejte následující kód do exampleLib.js.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  Přidejte následující kód do exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  Přidejte následující direktivy odkazu jako první řádek v appCode.js. Cesta se tady použít označuje, že soubory jazyka JavaScript jsou ve stejné složce.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  AppCode.js zadejte následující kód. Při psaní uvidíte, že na ikonu pro obor názvů se změnila na "{}", jak se používá v jazyce C#.  
  
     ![Příklad znázorňující použití piktogram vlastnosti](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5.  AppCode.js zadejte následující kód. Během psaní se zobrazí nová ikona výčtu pro člena Enum1 a novou ikonu třídy SomeClass1 člena.  
  
     ![Příklad znázorňující použití vlastnosti piktogram](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
###  <a name="Overriding"></a> Jak se vyhnout za běhu vliv na výsledky technologie IntelliSense  
 Služba jazyka JavaScript spouští kód k dynamickému poskytování informací technologie IntelliSense. V důsledku toho chování za běhu může čas od času narušovat požadovaných výsledků. Následující postup ukazuje, jak přepsat výsledky technologie IntelliSense při chování za běhu má za následek nesprávnou IntelliSense.  
  
 Pro tento příklad fungoval musíte tyto soubory jazyka JavaScript v projektu:  
  
-   exampleLib.js, což je soubor projektu, který představuje knihovnu třetí strany.  
  
-   exampleLib.intellisense.js, což je rozšíření technologie IntelliSense. Tento soubor nemusí být součástí projektu, ale musí být ve stejné složce jako exampleLib.js.  
  
-   appCode.js, což je soubor projektu, který představuje kód aplikace.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Aby se zabránilo za běhu vliv na výsledky technologie IntelliSense  
  
1.  Přidejte následující kód do exampleLib.js.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     V předchozím kódu zabalené funkce ignoruje počáteční volání na základě hodnoty z `count`a nevrací výsledky.  
  
2.  Přidejte následující direktivy odkazu jako první řádek v appCode.js. Cesta se tady použít označuje, že soubory jazyka JavaScript jsou ve stejné složce.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  AppCode.js zadejte následující kód. Seznam identifikátorů se zobrazí místo technologie IntelliSense, protože zabalené funkce se nikdy nevolá, což znamená, že `throttled` funkce nevrací žádné výsledky.  
  
     ![Příklad přepsání intellisense výsledky](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4.  Přidejte následující kód do exampleLib.intellisense.js. Tím se změní chování návrhu tak, aby IntelliSense se zobrazí pro zabalenou funkci podle očekávání.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  V appCode.js výsledky testů tak, že zadáte stejný kód, který jste zadali dříve. Tentokrát IntelliSense obsahuje požadované informace.  
  
     ![Příklad přepsání IntelliSense výsledky](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Viz také  
 [Technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md)   
 [Doplňování výrazů pro identifikátory](../ide/statement-completion-for-identifiers.md)



