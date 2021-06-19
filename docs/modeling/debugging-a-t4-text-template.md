---
title: Ladění textové šablony T4
description: Pokud chcete ladit textovou šablonu v době návrhu, uložte soubor textové šablony a pak v místní nabídce souboru v souboru v Průzkumník řešení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c9e4454071002e3bce8478bc825ecfddc17620f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385770"
---
# <a name="debugging-a-t4-text-template"></a>Ladění textové šablony T4
Zarážky můžete nastavit v textových šablonách. Pokud chcete ladit textovou šablonu v době návrhu,  uložte soubor textové šablony a pak v místní nabídce souboru v souboru v Průzkumník řešení. Pokud chcete ladit textovou šablonu za běhu, stačí ladit aplikaci, do které patří.

 Pokud chcete ladit textovou šablonu, měli byste rozumět krokům procesu transformace šablony. V každém kroku může dojít k různým druhům chyb. Postup je následující.

|Krok|Šablona v době návrhu: kdy k ní dojde|Šablona za běhu: když k ní dojde|
|-|-|-|
|Z textové šablony se vygeneruje kód.<br /><br /> Chyby v direktivách nebo neodpovídající nebo zašedlované `<#...#>` značky.|Když šablonu uložíte nebo vyvoláte transformaci textu.|Když šablonu uložíte nebo vyvoláte transformaci textu.|
|Vygenerovaný kód je zkompilován.<br /><br /> Chyby kompilace v kódu šablony.|Ihned po předchozím kroku.|Spolu s kódem vaší aplikace.|
|Spustí se kód.<br /><br /> Chyby za běhu v kódu šablony.|Ihned po předchozím kroku.|Při spuštění aplikace a vyvolání kódu šablony.|

 Ve většině případů jsou čísla řádků v kódu šablony dána v sestavě chyb. Pokud sestava chyb odkazuje na dočasný název souboru, obvyklou příčinou je neshoda hranaté závorky v kódu textové šablony.

 Zarážky můžete nastavit v textových šablonách a ladit obvyklým způsobem.

## <a name="common-errors-and-fixes"></a>Běžné chyby a opravy
 V následující tabulce jsou uvedeny nejběžnější chyby a jejich opravy.

|Chybová zpráva|Popis|Řešení|
|-|-|-|
|Nepodařilo se načíst základní třídu {0} , ze které dědí třída Transformation.|Vyvolá se v případě, že nemůžete najít základní třídu zadanou `inherits` v parametru v direktivě šablony. Zpráva obsahuje číslo řádku direktivy šablony.|Ujistěte se, že zadaná třída existuje a že sestavení, ve které existuje, je zadáno v direktivě sestavení.|
|Nepovedlo se přeložit text zahrnutí souboru:{0}|Vyvolá se v případě, že nemůžete najít zahrnutou šablonu. Zpráva obsahuje název požadovaného souboru zahrnutí.|Ujistěte se, že cesta k souboru je relativní vzhledem k původní cestě k šabloně, že je soubor v umístění, které je registrováno u hostitele, nebo že existuje úplná cesta k souboru.|
|Při inicializaci objektu transformace se vygenerovaly chyby. Transformace se nebude spouštět.|Vyvolá se v případě, že metoda Initialize() třídy transformace selhala nebo vrátila hodnotu false.|Kód ve funkci Initialize() pochází ze základní třídy transformace zadané v direktivě a \<#@template#> z procesorů direktiv. Chyba, která způsobila selhání inicializace, je pravděpodobně v seznamu chyb. Zjistěte, proč došlo k selhání. Na skutečný vygenerovaný kód pro Initialize() se můžete podívat podle postupů pro ladění šablony.|
|Sestavení pro {0} procesor direktiv nebylo uděleno {1} sadě oprávnění FullTrust. Pouze důvěryhodná sestavení mohou poskytovat procesory direktiv. Tento procesor direktiv se nenačítá.|Vyvolá se v případě, že systém neuděluje oprávnění FullTrust sestavení obsahujícímu procesor direktiv. Zpráva obsahuje název sestavení a název procesoru direktiv.|Ujistěte se, že používáte pouze důvěryhodná sestavení na místním počítači.|
|Cesta musí {0} být místní pro tento počítač nebo část důvěryhodné zóny.|Nastane, když direktiva nebo direktiva sestavení odkazuje na soubor, který není na místním počítači nebo v důvěryhodné zóně vaší sítě.|Ujistěte se, že adresář, ve kterém jsou direktivy direktivy nebo sestavení umístěny, je ve vaší důvěryhodné zóně. Síťový adresář můžete do důvěryhodné zóny přidat prostřednictvím Internet Explorer.|
|Více chyb syntaxe, například Neplatný token catch nebo Obor názvů nemůže přímo obsahovat členy|Příliš mnoho uzavíracích složených závorek v kódu šablony Kompilátor je matoucí s kódem standardní generace.|Zkontrolujte počet uzavíracích složených závorek uvnitř oddělovačů kódu.|
|Smyčky nebo podmíněné výrazy nejsou zkompilovány nebo provedeny správně. Příklad: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Výstupem tohoto kódu je vždy hodnota i. Podmíněný je pouze "Číslo je:".|V jazyce C# vždy používejte složené závorky k ohraničování textových bloků vložených do řídicích příkazů.|Přidejte složené závorky: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|"Výraz je příliš složitý" při zpracování šablony v době návrhu nebo při kompilaci šablony modulu runtime (předzpracované).<br /><br /> Visual Studio pokusu o kontrolu kódu vygenerované šablonou modulu runtime přestane fungovat.|Blok textu je příliš dlouhý. T4 převede textové bloky na výraz zřetězení řetězců s jedním řetězcovým literálem pro každý řádek šablony. Velmi dlouhé textové bloky mohou překrout omezení velikosti kompilátoru.|Blok dlouhého textu můžete rozdělit pomocí bloku výrazu, jako je například:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Popisy a opravy upozornění
 V následující tabulce jsou uvedena nejběžnější upozornění spolu s opravami, pokud jsou k dispozici.

|Zpráva upozornění|Popis|Řešení|
|-|-|-|
|Načtením souboru zahrnutí {0} vrátíte hodnotu null nebo prázdný řetězec.|Vyvolá se, pokud je zahrnutý soubor textové šablony prázdný. Zpráva obsahuje název zahrnutých souborů.|Odeberte direktivu include nebo se ujistěte, že soubor obsahuje nějaký obsah.|
|Kompilace transformace:|Při kompilaci transformace předá tento řetězec všem chybám nebo upozorněním pocházejícím z kompilátoru. Tento řetězec znamená, že kompilátor vyvolal chybu nebo upozornění.|Pokud máte potíže s nalezením knihovny DLL, možná budete muset zadat úplnou cestu nebo plně kvalifikovaný silný název, pokud je knihovna DLL v GAC.|
|Parametr ' {0} už v direktivě existuje. Duplicitní parametr bude ignorován.|Vyvolá se v případě, že je parametr v direktivě zadán více než jednou. Zpráva obsahuje název parametru a číslo řádku direktivy.|Odeberte specifikaci duplicitních parametrů.|
|Při načítání souboru zahrnutí došlo k {0} chybě. Direktiva include bude ignorována.|Vyvolá se v případě, že nemůžete najít soubor zadaný v `include` direktivě . Zpráva obsahuje název souboru a číslo řádku direktivy.|Ujistěte se, že soubor k zahrnutí existuje buď ve stejném adresáři jako původní soubor textové šablony, nebo v jednom z adresářů k zahrnutí, které jsou zaregistrované u hostitele.|
|Pro třídu Transformation byla zadána neplatná základní třída. Základní třída musí být odvozena od Microsoft.VisualStudio.TextTemplating.TextTransformation.|Nastane, když parametr v direktivě šablony určuje `inherits` třídu, která nezdědí z `TextTransformation` . Zpráva obsahuje číslo řádku direktivy šablony.|Určete třídu, která je odvozena z `TextTransformation` .|
|V direktivě Template byla zadána neplatná jazyková verze. Jazyková verze musí být ve formátu "XX-XX". Použije se invariantní jazyková verze.|Vyvolá se v případě, že je parametr jazykové verze v direktivě šablony zadán nesprávně. Zpráva poskytuje číslo řádku direktivy šablony.|Změňte parametr jazykové verze na platnou jazykovou verzi ve formátu "XX-XX".|
|{0}V direktivě šablony byla zadána neplatná hodnota pro ladění. Hodnota ladění musí být buď true, nebo false. Použije se výchozí hodnota false (NEPRAVDA).|Vyvolá se v případě, že `debug` je parametr v direktivě šablony nesprávně zadán. Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte parametr Debug na hodnotu "true" nebo "false".|
|{0}V direktivě šablony byla zadána neplatná hodnota hostspecific. Hodnota HostSpecific musí být buď true, nebo false. Použije se výchozí hodnota false (NEPRAVDA).|Vyvolá se v případě, že je parametr specifický pro hostitele v `template` direktivě zadán nesprávně. Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte parametr specifický pro hostitele na hodnotu "true" nebo "false".|
|{0}V direktivě template byl zadán neplatný jazyk. Jazyk musí být buď C#, nebo VB. Použije se výchozí hodnota C#.|Nastane, pokud je v direktivě zadán nepodporovaný jazyk `template` . Jsou povoleny pouze jazyky C# nebo VB (nerozlišuje velká a malá písmena). Zpráva poskytuje číslo řádku direktivy šablony.|Nastavte `language` parametr v direktivě Template na "C#" nebo "VB".|
|V šabloně bylo nalezeno více direktiv výstupu. Všechny kromě prvního ale budou ignorovány.|Vyvolá se v případě, že je `output` v souboru šablony zadáno více direktiv. Zpráva poskytuje číslo řádku pro duplicitní výstupní direktivu.|Odeberte duplicitní `output` direktivy.|
|V šabloně bylo nalezeno více direktiv šablony. Všechny kromě prvního ale budou ignorovány. V rámci jedné direktivy šablony by mělo být zadáno více parametrů direktivy šablony.|Nastane, pokud zadáte více `template` direktiv v rámci souboru textové šablony (včetně zahrnutých souborů). Zpráva poskytuje číslo řádku duplicitní direktivy šablony.|Seskupte různé `template` direktivy do jedné `template` direktivy.|
|Pro direktivu s názvem ' ' nebyl zadán žádný procesor {0} . Direktiva bude ignorována.|Nastane, pokud zadáte `custom` direktivu, ale nezadáte `processor` atribut. Zpráva poskytuje název direktivy a číslo řádku.|Zadejte `processor` atribut s názvem `directive` procesoru pro tuto direktivu.|
|Procesor s názvem {0} ' ' nebyl nalezen pro direktivu s názvem ' {1} '. Direktiva bude ignorována.|Vyvolá se v případě, že systém nemůže najít `directive` procesor, který jste zadali v rámci `custom` direktivy. Zpráva poskytuje název direktivy, název procesoru a číslo řádku direktivy.|Nastavte `processor` atribut v direktivě na název procesoru direktiv.|
|Požadovaný parametr {0} pro direktivu nebyl {1} nalezen. Direktiva bude ignorována.|Vyvolá se v případě, že systém neposkytne požadovaný parametr direktivy. Zpráva poskytuje název chybějícího parametru, název direktivy a číslo řádku.|Zadejte chybějící parametr.|
|Procesor s názvem nepodporuje {0} direktivu s názvem {1} . Direktiva bude ignorována.|Vyvolá se v případě, že procesor direktiv nepodporuje direktivu. Zpráva poskytuje název a číslo problematické direktivy spolu s názvem procesoru direktiv.|Opravte název direktivy.|
|Direktiva include pro soubor {0} způsobuje nekonečnou smyčku.|Zobrazuje se, pokud jsou zadány cyklické direktivy include (například File A zahrnuje soubor B, který obsahuje soubor A).|Nezadávejte cyklické direktivy include.|
|Spouštění transformace:|Dořadí tento řetězec ke všem chybám nebo varováním, které jsou generovány při spuštění transformace.|Neužívá se.|
|V rámci bloku byla nalezena neočekávaná počáteční nebo koncová značka. Ujistěte se, že jste nezadali počáteční nebo koncovou značku a že v šabloně nemáte žádné vnořené bloky.|Zobrazí se v případě neočekávaného \<# or #> . To znamená, že pokud máte, \<# after another open tag that has not been closed, or you have a #> když před ním nezůstane žádná neuzavřená otevřená značka. Zpráva poskytuje číslo řádku neodpovídající značky.|Buď odeberte neshodnou počáteční nebo koncovou značku, nebo použijte řídicí znak.|
|Byla zadána direktiva v nesprávném formátu. Direktiva bude ignorována. Zadejte prosím direktivu ve formátu. `<#@ name [parametername="parametervalue"]*  #>`|Zobrazeno analyzátorem, pokud není zadána direktiva ve správném formátu. Zpráva poskytuje číslo řádku nesprávné direktivy.|Ujistěte se, že všechny direktivy jsou ve formátu `<#@ name [parametername="parametervalue"]*  #>` . Další informace naleznete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).|
|Načtení sestavení ' {0} ' pro registrovaný procesor direktiv ' ' se nezdařilo. ' {1} '<br /><br /> {2}|Vyvolá se v případě, že hostitel nemůže načíst procesor direktiv. Zpráva identifikuje sestavení poskytnuté pro procesor direktiv a název procesoru direktiv.|Ujistěte se, že je správně zaregistrován procesor direktiv a zda sestavení existuje.|
|Nepovedlo se najít typ {0} v sestavení {1} pro registrovaný procesor direktiv. {2}<br /><br /> {3}|Nastane, pokud se nepovedlo načíst typ procesoru direktiv z jeho sestavení. Zpráva poskytuje název typu, sestavení a procesoru direktiv.|VSHost vyhledá v registru informace o procesoru direktiv (název, sestavení a typ). Ujistěte se, že je správně zaregistrován procesor direktiv a zda typ existuje v sestavení.|
|Při načítání sestavení došlo k {0} problému.|Nastane, pokud dojde k potížím při načítání sestavení. Zpráva poskytuje název sestavení.|Můžete určit sestavení, která mají být načtena do \<@#assembly#> direktiv a pomocí procesorů směrnice. Chybová zpráva, která následuje tento řetězec, by měla poskytnout více dat pro důvody, proč selhalo načtení sestavení.|
|Došlo k potížím při vytváření a inicializaci procesoru pro direktivu s názvem {1} . Typ procesoru je {0} . Direktiva bude ignorována.|Vyvolá se v případě, že systém nemohl vytvořit nebo inicializovat procesor direktiv. Zpráva poskytuje název a číslo řádku direktivy a typ procesoru.|Ujistěte se, že používáte správný procesor direktiv a že má procesor direktivy veřejný výchozí konstruktor. V opačném případě použijte možnosti ladění, abyste zjistili, proč metoda Initialize () procesoru direktivy selhala. Další informace najdete v tématu [Poradce při potížích s textovými šablonami](../modeling/debugging-a-t4-text-template.md).|
|Při zpracovávání direktivy s názvem ' ' byla vyvolána výjimka {0} .|Vyvolá se v případě, že procesor direktiv vyvolá výjimku při zpracování direktivy.|Ujistěte se, že jsou správné parametry procesoru direktiv.|
|Hostitel vyvolal výjimku při pokusu o vyřešení odkazu na sestavení {0} '.|Vyvolá se, když hostitel vyvolá výjimku při pokusu o vyřešení odkazu na sestavení. Zpráva obsahuje referenční řetězec sestavení.|Odkazy na sestavení pocházejí z \<@#assembly#> direktiv a z procesorů direktiv. Ujistěte se, že parametr name poskytnutý v parametru sestavení je správný.|
|Pokus o zadání nepodporované {1} hodnoty {0} pro direktivu {2}|Generuje se třídou RequiresProvidesDirectiveProcessor (odvozují se z ní všechny naše vygenerované procesory direktiv), když poskytnete nepodporovaný argument requires nebo .|Ujistěte se, že názvy ve dvojicích name='value' zadané v parametrech requires a poskytuje správné parametry.|
