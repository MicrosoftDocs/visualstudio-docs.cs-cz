---
title: C# IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2ed5d86599fa99b9c1360b414b37ef95ab59082d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303027"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense je k dispozici při kódování v editoru a při ladění v okně příkazu [okamžitý režim.](../ide/reference/immediate-window.md)

## <a name="completion-lists"></a>Seznamy dokončení

Seznamy dokončení technologie IntelliSense v c# obsahují tokeny ze seznamu členů, complete word a další. Poskytuje rychlý přístup k:

- Členové typu nebo oboru názvů

- Názvy proměnných, příkazů a funkcí

- Fragmenty kódu

- Jazyková klíčová slova

- Metody rozšíření

Seznam dokončení v C# je také dostatečně chytrý, aby odfiltrovat irelevantní tokeny a předem vybrat token na základě kontextu. Další informace naleznete v [tématu Filtrované seznamy dokončení](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kódu v seznamech dokončení

V c# seznam dokončení obsahuje fragmenty kódu, které vám pomohou snadno vložit předdefinovaná těla kódu do programu. Fragmenty kódu se v seznamu dokončení zobrazují jako [rezimktový text výstřižku](../ide/code-snippets-schema-reference.md#shortcut-element). Další informace o fragmentech kódu, které jsou ve výchozím nastavení k dispozici v c# naleznete v [tématu fragmenty kódu jazyka C#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Jazyková klíčová slova v seznamech dokončení

V jazyce C# seznam dokončení také obsahuje klíčová slova jazyka. Další informace o klíčových slovech jazyka Jazyka C# naleznete v [tématu Klíčová slova jazyka C#](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Metody rozšíření v seznamech dokončení

V c#, seznam dokončení obsahuje metody rozšíření, které jsou v oboru.

> [!NOTE]
> Seznam dokončení nezobrazuje všechny metody <xref:System.String> rozšíření pro objekty.

Metody rozšíření používají jinou ikonu než metody instance. Referenční příručka pro ikony seznamu najdete v [tématu Ikony zobrazení tříd a Prohlížeče objektů](../ide/class-view-and-object-browser-icons.md). Pokud jsou metoda instance a metoda rozšíření se stejným názvem v oboru, seznam dokončení zobrazí ikonu metody rozšíření.

### <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení

Technologie IntelliSense odebere nepotřebné členy ze seznamu dokončení pomocí filtrů. C# filtruje seznamy dokončení, které se zobrazí pro tyto položky:

- **Rozhraní a základní třídy**: Technologie IntelliSense automaticky odebere položky ze seznamu dokončení rozhraní a základní třídy, a to jak v základních deklaracích tříd, tak v seznamech rozhraní a seznamech omezení. Výčty se například nezobrazí v seznamu dokončení pro základní třídy, protože výčty nelze použít pro základní třídy. Seznam dokončení základních tříd obsahuje pouze rozhraní a obory názvů. Pokud vyberete položku v seznamu a zadejte čárku, technologie IntelliSense odebere základní třídy ze seznamu dokončení, protože c# nepodporuje vícenásobnou dědičnost. Stejné chování dochází pro klauzule omezení také.

- **Atributy**: Při použití atributu na typ je seznam dokončení filtrován tak, aby seznam obsahoval pouze ty <xref:System.Attribute>typy, které pocházejí z oborů názvů, které obsahují tyto typy, například .

- **Doložky o úlovku**

- **Inicializační metody objektu**: V seznamu dokončení se zobrazí pouze členové, které lze inicializovat.

- **nové klíčové slovo** `new` : Když zadáte a potom stisknete **mezeru**, zobrazí se seznam dokončení. Položka je automaticky vybrána v seznamu na základě kontextu v kódu. Například položky jsou automaticky vybrány v seznamu dokončení pro deklarace a pro návratové příkazy v metodách.

- **Klíčové slovo výčtu**: Když stisknete **mezeru** za znaménkem rovná se pro přiřazení výčtu, zobrazí se seznam dokončení. Položka je automaticky vybrána v seznamu na základě kontextu v kódu. Položky jsou například automaticky vybrány v seznamu dokončení po zadání vráceného klíčového slova a při prohlášení.

- **jako a operátory**: Filtrovaný seznam dokončení se zobrazí automaticky po stisknutí `is` **klávesy Mezera** po zadání klíčového `as` slova nebo.

- **Události**: Při zadávání `event`klíčového slova obsahuje seznam dokončení pouze typy delegátů.

- **Pomoc s parametrem** automaticky seřadí na první přetížení metody, které odpovídá parametrům při jejich zadávání. Pokud je k dispozici více přetížení metody, můžete použít šipky nahoru a dolů k přechodu na další možné přetížení v seznamu.

### <a name="most-recently-used-members"></a>Nejnověji použité členy

Technologie IntelliSense si pamatuje členy, které jste nedávno vybrali v poli Pop-up [List Members](../ide/using-intellisense.md) pro automatické dokončení názvu objektu. Při příštím použití **seznamu členů**se naposledy použité členy zobrazí nahoře. Historie naposledy použitých členů je vymazána mezi každou relací sady Visual Studio.

### <a name="override"></a>override

Když zadáte [přepsat](/dotnet/csharp/language-reference/keywords/override) a pak stisknete **mezeru**, intelliSense zobrazí všechny platné členy základní třídy, které můžete přepsat v rozbalovacím seznamu. Zadáním návratového typu metody `override` po výzvy IntelliSense zobrazíte pouze metody, které vracejí stejný typ. Pokud technologie IntelliSense nemůže najít žádné shody, zobrazí všechny členy základní třídy.

### <a name="ai-enhanced-intellisense"></a>Technologie IntelliSense s umělou diatou

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) poskytuje seznamy dokončení technologie IntelliSense s umělou inteligencí. IntelliCode předpovídá s největší pravděpodobností správné rozhraní API použít, nikoli pouze prezentaci abecední seznam členů. Používá aktuální kontext kódu a vzory k poskytnutí dynamického seznamu.

## <a name="automatic-code-generation"></a>Automatické generování kódu

### <a name="add-using"></a>Přidat direktivu using

Operace **Přidat pomocí** technologie IntelliSense `using` automaticky přidá požadovanou direktivu do souboru kódu. Tato funkce umožňuje zachovat vaše zaměření na kód, který píšete, spíše než vyžadovat, abyste přesunuli fokus na jinou část kódu.

Chcete-li zahájit operaci **Přidat pomocí,** umístěte kurzor na odkaz typu, který nelze přeložit. Například při vytvoření konzoly aplikace `XmlReader` a potom přidat `Main` do těla metody, červená vlnovka se zobrazí na tomto řádku kódu, protože odkaz na typ nelze přeložit. Potom můžete vyvolat **Přidat pomocí** pomocí rychlé **akce**. **Rychlé akce** jsou viditelné pouze v případě, že je kurzor umístěn na nevázaném typu.

![Přidání rozšířeného obrázku s pomocí rychlé akce](../ide/media/addusing-quickaction.png)

Klikněte na ikonu chybové žárovky a pak zvolte **pomocí system.xml;** chcete-li automaticky přidat direktivu using.

### <a name="remove-and-sort-usings"></a>Odebrání a řazení pomocí

Možnost **Odebrat a seřadit usings** seřadí a odebere `using` a `extern` odebírá beze změny chování zdrojového kódu. V průběhu času může být zdrojové soubory nafouklé a `using` obtížně čitelné z důvodu zbytečných a neorganizovaných směrnic. Možnost **Odebrat a seřadit usings** komprimuje zdrojový kód odebráním nepoužívaných `using` směrnic a zlepšuje čitelnost jejich řazením. V nabídce **Úpravy** zvolte **IntelliSense**a pak zvolte **Uspořádat způsoby použití**.

### <a name="implement-interface"></a>Implementace rozhraní

Technologie IntelliSense poskytuje možnost, která vám pomůže implementovat [rozhraní](/dotnet/csharp/language-reference/keywords/interface) při práci v editoru kódu. Za normálních okolností implementovat rozhraní správně, musíte vytvořit deklaraci metody pro každého člena rozhraní ve vaší třídě. Pomocí technologie IntelliSense se po zadání názvu rozhraní do deklarace třídy zobrazí žárovka **Rychlé akce.** Žárovka vám dává možnost implementovat rozhraní automaticky pomocí explicitní nebo implicitní pojmenování. Pod explicitní pojmenování deklarace metody nesou název rozhraní. Pod implicitní pojmenování deklarace metody neoznačují rozhraní, ke kterému patří. Explicitně pojmenovaná metoda rozhraní je přístupná pouze prostřednictvím instance rozhraní a nikoli prostřednictvím instance třídy. Další informace naleznete [v tématu Explicitní implementace rozhraní](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implement Interface generuje minimální počet zástupných procedur metody, které jsou nutné ke splnění rozhraní. Pokud základní třída implementuje části rozhraní, pak tyto zástupné procedury nejsou regenerovány.

### <a name="implement-abstract-base-class"></a>Implementace abstraktní základní třídy

Technologie IntelliSense poskytuje možnost, která vám pomůže automaticky implementovat členy abstraktní základní třídy při práci v editoru kódu. Normálně implementovat členy abstraktní základní třídy vyžaduje vytvoření nové definice metody pro každou metodu abstraktní základní třídy v odvozené třídě. Pomocí technologie IntelliSense se po zadání názvu abstraktní základní třídy do deklarace třídy zobrazí žárovka **Rychlé akce.** Žárovka vám dává možnost implementovat metody základní třídy automaticky.

Zástupné procedury metody, které jsou generovány funkcí **Implement Abstract Base Class,** jsou modelovány fragmentem kódu definovaným v souboru *MethodStub.snippet*. Fragmenty kódu lze upravit. Další informace naleznete [v tématu Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generovat z využití

Funkce **Generovat z použití** umožňuje používat třídy a členy před jejich definováním. Můžete vygenerovat se zakázaným inzerováním pro libovolnou třídu, konstruktor, metodu, vlastnost, pole nebo výčt, které chcete použít, ale ještě jste je nedefinovali. Můžete generovat nové typy a členy, aniž byste opustili aktuální umístění v kódu. Tím se minimalizuje přerušení pracovního postupu.

Pod každým nedefinovaným identifikátorem se zobrazí červené podtržení vlnovkou. Když položíte ukazatel myši na identifikátor, zobrazí se v popisku chybová zpráva. Chcete-li zobrazit příslušné možnosti, můžete použít jeden z následujících postupů:

- Klikněte na nedefinovaný identifikátor. Pod identifikátorem se zobrazí kontrolka chyby **rychlé akce.** Klikněte na chybovou žárovku.

- Klepněte na nedefinovaný identifikátor a stiskněte **klávesu Ctrl**+**.** (**Ctrl** + tečka).

- Klikněte pravým tlačítkem myši na nedefinovaný identifikátor a potom klikněte na **rychlé akce a refaktoringy**.

Zobrazené možnosti mohou zahrnovat následující:

- **Generovat vlastnost**

- **Generovat pole**

- **Generování metody**

- **Generovat třídu**

- **Generovat nový typ** (pro třídu, strukturu, rozhraní nebo výčtu)

## <a name="generate-event-handlers"></a>Generovat obslužné rutiny událostí

V editoru kódu vám technologie IntelliSense může pomoci připojit metody (obslužné rutiny událostí) k polím událostí.

Když zadáte `+=` operátor a zadáte operátor a zadáte do souboru *.cs* pole události, technologie IntelliSense vás vyzve k stisknutí klávesy **Tab.** Tím vložíte novou instanci delegáta, který odkazuje na metodu zpracování události.

![Tlačítko Automatické připojení](../ide/media/vxautohookup.gif)

Pokud stisknete **klávesu**Tab , technologie IntelliSense automaticky dokončí příkaz za vás a zobrazí odkaz na obslužnou rutinu události jako vybraný text v editoru kódu. Chcete-li dokončit automatické připojení k události, technologie IntelliSense vás vyzve k opětovnému stisknutí **klávesy Tab** a vytvoří teprázdna zástupného příkazu pro obslužnou rutinu události.

![Generovat obslužnou rutinu události](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Pokud nový delegát vytvořený nástrojem IntelliSense odkazuje na existující obslužnou rutinu události, technologie IntelliSense tyto informace sdělí v popisku. Tento odkaz pak můžete upravit. text je již vybrán v editoru kódu. V opačném případě je automatické připojení k události dokončeno v tomto okamžiku.

Pokud stisknete **klávesu Tab**, intelliSense zobrazí se zakázaným inzerováním metodu se správným podpisem a umístí kurzor do těla obslužné rutiny události.

> [!NOTE]
> Pomocí příkazu **Přejít zpět** v nabídce **Zobrazení** (**Ctrl**+**-**) se vraťte k příkazu připojení k události.

## <a name="see-also"></a>Viz také

- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [IDE visual studia](../get-started/visual-studio-ide.md)
