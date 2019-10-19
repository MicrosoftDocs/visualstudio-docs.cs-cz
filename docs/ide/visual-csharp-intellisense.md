---
title: C# IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 13a3c16adca29128be275495fe8921895aa84250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647223"
---
# <a name="c-intellisense"></a>C# IntelliSense

C#Technologie IntelliSense je k dispozici při psaní kódu v editoru a při ladění v příkazovém okně [přímo v režimu](../ide/reference/immediate-window.md) .

## <a name="completion-lists"></a>Seznamy dokončení

Seznamy dokončení IntelliSense v C# obsahují tokeny ze seznamu členů, kompletních slov a dalších. Poskytuje rychlý přístup k:

- Členové typu nebo oboru názvů

- Názvy proměnných, příkazů a funkcí

- Fragmenty kódu

- Klíčová slova jazyka

- Metody rozšíření

Seznam pro doplňování C# v nástroji je také dostatečně inteligentní, aby bylo možné filtrovat nedůležité tokeny a předem vybrat token na základě kontextu. Další informace najdete v tématu [Filtrované seznamy dokončení](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kódu v seznamech dokončení

V C#nástroji obsahuje seznam pro dokončování fragmenty kódu, které vám pomůžou snadno vkládat předdefinované texty do programu. Fragmenty kódu se zobrazí v seznamu pro doplňování jako [text zástupce](../ide/code-snippets-schema-reference.md#shortcut-element)fragmentu. Další informace o fragmentech kódu, které jsou k dispozici ve výchozím nastavení, naleznete v C# tématu [ C# fragmenty kódu](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Klíčová slova jazyka v seznamech dokončení

V C#nástroji obsahuje seznam pro doplňování také klíčová slova jazyka. Další informace o C# klíčových slovech jazyka najdete v tématu [ C# klíčová](/dotnet/csharp/language-reference/keywords/index)slova.

### <a name="extension-methods-in-completion-lists"></a>Metody rozšíření v seznamech dokončení

V C#nástroji obsahuje seznam pro doplňování rozšiřující metody, které jsou v oboru.

> [!NOTE]
> V seznamu pro doplňování se nezobrazí všechny metody rozšíření pro objekty <xref:System.String>.

Metody rozšíření používají jinou ikonu než metody instance. Referenční vodítko pro ikonu seznamu najdete v tématu [zobrazení tříd a prohlížeč objektů ikony](../ide/class-view-and-object-browser-icons.md). Pokud metoda instance a metoda rozšíření se stejným názvem jsou v oboru, v seznamu pro doplňování se zobrazí ikona metody rozšíření.

### <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení

IntelliSense odebere nepotřebné členy ze seznamu pro doplňování pomocí filtrů. C#Filtruje seznam dokončení, který se zobrazí pro tyto položky:

- **Rozhraní a základní třídy**: technologie IntelliSense automaticky odebere položky ze seznamu rozhraní a seznamů doplňování základní třídy v deklaracích Base třídy i v seznamech rozhraní a seznamech omezení. Například výčty se nezobrazují v seznamu pro doplňování pro základní třídy, protože výčty nelze použít pro základní třídy. Seznam dokončení základních tříd obsahuje pouze rozhraní a obory názvů. Pokud vyberete položku v seznamu a potom zadáte čárku, technologie IntelliSense odebere základní třídy ze seznamu dokončení, protože C# nepodporuje vícenásobnou dědičnost. Stejné chování se projeví také v klauzulích omezení.

- **Atributy**: když použijete atribut na typ, seznam pro doplňování se vyfiltruje tak, že seznam obsahuje jenom ty typy, které se dokončí od oborů názvů, které obsahují tyto typy, například <xref:System.Attribute>.

- **Klauzule catch**

- **Inicializátory objektů**: v seznamu dokončení se zobrazí pouze členové, které lze inicializovat.

- **New – klíčové slovo**: když zadáte `new` a pak stisknete **MEZERNÍK**, zobrazí se seznam pro doplňování. Položka je automaticky vybrána v seznamu na základě kontextu v kódu. Například položky jsou automaticky vybrány v seznamu pro doplňování pro deklarace a příkazy Return v metodách.

- **Enum – klíčové slovo**: **když po stisknutí klávesy za** symbolem rovná se u přiřazení výčtu vypíšete, zobrazí se seznam pro doplňování. Položka je automaticky vybrána v seznamu na základě kontextu v kódu. Například položky jsou automaticky vybrány v seznamu pro doplňování po zadání klíčového slova Return a při vytváření deklarace.

- **operátory a jsou**: filtrované dokončování se zobrazí automaticky po stisknutí **mezerníku** po zadání klíčového slova `as` nebo `is`.

- **Události**: když zadáte klíčové slovo `event`, seznam pro doplňování obsahuje jenom typy delegátů.

- **Parametr help** se automaticky řadí k prvnímu přetížení metody, které odpovídá parametrům při jejich zadávání. Pokud je k dispozici více přetížení metod, můžete pomocí šipek nahoru a dolů přejít na další možné přetížení v seznamu.

### <a name="most-recently-used-members"></a>Naposledy použité členy

Technologie IntelliSense pamatuje členy, které jste v poslední době vybrali v rozevíracím [seznamu Členové](../ide/using-intellisense.md) okna pro automatické dokončování názvů objektů. Při příštím použití **seznamu členů**se v horní části zobrazí naposledy použité členy. Historie naposledy použitých členů se mezi jednotlivými relacemi sady Visual Studio vymaže.

### <a name="override"></a>override

Když zadáte [přepis](/dotnet/csharp/language-reference/keywords/override) a potom stisknete **MEZERNÍK**, IntelliSense zobrazí všechny platné členy základní třídy, které lze přepsat v rozevíracím seznamu. Zadání návratového typu metody po `override` požádá IntelliSense, aby zobrazil pouze metody, které vracejí stejný typ. Pokud IntelliSense nenajde žádné shody, zobrazí všechny členy základní třídy.

### <a name="ai-enhanced-intellisense"></a>Vylepšená technologie IntelliSense pro AI

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) nabízí umělé seznamy dokončení technologie IntelliSense, které jsou vylepšené. IntelliCode předpovídá nejpravděpodobnější správné rozhraní API, které by se mělo použít místo pouhého zobrazení abecedních seznamů členů. Pomocí aktuálního kontextu kódu a vzorů poskytuje dynamický seznam.

## <a name="automatic-code-generation"></a>Automatické generování kódu

### <a name="add-using"></a>Přidat direktivu using

Operace **přidat pomocí** technologie IntelliSense automaticky přidá požadovanou direktivu `using` do souboru kódu. Tato funkce vám umožní udržovat svůj fokus na kód, který píšete, a nevyžadovat, abyste posunuli fokus na jinou část kódu.

Chcete-li zahájit operaci **přidat pomocí** , umístěte kurzor na odkaz na typ, který nelze přeložit. Například když vytvoříte konzolovou aplikaci a poté přidáte `XmlReader` do těla metody `Main`, zobrazí se na řádku kódu červená vlnovka, protože odkaz na typ nelze přeložit. Pak můžete vyvolat **přidat pomocí** **rychlých akcí**. **Rychlé akce** jsou viditelné pouze v případě, že je kurzor umístěn na nevázaném typu.

![Přidat rozšířený obrázek pomocí a rychlé akce](../ide/media/addusing-quickaction.png)

Klikněte na ikonu chyby žárovky a pak zvolte **použít System. XML;** k automatickému přidání direktivy using.

### <a name="remove-and-sort-usings"></a>Odebrat a seřadit direktivy using

Možnost **Odebrat a seřadit pomocí** seřadí a odstraní deklarace `using` a `extern`, aniž by došlo ke změně chování zdrojového kódu. V průběhu času se zdrojové soubory můžou bloated a obtížně číst z důvodu zbytečných a neuspořádaných `using` direktiv. Možnost **Odebrat a seřadit pomocí** komprimuje zdrojový kód tím, že se odeberou nepoužívané direktivy `using` a vylepšuje čitelnost jejich řazením. V nabídce **Upravit** zvolte **IntelliSense**a pak zvolte **uspořádat pomocí**.

### <a name="implement-interface"></a>Implementace rozhraní

Technologie IntelliSense poskytuje možnost, která vám umožní implementovat [rozhraní](/dotnet/csharp/language-reference/keywords/interface) při práci v editoru kódu. Obvykle pro správné implementaci rozhraní je nutné vytvořit deklaraci metody pro každého člena rozhraní ve vaší třídě. Pomocí technologie IntelliSense po zadání názvu rozhraní v deklaraci třídy se zobrazí žárovka **rychlé akce** . Žárovka nabízí možnost automaticky implementovat rozhraní pomocí explicitního nebo implicitního pojmenování. V rámci explicitního pojmenování deklarace metod přenese název rozhraní. V rámci implicitního pojmenování deklarace metod neurčuje rozhraní, ke kterému patří. K metodě explicitně pojmenovaného rozhraní lze přistupovat pouze prostřednictvím instance rozhraní a nikoli prostřednictvím instance třídy. Další informace naleznete v tématu [explicitní implementace rozhraní](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implementující rozhraní generuje minimální počet zástupných procedur, které jsou požadovány pro uspokojení rozhraní. Pokud základní třída implementuje části rozhraní, pak tyto zástupné procedury nejsou znovu vygenerovány.

### <a name="implement-abstract-base-class"></a>Implementovat abstraktní základní třídu

Technologie IntelliSense poskytuje možnost, která vám umožní při práci v editoru kódu automaticky implementovat členy abstraktní základní třídy. Za normálních okolností pro implementaci členů abstraktní základní třídy je nutné vytvořit novou definici metody pro každou metodu abstraktní základní třídy v odvozené třídě. Pomocí technologie IntelliSense po zadání názvu abstraktní základní třídy v deklaraci třídy se zobrazí žárovka **rychlé akce** . Žárovka žárovky poskytuje možnost automaticky implementovat metody základní třídy.

Metoda zástupných procedur, které jsou generovány funkcí **implementovat abstract Base Class** , jsou modelovány fragmentem kódu, který je definován v souboru *MethodStub. fragment*. Fragmenty kódu lze upravovat. Další informace naleznete v tématu [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generovat z využití

Funkce **Generovat z využití** umožňuje použít třídy a členy před jejich definováním. Můžete vygenerovat zástupnou proceduru pro libovolnou třídu, konstruktor, metodu, vlastnost, pole nebo výčet, které chcete použít, ale ještě nebyly definovány. Můžete generovat nové typy a členy, aniž byste opustili aktuální umístění v kódu. Tím se minimalizuje přerušení pracovního postupu.

Pod každým nedefinovaným identifikátorem se zobrazí červené vlnovové podtržení. Když umístíte ukazatel myši na identifikátor, zobrazí se v popisu chybová zpráva. Chcete-li zobrazit vhodné možnosti, můžete použít jeden z následujících postupů:

- Klikněte na nedefinovaný identifikátor. Pod identifikátorem se objeví chybová žárovka chyby **rychlých akcí** . Klikněte na žárovku chyby.

- Klikněte na nedefinovaný identifikátor a potom stiskněte **klávesu Ctrl** + **.** (**CTRL** + tečka).

- Klikněte pravým tlačítkem myši na nedefinovaný identifikátor a pak klikněte na **rychlé akce a refaktoring**.

Mezi možnosti, které se zobrazí, patří následující:

- **Generovat vlastnost**

- **Generovat pole**

- **Generování metody**

- **Generovat třídu**

- **Generovat nový typ** (pro třídu, strukturu, rozhraní nebo výčet)

## <a name="generate-event-handlers"></a>Generovat obslužné rutiny událostí

V editoru kódu vám IntelliSense může přispět k zapojení metod (obslužných rutin událostí) do polí událostí.

Když zadáte operátor `+=` po poli události v souboru *. cs* , IntelliSense vás vyzve k stisknutí klávesy **tabulátoru** . Tím se vloží nová instance delegáta, která odkazuje na metodu, která událost zpracovává.

![Automatické zavěšení tlačítka](../ide/media/vxautohookup.gif)

Pokud stisknete klávesu **TAB**, technologie IntelliSense automaticky dokončí příkaz a v editoru kódu zobrazí odkaz na obslužnou rutinu události jako vybraný text. K dokončení automatické služby Event propojení vás IntelliSense vyzve k opětovnému stisknutí klávesy **TAB** a k vytvoření prázdné zástupné procedury pro obslužnou rutinu události.

![Generovat obslužnou rutinu události](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Pokud nový delegát, který je vytvořen technologií IntelliSense, odkazuje na existující obslužnou rutinu události, technologie IntelliSense tyto informace komunikuje v popisu tlačítka. Pak můžete tento odkaz upravit; text je již vybrán v editoru kódu. V opačném případě je v tuto chvíli dokončená Automatická Event propojení.

Pokud stisknete klávesu **TAB**, technologie IntelliSense odblokuje metodu se správným podpisem a umístí kurzor do těla vaší obslužné rutiny události.

> [!NOTE]
> Pomocí příkazu **Navigovat zpět** v nabídce **zobrazení** (**CTRL** + **-** ) se vraťte do příkazu Event propojení.

## <a name="see-also"></a>Viz také:

- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)